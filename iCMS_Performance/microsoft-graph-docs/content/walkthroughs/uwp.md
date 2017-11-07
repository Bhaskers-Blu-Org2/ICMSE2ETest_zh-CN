# <a name="call-microsoft-graph-in-a-universal-windows-10-app"></a>在一个通用的窗口 10 应用程序中调用 Microsoft Graph

在本文中我们获取访问令牌从 Azure 活动目录 (AD)，调用 Microsoft Graph 所需的最小任务。 我们使用[Office 365 UWP 使用 Microsoft Graph 连接示例](https://github.com/microsoftgraph/uwp-csharp-connect-rest-sample)代码解释您需要在您的应用程序中实现的主要概念。

## <a name="sample-user-interface"></a>示例用户界面

该示例包含 top 命令栏、**连接按钮**、**发送邮件**的按钮，以及已登录的用户的电子邮件地址自动填充，但您可以编辑的文本框组成一个非常简单的用户界面。 命令栏还包含一个按钮，使开发人员能够找到应用程序的重定向 URI。

**发送邮件**按钮将被禁用，用户有未连接时︰

![屏幕显示连接按钮启用和禁用发送邮件按钮](images/SignedOut.png)

Top 命令栏包含一个断开连接按钮，当用户连接︰

![屏幕显示连接的用户的电子邮件地址，并启用发送邮件按钮](images/SignedIn.png)

在资源文件夹中的 Resources.resw 文件中存储的所有示例的用户界面字符串。

## <a name="register-the-app"></a>注册应用程序
 
Windows 10 提供了每个应用程序使用唯一的 URI 并确保发送到该 URI 的消息只发送到该应用程序。 您需要创建您的应用程序并在您注册您的应用程序之前找到此系统生成的 URI。 示例中的 AuthenticationHelper.cs 文件中可以找到此方法︰

```c#
        public static string GetAppRedirectURI()
        {
            // Windows 10 universal apps require redirect URI in the format below. Add a breakpoint to this line and run the app before you register it, so that
            // you can supply the correct redirect URI value.
            return string.Format("ms-appx-web://microsoft.aad.brokerplugin/{0}", WebAuthenticationBroker.GetCurrentApplicationCallbackUri().Host).ToUpper();
        }
```

方法样本中触发该**副本重定向 URI**的按钮，但您也可以按照[AzureAD NativeClient UWP WAM](https://github.com/Azure-Samples/AzureAD-NativeClient-UWP-WAM)示例，其中主页类声明中定义的字符串，您可以读取它使用 Visual Studio 调试器中的模式。 

若要注册您的应用程序之后，您已经看到了重定向 URI 值按照[注册和配置应用程序](https://github.com/microsoftgraph/uwp-csharp-connect-rest-sample#register)的示例自述文件中的步骤操作。

当您配置您的应用程序进行身份验证时，您将需要从 Azure 应用程序的**配置**页中的客户端 ID 值。

## <a name="connect-to-microsoft-graph"></a>连接到 Microsoft Graph

该示例使用本机 Windows 10 WebAccountManager API 用户进行身份验证。 它遵循模式类似于所述[开发 Windows 通用应用程序使用 Azure 的 AD 和 Windows 10 身份 API](http://blogs.technet.com/b/ad/archive/2015/08/03/develop-windows-universal-apps-with-azure-ad-and-the-windows-10-identity-api.aspx)博客张贴和[AzureAD NativeClient UWP WAM](https://github.com/Azure-Samples/AzureAD-NativeClient-UWP-WAM)示例所示。

App.xaml 文件中包含的键/值对的您的应用程序将需要对用户进行身份验证和授权应用程序发送一封电子邮件︰

```xml
    <Application.Resources>
        <!-- Add your client id here. -->
        <x:String x:Key="ida:ClientID"><your client id></x:String>
        <x:String x:Key="ida:AADInstance">https://login.microsoftonline.com/</x:String>
        <!-- Add your developer tenant domain here. -->
        <x:String x:Key="ida:Domain">yourtenant.onmicrosoft.com</x:String>
    </Application.Resources>
```

添加了您的应用程序注册为**ida︰ 客户机 Id**键的值时的客户端 ID 值。 更改**域 ida︰**键的值，使其匹配您的 Office 365 租户。

AuthenticationHelper.cs 文件中包含的所有身份验证代码，以及其他逻辑来存储用户信息，并仅在用户已从应用程序断开时强制进行身份验证。

``GetTokenHelperAsync``在此文件中定义的方法运行时对用户进行身份验证以及随后每次应用程序调用 Microsoft Graph。 其首要任务是找到 Azure 的广告帐户提供程序︰

```c#
           aadAccountProvider = await WebAuthenticationCoreManager.FindAccountProviderAsync("https://login.microsoft.com", authority);
```

值``authority``是由两个值存储在 App.xaml 文件中串联的字符串︰ **ida: AADInstance**键加上**ida︰ 域**键的值的值。 这将创建一个特定于租户的颁发机构。 您还可以使用字符串"组织"如果您希望您的应用程序在任何 Azure AD 客户端上运行。

应用程序对用户进行身份验证后，存储在中的用户 ID 值``ApplicationData.Current.RoamingSettings``。 ``GetTokenHelperAsync``方法首先检查是否存在此值，如果是这样，它会尝试自行进行身份验证︰

```c#
            // Check if there's a record of the last account used with the app
            var userID = _settings.Values["userID"];

            if (userID != null)
            {

                WebTokenRequest webTokenRequest = new WebTokenRequest(aadAccountProvider, string.Empty, clientId);
                webTokenRequest.Properties.Add("resource", ResourceUrl);

                // Get an account object for the user
                userAccount = await WebAuthenticationCoreManager.FindAccountAsync(aadAccountProvider, (string)userID);


                // Ensure that the saved account works for getting the token we need
                WebTokenRequestResult webTokenRequestResult = await WebAuthenticationCoreManager.RequestTokenAsync(webTokenRequest, userAccount);
                if (webTokenRequestResult.ResponseStatus == WebTokenRequestStatus.Success || webTokenRequestResult.ResponseStatus == WebTokenRequestStatus.AccountSwitch)
                {
                    WebTokenResponse webTokenResponse = webTokenRequestResult.ResponseData[0];
                    userAccount = webTokenResponse.WebAccount;
                    token = webTokenResponse.Token;

                }
                else
                {
                    // The saved account could not be used for getting a token
                    // Make sure that the UX is ready for a new sign in
                    SignOut();
                }

            }
```

该应用程序使用 Microsoft Graph 终结点- **https://graph.microsoft.com/** -作为资源值。 当构建``WebTokenRequest``它使用添加到 App.xaml 文件的客户端 ID 值。 由于应用程序知道用户 ID 和用户没有断开连接，WebAccountManager API 可以查找用户帐户并将其传递到令牌的请求。 ``WebAuthenticationCoreManager.RequestTokenAsync``方法返回具有适当的权限分配给它一个访问令牌。

如果应用程序找到任何``userID``建立在漫游的设置中， ``WebTokenRequest`` ，迫使用户通过用户界面进行身份验证︰

```c#
            else
            {
                // There is no recorded user. Start a sign in flow without imposing a specific account.

                WebTokenRequest webTokenRequest = new WebTokenRequest(aadAccountProvider, string.Empty, clientId, WebTokenRequestPromptType.ForceAuthentication);
                webTokenRequest.Properties.Add("resource", ResourceUrl);

                WebTokenRequestResult webTokenRequestResult = await WebAuthenticationCoreManager.RequestTokenAsync(webTokenRequest);
                if (webTokenRequestResult.ResponseStatus == WebTokenRequestStatus.Success)
                {
                    WebTokenResponse webTokenResponse = webTokenRequestResult.ResponseData[0];
                    userAccount = webTokenResponse.WebAccount;
                    token = webTokenResponse.Token;

                }
            }
```

如果尝试检索令牌成功，``GetTokenHelperAsync``方法完成将重要的用户信息存储在漫游设置，然后返回标记的值。 否则，它确保了漫游的设置都为 null，则返回空值。

```c#
            // We succeeded in getting a valid user.
            if (userAccount != null)
            {
                // save user ID in local storage
                _settings.Values["userID"] = userAccount.Id;
                _settings.Values["userEmail"] = userAccount.UserName;
                _settings.Values["userName"] = userAccount.Properties["DisplayName"];

                return token;
            }

            // We didn't succeed in getting a valid user. Clear the app settings so that another user can sign in.
            else
            {
                
                SignOut();
                return null;
            }
```

## <a name="send-an-email-with-microsoft-graph"></a>Microsoft Graph 电子邮件发送

MailHelper.cs 文件中包含的代码构造并发送电子邮件。 它包含一个方法 — ``ComposeAndSendMailAsync`` -的构造，并将 POST 请求发送到**https://graph.microsoft.com/v1.0/me/microsoft.graph.SendMail**的终结点。 

``ComposeAndSendMailAsync``方法采用三个字符串值- ``subject``， ``bodyContent``，和``recipients``-MainPage.xaml.cs 文件传递给它。 ``subject`` ，``bodyContent``字符串存储，以及所有其他 UI 字符串，在 Resources.resw 文件中。 ``recipients``来自应用程序的界面中的地址框中的字符串。 

由于用户可能可以通过多个地址，第一项任务就是拆分``recipients``到一组电子邮件地址对象，然后可以在 POST 请求体中传递的字符串︰

```c#
            // Prepare the recipient list
            string[] splitter = { ";" };
            var splitRecipientsString = recipients.Split(splitter, StringSplitOptions.RemoveEmptyEntries);
            string recipientsJSON = null;

            int n = 0;
            foreach (string recipient in splitRecipientsString)
            {
                if ( n==0)
                recipientsJSON += "{'EmailAddress':{'Address':'" + recipient.Trim() + "'}}";
                else
                {
                    recipientsJSON += ", {'EmailAddress':{'Address':'" + recipient.Trim() + "'}}";
                }
                n++;
            }
```

第二项任务是构造一个有效的 JSON 消息对象并将其发送到**me/microsoft.graph.SendMail**通过 HTTP POST 请求的端点。 由于``bodyContent``字符串是一个 HTML 文档，该请求将**ContentType**值设置为 HTML。 此外注意到在调用``AuthenticationHelper.GetTokenHelperAsync``以确保我们有一个新的访问令牌请求中传递。

```c#
                HttpClient client = new HttpClient();
                var token = await AuthenticationHelper.GetTokenHelperAsync();
                client.DefaultRequestHeaders.Add("Authorization", "Bearer " + token);

                // Build contents of post body and convert to StringContent object.
                // Using line breaks for readability.
                string postBody = "{'Message':{" 
                    +  "'Body':{ " 
                    + "'Content': '" + bodyContent + "'," 
                    + "'ContentType':'HTML'}," 
                    + "'Subject':'" + subject + "'," 
                    + "'ToRecipients':[" + recipientsJSON +  "]}," 
                    + "'SaveToSentItems':true}";

                var emailBody = new StringContent(postBody, System.Text.Encoding.UTF8, "application/json");

                HttpResponseMessage response = await client.PostAsync(new Uri("https://graph.microsoft.com/v1.0/me/microsoft.graph.SendMail"), emailBody);

                if ( !response.IsSuccessStatusCode)
                {

                    throw new Exception("We could not send the message: " + response.StatusCode.ToString());
                }
```

完成其余请求成功后，实施了为与图表进行交互所需的三个步骤︰ 应用程序注册、 用户身份验证和其他请求。


<!--## Additional resources

* [Develop Windows Universal Apps with Azure AD and the Windows 10 Identity API](http://blogs.technet.com/b/ad/archive/2015/08/03/develop-windows-universal-apps-with-azure-ad-and-the-windows-10-identity-api.aspx)
* [AzureAD-NativeClient-UWP-WAM](https://github.com/Azure-Samples/AzureAD-NativeClient-UWP-WAM)
* [Office Dev Center](http://dev.office.com)-->


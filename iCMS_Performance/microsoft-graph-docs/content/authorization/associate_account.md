<!---<a name="bk_CreateAzureSubscription"> </a>-->

# <a name="associate-your-office-365-account-with-azure-ad-to-create-and-manage-apps"></a>与 Azure 的广告来创建和管理应用程序关联您 Office 365 的帐户

要验证您的应用程序，您需要在 Microsoft Azure 活动目录 (AD Azure) 中注册它们。 这是 Office 365 的用户帐户和应用程序信息的存储位置。 若要管理 Azure 广告通过 Azure 管理门户，需要 Microsoft Azure 订阅。 使用 Microsoft Azure 中的管理门户网站，使您能够管理用户、 角色和应用程序。 

这篇文章将引导您完成将 Office 365 帐户使用 Azure 的广告来创建和管理应用程序相关联。


## <a name="prerequisites"></a>先决条件

**Office 365 的企业往来帐户**

如果您没有现有的 Office 365 的企业往来帐户，您可以︰

- [Office 365 的业务计划](http://products.office.com/en-us/business/compare-office-365-for-business-plans)上述注册了或
- [参加 Office 365 开发计划并获取 Office 365 的免费 1 年预订](https://aka.ms/devprogramsignup)。

**Microsoft Azure 订阅** 

- 如果可以有 Microsoft Azure 的订阅，您可以将业务订阅您 Office 365 与其相关联。 

- 否则，您将需要创建一个新的 Azure 订阅并将其与您的 Office 365 帐户来注册和管理应用程序。


<!---<a name="bk_AssociateExistingAzureSubscription"> </a>-->

## <a name="to-associate-an-existing-azure-subscription-with-your-office-365-account"></a>若要将现有 Azure 订阅与 Office 365 帐户相关联


1. 登录到您现有的 Azure 凭据 (例如，您 Microsoft ID 如[Microsoft Azure 管理门户](https://manage.windowsazure.com)user@live.com).
        
2. 选择**活动目录**节点，然后选择**目录**选项卡，并在屏幕的底部，选择**新建**。 
     
4. 在**新建**菜单中，选择**活动目录** > **目录** > **自定义创建**。
    
5. 在**添加目录**，请在**目录**下拉列表框中，选择**使用现有目录**。 检查**我已准备好要签名**，然后选择在右下角的复选标记。 
    
    这将返回到 Azure 管理门户。
        
3. 使用 Office 365 的帐户信息登录。 
    
    系统将提示您是否要使用 Azure 的目录。 
    
    **重要**若要将 Office 365 帐户与 Azure AD 相关联，您将需要 Office 365 提供企业往来帐户具有全局管理员权限。 
    
        
4. 选择**继续**，然后**立即注销**。
        
5. 关闭浏览器，然后重新打开[门户](https://manage.windowsazure.com)。 否则，您将收到拒绝访问错误。
    
        
6. 再次登录与您现有的 Azure 凭据 (例如，如您 Microsoft IDuser@live.com).导航到**Active Directory**节点并在**目录**下，您应看到您列出的 Office 365 提供帐户。
    

<!--<a name="bk_AssociateNewAzureSubscription"> </a>-->

## <a name="to-create-a-new-azure-subscription-and-associate-it-with-your-office-365-account"></a>若要创建新的 Azure 订阅并将其与您的 Office 365 帐户


1. 登录到 Office 365。 从**主页**页中，选择**管理**图标，以打开 Office 365 管理中心。
2. 在页面左侧菜单页，向下滚动到**管理**并选择**Azure 的广告**。

    **重要**要打开 Office 365 管理中心，并访问 Azure 的广告，则需要全局管理员权限使用 Office 365 提供企业往来帐户。 
    
3. 创建新的订阅。
        
    如果使用的 Office 365 的试用版，您将看到一条消息告诉您 Azure 广告仅限于客户提供付费服务。 您仍然可以创建试用 30 天 Azure 订阅免费，但您将需要执行几个额外的步骤︰
    
    1. 选择您的国家或地区，然后单击**Azure 的订阅**。
    2. 请输入您的个人信息。 出于验证目的输入电话号码时可到达，并指定您是否要发送文本消息或调用。
    3. 一旦您收到您的验证码，输入它并单击**验证代码**。
    4. 输入付款信息、 签了协议，并选择**注册**。
        
        您的信用卡不收取。
        
        不要关闭或刷新您的浏览器，创建 Azure 订购过程。
            
4. Azure 订阅创建后，选择**门户**。
        
5. Azure 教程将显示。 您可以查看它，或选择**X**来关闭它。
        
    您现在应该在 Azure 订阅查看所有项目。 它列出了 Office 365 租户同名的目录。
    

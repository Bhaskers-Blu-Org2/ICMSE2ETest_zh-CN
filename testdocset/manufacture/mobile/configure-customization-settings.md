---
Description: In this section, we'll focus on adding the Start layout modification file, preloading an app, and configuring some customization settings using MCSF.For more detailed information about the various customizations you can do, see https://msdn.microsoft.com/library/windows/hardware/dn757433.
ms.assetid: 507fea31-f113-4cd3-84bf-1ab14898782f
MSHAttr: PreferredLib:/library
title: "配置自定义设置"
author: CelesteDG
ms.openlocfilehash: 919d399a7b2e449fab5a6121a6642138f679c6fa
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configure-customization-settings"></a>配置自定义设置


自定义是您可以修改 Windows 设备用户界面、 连接设置和用户体验更好地反映您的品牌，满足要求的网络和设备将的市场的方式。 自定义可以包括添加应用程序、 修改开始布局、 配置网络设置，使用设备管理、 更改设置屏幕中的默认值或添加新的墙纸。

Windows 10 移动支持这两种自定义框架︰ MCSF 和设置窗口。 有关每个框架的详细信息，请参阅[移动设备的自定义项](https://msdn.microsoft.com/library/windows/hardware/mt481438)。

在本节中，我们将重点讨论添加开始布局修改文件、 预加载应用程序，以及配置使用 MCSF 一些自定义设置。

您可以执行各种自定义设置的详细信息，请参阅[https://msdn.microsoft.com/library/windows/hardware/dn757433](https://msdn.microsoft.com/library/windows/hardware/dn757433)。

## <a name="span-idcreateanmcsfcustomizationanswerfilespanspan-idcreateanmcsfcustomizationanswerfilespancreate-an-mcsf-customization-answer-file"></a><span id="create_an_mcsf_customization_answer_file"></span><span id="CREATE_AN_MCSF_CUSTOMIZATION_ANSWER_FILE"></span>创建一个 MCSF 自定义答案文件


可以使用 MCSF[自定义应答文件](https://msdn.microsoft.com/library/windows/hardware/dn757452)（咖啡馆） 指定设置和要为其配置自定义的移动操作系统映像的款式。 这取决于您使用来构建您的映像工具，可以作为输入到 ImgGen.cmd 或 Windows 图像处理和配置设计器 (ICD) CLI 使用 MCSF 咖啡馆。 此应答文件基于 MCSF 架构因此如果您决定使用另一个架构，如 Windows 资源调配架构，您需要编写的不同的答案文件，而是遵循该架构。

如果您没有预先存在的 MCSF 咖啡馆，请按照本演练中，若要了解如何创建基本的 MCSF 咖啡馆 multivariant 支持。 Multivariant 是用于创建单个图像，可以通过动态配置语言、 品牌，应用程序，并在运行时基于的支持条件，如移动运营商和区域设置网络设置工作的多个市场的一般机制。 如果您要构建一个 variant 类型的值图像，您可以跳过本演练。

**若要创建 multivariant 支持 MCSF 咖啡馆**

1.  创建一个 XML 文件，并添加以下内容。

    ```XML
    <?xml version="1.0" encoding="utf-8" ?>
    <ImageCustomizations xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate"  
                         Name=""  
                         Description="Use to configure settings for custom mobile image."  
                         Owner=""  
                         OwnerType="OEM"> 

      <!-- Use to set up targets and conditions for the variants -->
      <Targets>  
       <Target Id="">  
          <TargetState>  
            <Condition Name="" Value="" />  
            <Condition Name="" Value="" />  
          </TargetState>  
        </Target>  
       <Target Id="">  
          <TargetState>  
            <Condition Name="" Value="" />  
            <Condition Name="" Value="" />  
          </TargetState>  
        </Target> 
      </Targets>  
      
      <!-- Use to specify the customizations for a single variant when used without the Variant element, 
           or customizations that apply to all variants when used with the Variant element -->
      <Static>  
        <!-- Use to preload apps to install for all variants -->
        <Applications>
          <Application Source=""
                       License=""
                       ProvXML="" />
        </Applications>

        <!-- Section where you specify the settings you want to configure -->
        <Settings Path="">  
          <Setting Name="" Value="" /> 
        </Settings>
      </Static>

      <!-- These settings in the Variant groups will only be applied if the associated target&#39;s conditions are met. -->
      <!-- The settings shown here will only be applied for this variant -->
      <Variant Name="">  
        <!-- Only one TargetRef can be used for each variant -->
        <TargetRefs>  
          <TargetRef Id="" />  
        </TargetRefs>  

        <Settings Path="">  
          <Setting Name="" Value="" /> 
        </Settings> 

        <Settings Path="">  
          <Setting Name="" Value="" /> 
        </Settings> 
      </Variant>  

      <!-- The settings shown here will only be applied for this variant -->
      <Variant Name="">  
        <!-- Only one TargetRef can be used for each variant -->
        <TargetRefs>  
          <TargetRef Id="" />  
        </TargetRefs>  

        <Settings Path="">  
          <Setting Name="" Value="" /> 
        </Settings> 

        <Settings Path="">  
          <Setting Name="" Value="" /> 
        </Settings> 
      </Variant> 

    </ImageCustomizations>
    ```

2.  指定下列属性的值确定自定义项的所有者︰

    -   **名称**-指定自定义项或文件包的名称的字符串。 您可以指定根据您正在配置，如"XDeviceCustomizations"或类似"MobileCustomizations"的通用名称的设备的名称。
    -   **说明**-可以帮助您识别在咖啡馆中定义的自定义项的字符串。
    -   **所有者**— 指定的所有者，例如 OEM 名称的字符串。
    -   **所有者类型**的设置为"OEM"。

3.  指定要用于该变型**的目标**。 **目标**描述键控的 variant 类型的值必须是所述或预先声明的变量，该变量引用之前。 若要此操作︰

    **若要设置一个目标**

    1.  命名**的目标 Id**。

    2.  通过提供**名称**和**值**为目标指定**条件**(s)。

    例如，如果我们创建的两个虚构的移动运营商的款式，电话公司 Fabrikam，和我们有他们的 MCC 和 mnc，我们可以为每个运算符使用 MCC 和 mnc 创建目标。

    ```XML
      <!-- Use to set up targets and conditions for the variants -->
      <Targets>  
       <Target Id="Id_PhoneCo">  
          <TargetState>  
            <Condition Name="MCC" Value="410" />  
            <Condition Name="MNC" Value="510" />  
          </TargetState>  
        </Target>  
       <Target Id="Id_Fabrikam">  
          <TargetState>  
            <Condition Name="MCC" Value="310" />  
            <Condition Name="MNC" Value="610" />  
          </TargetState>  
        </Target> 
      </Targets>  
      
    ```

    若要了解更多有关所有受支持**条件名称**，您可以使用，请参阅一节*目标、 TargetState、 条件和优先级*[创建具有 multivariant 设置的自动配置软件包](https://msdn.microsoft.com/library/windows/hardware/dn916108)中。 请注意，在本演练中我们不使用的供应包声明我们 multivariant 的设置;相反，我们将添加这直接插入 MCSF 咖啡馆。

4.  设置该变量。 若要此操作︰

    **若要定义一个变量**

    1.  指定的**变量名称**。

    2.  指定的款式的**TargetRef Id** 。 这应与 s 的咖啡馆的**目标**部分中指定的**目标 Id**之一匹配。 请注意，只应该有一个**TargetRef Id**每个变型。

    使用我们虚构移动运营商的电话公司和 Fabrikam，我们可以按每个这些运算符来定义变体如下面的示例中所示︰

    ```XML
      <!-- The settings shown here will only be applied for The Phone Company -->
      <Variant Name="ThePhoneCompany">  
        <TargetRefs>  
          <TargetRef Id="Id_PhoneCo" />  
        </TargetRefs>  

        <Settings Path="">  
          <Setting Name="" Value="" /> 
        </Settings> 

        <Settings Path="">  
          <Setting Name="" Value="" /> 
        </Settings> 
      </Variant>  

      <!-- The settings shown here will only be applied for Fabrikam -->
      <Variant Name="Fabrikam">  
        <TargetRefs>  
          <TargetRef Id="Id_Fabrikam" />  
        </TargetRefs>  

        <Settings Path="">  
          <Setting Name="" Value="" /> 
        </Settings> 

        <Settings Path="">  
          <Setting Name="" Value="" /> 
        </Settings> 
      </Variant>   
    ```

5.  命名并保存的 XML 文件;例如， *c:\\Contoso\\的自定义\\MobileCustomizations.xml*。

    我们将在下一次演练中添加 （公共或不可知的变量，该变量） 的静态变量，该变量的特定自定义设置和值。

## <a name="span-idconfigurethestartlayoutmcsfspanspan-idconfigurethestartlayoutmcsfspanconfigure-the-start-layout"></a><span id="configure_the_start_layout_mcsf"></span><span id="CONFIGURE_THE_START_LAYOUT_MCSF"></span>配置开始布局


在本节中，我们将使用启动 MCSF 设置以添加您在[配置开始布局](configure-the-start-layout.md)中创建的开始布局修改文件。 我们将为通用开始布局使用布局修改文件中的一个，一个虚构的移动运营商变体将使用其他布局修改文件。

1.  创建和编辑 MCSF 咖啡馆中;例如， *c:\\Contoso\\的自定义\\MobileCustomizations.xml*。

2.  设置*c:\\Contoso\\的自定义\\LayoutModification1.xml*作为通用开始布局。

    在咖啡馆的**静态**部分，设置`LayoutModificationFilePath`布局修改文件的文件路径。

    ```XML
      <Static>  
        <!-- Use to preload apps to install for all variants -->
        <Applications>
          <Application Source=""
                       License=""
                       ProvXML="" />
        </Applications>

        <!-- Section where you specify the settings you want to configure -->
        <Settings Path="StartLayoutModificationFilePath">  
          <Setting Name="LayoutModificationFilePath" Value="C:\Contoso\Customizations\LayoutModification1.xml" />
        </Settings>  
      </Static>
    ```

    通过指定新的默认位置为 LayoutModification.xml，重写默认的开始布局中 c:\\数据\\ProgramData\\Microsoft\\启动\\布局。

3.  设置*c:\\Contoso\\的自定义\\LayoutModification2.xml*作为虚构的移动运营商，电话公司默认开始布局。

    在名为 ThePhoneCompany 的**变量**部分中，将`LayoutModificationFilePath`为第二个布局修改文件的文件路径。

    ```XML
      <!-- The settings shown here will only be applied for The Phone Company -->
      <Variant Name="ThePhoneCompany">  
        <TargetRefs>  
          <TargetRef Id="Id_PhoneCo" />  
        </TargetRefs>  

        <Settings Path="StartLayoutModificationFilePath">  
          <Setting Name="LayoutModificationFilePath" Value="C:\Contoso\Customizations\LayoutModification2.xml" />
        </Settings> 
      </Variant>  
    ```

**注意**`LayoutModificationFilePath` FirstVariationOnly 设置，这意味着它只修改在第一种用法，通常是在找到第一个有效的配置 （如 sim 卡插入时，标记的配置以便在 sim 卡中找到）。   如果更改了配置，如在 sim 卡换用，FirstVariationOnly 设置的值将不再次更改。

 

在此示例中，当设备启动刷新新的移动图像后并没有没有 sim 卡被插入到手机或 sim 卡为虚构的 Fabrikam 移动运营商 (MCC 310，mnc 是否 = = 610) 是在设备中的已会使用 LayoutModification1.xml （开始布局与一个文件夹）。 如果为虚构的 SIM 电话公司 (MCC = 410、 mnc 是否 = 510) 之后，将不会更改布局的开始插入。 但是，如果设备启动刷新新的移动图像后，已经有电话公司在设备中插入 SIM LayoutModification2.xml （与没有文件夹开始布局） 将改为使用。

## <a name="span-idpreloadappsspanspan-idpreloadappsspanpreload-apps"></a><span id="preload_apps"></span><span id="PRELOAD_APPS"></span>预加载应用程序


合作伙伴可以预加载应用程序打包和配置初始设备安装过程中安装在移动设备上。 除了预加载游戏、 生活方式的应用程序和应用程序的其他流派，合作伙伴可以预先加载系统设置的应用程序和合作伙伴帐户安装应用程序，只是仅举几例。 有关预加载应用程序的详细信息，请参阅[Preinstallable 应用程序的移动设备](https://msdn.microsoft.com/library/windows/hardware/dn707972)。

**重要** 在 Windows 10，如果您正在使用的应用程序开发人员或创建您自己的应用程序预安装的设备，您必须立即请求应用程序预安装包。 有关过程的这一部分的详细信息，请参阅[预安装 oem 包的生成](http://go.microsoft.com/fwlink/p/?LinkId=624851)。 作为此过程的一部分应包含应用程序的源文件 （如.appx、.appxbundle 或.xap） 返回的.zip 文件、 配置文件 (.provxml) 和许可证文件 (.xml)。 如果您预安装的包不包含这些文件的所有，不能成功预加载应用程序。

 

**若要预加载应用程序**

1.  验证应用程序预安装包中包含要预加载应用程序所需的所有文件︰ 文件、 配置文件和许可证文件源。

2.  将应用程序添加到映像中。 若要执行此操作，请执行以下步骤︰

    1.  将**应用程序**部分添加到咖啡馆。

        ```XML
            <!-- Use to preload apps to install for all variants -->
            <Applications>
              <Application Source=""
                           License=""
                           ProvXML="" />
            </Applications>
        ```

        **请注意** 您可以添加的**静态**部分中的咖啡馆，这意味着将安装应用程序而不考虑该变量的所有图像，**应用**部分或特定**variant 类型的值**，这都意味着特定变型的仅将其安装在您可以添加它。 如果将预加载多个应用程序，一个可以通用于所有变体 （或**静态**部分中），而另一个仅适用于特定的变体 （或**变量**部分中）。 后一种情况的一个示例可以是当您有一个应用程序，您只需安装一个特定的移动运营商，或国家/地区，等等。

         

    2.  将**源**设置为的位置和名称的应用程序源文件。例如， *c:\\Contoso\\的自定义\\应用程序\\SampleApp.appx*。

    3.  设置的位置和名称的应用程序的许可文件;**许可**例如， *c:\\Contoso\\的自定义\\应用程序\\SampleAppLicense.xml*。

    4.  将**ProvXML**设置的位置和名称的应用程序的配置文件，则为例如， *c:\\Contoso\\的自定义\\应用程序\\mpap\_示例应用程序\_001.provxml*。

        ProvXML 文件遵循规定的命名约定。 [Preinstallable 用于移动设备的应用程序](https://msdn.microsoft.com/library/windows/hardware/dn707972)的详细信息，请参见

3.  完成后保存咖啡馆添加所有应用程序。

在某些情况下，可能需要预先加载程序项目依赖于其他软件包或组件的应用程序。 在这种情况下，您需要确保其他组件或包是预装第一次在您的应用程序之前。 如果没有第一次安装相关程序包或组件，您的应用程序预加载将失败。 我们将不会遍历此方案中，但您可以找到此记录在[预加载应用程序的依赖项](https://msdn.microsoft.com/library/windows/hardware/mt691485)。

## <a name="span-idconfiguredevicetargetinginfometadataspanspan-idconfiguredevicetargetinginfometadataspanconfigure-the-devicetargetinginfo-metadata-for-the-device"></a><span id="configure_devicetargetinginfo_metadata"></span><span id="CONFIGURE_DEVICETARGETINGINFO_METADATA"></span>配置设备的 DeviceTargetingInfo 元数据


才能交付至少一个移动设备，您必须设置[电话 DeviceTargetingInfo 中的元数据](https://msdn.microsoft.com/library/windows/hardware/dn772214)中描述所需的设置。 必需的元数据的示例包括︰

-   OEM 和移动运营商的信息，用于连接到 Windows 应用商店，在 UI 中，设备的更新，显示字符串等等。
-   硬件组件版本和软件版本中，用于针对设备更新以及用户支持。
-   设备的型号、 移动运营商的名称和制造商的名称，**设置**中的**关于**屏幕中显示的。

**若要配置 DeviceTargetingInfo 元数据**

1.  编辑 MCSF 咖啡馆中;例如， *c:\\Contoso\\的自定义\\MobileCustomizations.xml*。

2.  在咖啡馆的**静态**部分，添加`DeviceInfo/Static`设置组。

    ```XML
      <Static>  
        <!-- Other settings groups may already precede the DeviceInfo/Static group -->

        <Settings Path="DeviceInfo/Static">       
          <Setting Name="PhoneManufacturer" Value="" />    
          <Setting Name="PhoneManufacturerDisplayName" Value="" /> 
          <Setting Name="PhoneROMVersion" Value="" /> 
          <Setting Name="PhoneHardwareRevision" Value="" />    
          <Setting Name="PhoneSOCVersion" Value="" /> 
          <Setting Name="PhoneFirmwareRevision" Value="" />   
          <Setting Name="PhoneRadioHardwareRevision" Value="" />    
          <Setting Name="PhoneRadioSoftwareRevision" Value="" /> 
          <Setting Name="PhoneBootLoaderVersion" Value="" />    
          <Setting Name="PhoneROMLanguage" Value="" /> 
          <Setting Name="PhoneHardwareVariant" Value="" /> 
       </Settings> 

      </Static>
    ```

    这些设置只是图像时，将会放入注册表配置单元直接。 请注意，在某些设置`DeviceInfo/Static`组是可选的因此您可以选择不能为其指定任何值，或从咖啡馆中删除它们。 下表总结了哪些设置那些必需、 可选的而哪些来自硅供应商。

    <table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">所需的设置</th>
    <th align="left">可选设置</th>
    <th align="left">SoC 的供应商设置</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>PhoneManufacturer</p>
    <p>PhoneFirmwareRevision</p>
    <p>PhoneROMLanguage</p>
    <p>PhoneHardwareVariant</p></td>
    <td align="left"><p>PhoneManufacturerDisplayName</p>
    <p>PhoneRadioHardwareRevision</p></td>
    <td align="left"><p>PhoneROMVersion</p>
    <p>PhoneHardwareRevision</p>
    <p>PhoneSOCVersion</p>
    <p>PhoneRadioSoftwareRevision</p>
    <p>PhoneBootLoaderVersion</p></td>
    </tr>
    </tbody>
    </table>

     

    **请注意** 您需要与您的 Microsoft 代表联系以确定应使用的值`PhoneManufacturer`。

     

3.  在咖啡馆**变体**部分中，添加`DeviceInfo/Variant`设置组。

    使用我们的示例中，我们将添加到 ThePhoneCompany 中的变体部分的设置

    ```XML
       <!-- The settings shown here will only be applied for The Phone Company -->
      <Variant Name="ThePhoneCompany">  
        <TargetRefs>  
          <TargetRef Id="Id_PhoneCo" />  
        </TargetRefs>  

        <!-- Other settings with the Variant section not included here for simplicity --> 

        <Settings Path="DeviceInfo/Variant">
          <Setting Name="PhoneMobileOperatorName" Value="" /> 
          <Setting Name="PhoneManufacturerModelName" Value="" />    
          <Setting Name="PhoneMobileOperatorDisplayName" Value="" /> 
          <Setting Name="PhoneSupportPhoneNumber" Value="" />    
          <Setting Name="PhoneSupportLink" Value="" /> 
          <Setting Name="PhoneOEMSupportLink" Value="" />    
          <Setting Name="PhoneModelName" Value="" /> 
          <Setting Name="RoamingSupportPhoneNumber" Value="" />
       </Settings> 
     
      </Variant>  
    ```

    这些设置是第一种用法，并且可以在运行时配置，因此潜在可能基于 sim 卡值。 请注意，在某些设置`DeviceInfo/Variant`组是可选的因此您可以选择不能为其指定值，或将它们从咖啡馆。 下表总结了哪些设置那些必需、 可选的而哪些来自硅供应商。

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">所需的设置</th>
    <th align="left">可选设置</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>PhoneMobileOperatorName</p>
    <p>PhoneManufacturerModelName</p>
    <p>PhoneModelName</p></td>
    <td align="left"><p>PhoneMobileOperatorDisplayName</p>
    <p>PhoneSupportPhoneNumber</p>
    <p>PhoneSupportLink</p>
    <p>PhoneOEMSupportLink</p>
    <p>PhoneRoamingSupportPhoneNumber</p></td>
    </tr>
    </tbody>
    </table>

     

4.  咖啡馆保存完成后添加所需的设置的所有值或任何可选设置您选择设置。 按照[电话中 DeviceTargetingInfo 的元数据](https://msdn.microsoft.com/library/windows/hardware/dn772214)，以确保设置正确的值和它们的格式中的指南。

## <a name="span-idconfigureothercustomizationsettingsspanspan-idconfigureothercustomizationsettingsspanconfigure-other-customization-settings"></a><span id="configure_other_customization_settings"></span><span id="CONFIGURE_OTHER_CUSTOMIZATION_SETTINGS"></span>配置其他自定义设置


可以采用多种其他自定义设置，您可以配置为 Windows 移动设备。 对于电话特别要说明的是，通常还需要提供连接设置，如 MMS APN，MMS 代理服务器、 即时消息服务 （如果支持） 等。 在本演练中，我们假设您已经使我们将介绍如何配置这些连接设置配置这些设置。 合作伙伴文档的 MCSF 部分提供了根据方案或您想要启用的区域的基于方案的文档，以帮助您确定需要配置的设置。 有关这些自定义项的详细信息，请参阅︰

-   重写默认值 CountryTable.xml，设置 UICC 插槽有配置和更多的品牌信息[的设备管理自定义项](https://msdn.microsoft.com/library/windows/hardware/dn757439)。
-   [硬件组件的自定义](https://msdn.microsoft.com/library/windows/hardware/dn757441)有关自定义的显示、 存储、 触摸，等信息。
-   [自定义应用程序和 Microsoft 组件](https://msdn.microsoft.com/library/windows/hardware/dn757434)添加电话/SMS 筛选应用程序、 活动电话盖设置以及其他信息。
-   [启动、 初始化设置和关闭自定义](https://msdn.microsoft.com/library/windows/hardware/dn757435)，以了解如何配置期间安装设备，以及更多的时区确认页和语言选项。
-   您可以自定义 Microsoft 边缘的方法的信息的[浏览器的自定义项](https://msdn.microsoft.com/library/windows/hardware/dn757436)。
-   [连接的自定义项](https://msdn.microsoft.com/library/windows/hardware/dn757437)，若要了解有关设置自定义百分比，信号强度条、 首选的数据提供程序列表、 漫游筛选，等等。
-   [自定义桌面体验](https://msdn.microsoft.com/library/windows/hardware/dn757438)进行自定义的设备图标，默认图像的移动设备连接到桌面时出现。
-   [电子邮件的自定义](https://msdn.microsoft.com/library/windows/hardware/dn757440)，以了解如何更改电子邮件应用程序总是有光的背景。
-   [自定义映射](https://msdn.microsoft.com/library/windows/hardware/dn757442)的预加载站点地图数据在用户存储或 SD 卡中的信息映射; 在中国，以及其他附带的电话。
-   [电话联络的自定义项](https://msdn.microsoft.com/library/windows/hardware/dn757443)，若要了解有关品牌设置可视语音邮件，启用即时消息服务和 RCS 和更多的电话联络。
-   添加 OEM 信息有关音频音量限制的[自定义设置的照片、 音乐和视频](https://msdn.microsoft.com/library/windows/hardware/dn757445)镜头的应用程序，等等。
-   若要了解有关的许多自定义[设置的自定义项](https://msdn.microsoft.com/library/windows/hardware/dn757448)可以出现在移动设备上**设置**应用程序中的设置配置。
-   [SMS 和 MMS 的自定义](https://msdn.microsoft.com/library/windows/hardware/dn757449)更多的信息，在 SMS 消息的最大长度为添加编码扩展表的截距拒绝列表中，以及更多。
-   [开始时使用的自定义设置](https://msdn.microsoft.com/library/windows/hardware/dn757450)来更改 Windows 应用商店实时图块的默认行为。 请注意，您可以配置开始布局太，但，已涵盖在[开始 Windows 10 移动版本的布局](https://msdn.microsoft.com/library/windows/hardware/mt171093)和在本演练中的示例所示。

 

 




---
author: kpacquer
Description: "更新的 KMDF 设备驱动程序"
ms.assetid: e391e00a-b764-4d47-8e14-30b4446ddfb2
MSHAttr: PreferredLib:/library/windows/hardware
title: "更新的 KMDF 设备驱动程序"
ms.openlocfilehash: edaae7f63e11c989cf8385469b7a8c60c600457c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="update-a-kmdf-device-driver"></a>更新的 KMDF 设备驱动程序


像所有其他组件添加到操作系统，KMDF （内核模式驱动程序框架） 驱动程序 OS 映像中包含由 Oem 生成图像时使用.spkg 的包文件中引用了一个 OEMInput.xml 文件。

同样，通过使用.spkg 软件包文件发布驱动程序更新。 像所有的更新包，包版本必须增加每次更新;有关详细信息，请参阅[更新的要求](update-requirements.md)。 当准备驱动程序更新时， **DriverVer**指令驱动程序 INF 文件中的值也必须被递增。 本演练演示如何准备 KMDF 设备驱动程序的更新以及更新的驱动程序已加载操作系统。

本主题假定您熟悉与 Windows 设备驱动程序的安装和使用的 INF 文件的一般概念。 有关详细信息，请参阅[设备和驱动程序安装](https://msdn.microsoft.com/library/windows/hardware/ff549731)。

## <a name="span-iddriverinffilesandupdatesspanspan-iddriverinffilesandupdatesspanspan-iddriverinffilesandupdatesspandriver-inf-files-and-updates"></a><span id="Driver_INF_files_and_updates"></span><span id="driver_inf_files_and_updates"></span><span id="DRIVER_INF_FILES_AND_UPDATES"></span>驱动程序 INF 文件和更新


在生成 Windows 10 移动 KMDF 驱动程序项目时，Visual Studio 自动生成一个 INF 文件。 在 Windows 中，驱动程序安装直接使用的 INF 文件。 但是，在 Windows 10 手机，INF 文件被转换到注册表项 (.reg) 文件。 驱动程序打包时在.spkg 文件中包含该.reg 文件。

创建时的 KMDF 驱动程序更新，必须增加两个版本编号︰.spkg 软件包文件和**DriverVer**值在 INF 文件中的版本号。

**包版本**

必须增加软件包的版本号进行的更新将应用于操作系统。 如果不大于现有版本的更新程序包版本，将不会应用更新。

**INF 驱动程序版本**

必须增加 INF 驱动程序的版本号会导致更新的驱动程序数据应用到当前驱动程序注册表中的 System 配置单元。 按以下格式指定的驱动程序版本︰

*MM*/*DD*/*YYYY*, *n*. *n*. *n*. *n*

*MM*将月份、 *DD*为天，和*YYYY*是跟版本号的年份。 版本编号的第一个数字是主要版本，跟的次要版本。 驱动程序的更新，整个字符串计算为版本号。 如果只是日期 (*毫米*/*DD*/*YYYY*) 是递增，它被认为是较新版本的驱动程序。

## <a name="span-iddriverwalkthroughintroductionspanspan-iddriverwalkthroughintroductionspanspan-iddriverwalkthroughintroductionspandriver-walkthrough-introduction"></a><span id="Driver_walkthrough_introduction"></span><span id="driver_walkthrough_introduction"></span><span id="DRIVER_WALKTHROUGH_INTRODUCTION"></span>驱动程序演练简介


驱动程序更新本演练介绍了以下任务︰

-   [生成版本 1 驱动程序包](#buildtheversion1)

-   [添加到 OS 版本 1 的驱动程序](#addingtheversion1)

-   [查看驱动程序的注册表设置](#viewtheregistry)

-   [检查注册表项，以确认驱动程序处于活动状态](#examinetheregistrykeys)

-   [生成版本 2 驱动程序包](#buildingtheversion2)

-   [添加到操作系统的版本 2 驱动程序](#addingtheversion2)

-   [确认更新的驱动程序处于活动状态](#confirmthattheupdateddriver)

在此示例中，使用下面的版本编号︰

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">INF 文件中的驱动程序版本</th>
<th align="left">包版本</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>11/01/2012,1.00.00.00</p></td>
<td align="left"><p>8.00.9907.12</p></td>
</tr>
<tr class="even">
<td align="left"><p>02/19/2013,1.32.00.00</p></td>
<td align="left"><p>8.00.10211.25</p></td>
</tr>
</tbody>
</table>

 

驱动程序文件命名为 XKmdfDriver.sys，，INF 文件 XKmdfDriver.inf。

**请注意**  
您想要在此演练中使用该驱动程序的名称替换这些文件的名称。

 

原来的驱动程序将位于\\将位于 Version1 文件夹和更新的版本\\Version2。

本演练假定下列环境变量都类似于此处所示︰

``` syntax
set AK_ROOT=C:\Program Files (x86)\Windows Kits\10
set WINKIT_ROOT=C:\Program Files (x86)\Windows Kits\10
PATH=%AK_ROOT%\Tools\bin\i386;%WINKIT_ROOT%\bin\x86;%PATH%
```

## <a name="span-idbuildtheversion1spanspan-idbuildtheversion1spanspan-idbuildtheversion1spanbuild-the-version-1-driver-package"></a><span id="BuildTheVersion1"></span><span id="buildtheversion1"></span><span id="BUILDTHEVERSION1"></span>生成版本 1 驱动程序包


使用以下步骤在操作系统中包含第 1 版驱动程序。

1.  驱动程序将文件复制到\\Version1 目录︰

    -   XKmdfDriver.inf

    -   XKmdfdriver.pkg.xml

    -   XKmdfDriver.sys

2.  在 XKmdfDriver.inf 文件中，设置`DriverVer`指令中`[Version]`节如下所示。 突出显示的字符串"11/01/2012,1.00.00.00"是驱动程序的版本号。

    ``` syntax
    …
    [Version]
    Signature="$WINDOWS NT$"
    Class=System
    ClassGuid={4d36e97d-e325-11ce-bfc1-08002be10318}
    Provider=%MSFT%
    DriverVer=11/01/2012,1.00.00.00
    BootCritical=1

    [DestinationDirs]
    DefaultDestDir = 12
    …
    ```

3.  软件包 (XKmdfdriver.pkg.xml) 的 XML 版本 1 的驱动程序，如下所示。 指定 OEM`Owner`名。

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <Package xmlns="urn:Microsoft.WindowsPhone/PackageSchema.v8.00"
      Owner="OEMName"
      OwnerType="OEM"     
      ReleaseType="Test"
      Platform="QC8960"           
      Component="Phone.Test.BaseOS"
      SubComponent="XKmdfDriver"
      Partition="MainOS"
      BinaryPartition="false">
      <Components>
        <OSComponent>
            <Files>
                <File Source="XKmdfDriver.sys" DestinationDir="$(runtime.system32)\drivers"/>
            </Files>
        </OSComponent>
        <Driver InfSource="XKmdfDriver.inf">
            <Reference Source="XKmdfDriver.sys"/>
        </Driver>
      </Components>
    </Package>
    ```

4.  移动到\\Version1 目录设置包版本，如所示，并生成该驱动程序包。

    ``` syntax
    cd \Version1
    set PKGVER=8.00.9907.12
    pkggen  XKmdfDriver.pkg.xml /version:%PKGVER% /build:fre /cpu:ARM /config:"%AK_ROOT%\Tools\bin\i386\pkggen.cfg.xml" /output:. /variables:"HIVE_ROOT=%AK_ROOT%\CoreSystem"
    ```

5.  确认*OEMName*。Phone.Test.BaseOS.XKmdfDriver.spkg 包是生成的。

## <a name="span-idaddingtheversion1spanspan-idaddingtheversion1spanspan-idaddingtheversion1spanadd-the-version-1-driver-to-the-os"></a><span id="AddingTheVersion1"></span><span id="addingtheversion1"></span><span id="ADDINGTHEVERSION1"></span>添加到 OS 版本 1 的驱动程序


使用以下步骤以在操作系统中包括第 1 版驱动程序，通过使用 IUTool 和生产或测试生成。 或者，图像中包含的程序包，然后刷新该图像的移动电话。

1.  通过 USB 电缆连接到计算机的设备。

2.  使用 IuTool 可以将版本 1 驱动程序包添加到现有的映像。

    ``` syntax
    IuTool -p OEMName.Phone.Test.BaseOS.XKmdfDriver.spkg
    ```

3.  确认 IuTool 已能够将包部署到设备

## <a name="span-idviewtheregistryspanspan-idviewtheregistryspanspan-idviewtheregistryspanview-the-driver-registry-settings"></a><span id="ViewTheRegistry"></span><span id="viewtheregistry"></span><span id="VIEWTHEREGISTRY"></span>查看驱动程序的注册表设置


使用以下过程来装载在大容量存储模式下的设备并查看注册表。

1.  重新启动设备连接到 USB 大容量存储模式。 这通过在手机上使用特定的键序列 — — 例如，照相机按钮时按住开机。

2.  将设备连接到 USB 数据线与电脑。

3.  当设备连接到 PC 以 USB 大容量存储模式时，它将显示为计算机上的逻辑驱动器。

4.  以管理员身份打开命令提示符窗口。

5.  找到的文件夹下的注册表 SYSTEM 配置单元**\\WINDOWS\\SYSTEM32\\配置**。

6.  在计算机上启动注册表编辑器 (Regedit.exe)。

7.  在注册表编辑器中，单击**文件** &gt; **加载配置单元**和负载系统配置单元。

8.  提供导入的配置单元的名称 — — 例如，驱动程序\_VERSION1

9.  前进到下一节，检查导入的注册表配置单元的内容。

## <a name="span-idexaminetheregistrykeysspanspan-idexaminetheregistrykeysspanspan-idexaminetheregistrykeysspanexamine-the-registry-keys-to-confirm-that-the-driver-is-active"></a><span id="ExamineTheRegistryKeys"></span><span id="examinetheregistrykeys"></span><span id="EXAMINETHEREGISTRYKEYS"></span>检查注册表项，以确认驱动程序处于活动状态


当 Windows 10 移动安装驱动程序时，下面的注册表项将出现在系统配置单元︰

-   特定于驱动程序的注册表项下创建`SYSTEM\DriverDatabase`。

-   下创建活动驱动程序子项`SYSTEM\ControlSet001\Enum\ROOT\XKmdfDriver`。

以下各节讨论了每个这两个区域。 在注册表中使用此信息确定是否准备好安装该驱动程序以及操作系统具有识别硬件并安装该驱动程序的正确版本。

### <a name="span-iddriverdatabasespanspan-iddriverdatabasespanspan-iddriverdatabasespandriver-database"></a><span id="Driver_database"></span><span id="driver_database"></span><span id="DRIVER_DATABASE"></span>驱动程序数据库

驱动程序设置已准备好在以后安装`SYSTEM\DriverDatabase`。 操作系统将使用此子项时识别新硬件安装驱动程序。 它包含︰

-   有关 XKmdfDriver.inf 的信息

-   一个特定的 GUID `{4d36e97d-e325-11ce-bfc1-08002be10318}` XKmdfDriver 标识为系统类驱动程序，不使用 （例如 ACPI 或 USB） 的动态可枚举总线的驱动程序。 此示例使用系统类驱动程序用于简化本演练中，但所示的概念相似，但有其他类型的驱动程序。

当安装程序包时，将 XKmkdfDriver.inf 添加到`[SYSTEM\DriverDatabase\DeviceIds\{4d36e97d-e325-11ce-bfc1-08002be10318}]`，其中`{4d36e97d-e325-11ce-bfc1-08002be10318}`的系统驱动程序的 GUID。

下面的示例演示系统驱动程序 GUID 中`[SYSTEM\DriverDatabase\DeviceIds\Root\XKmdfDriver]`注册表子项。

``` syntax
[SYSTEM\DriverDatabase\DeviceIds\Root\XKmdfDriver]
"XKmdfDriver.inf"=hex:01,ff,00,00
[SYSTEM\DriverDatabase\DeviceIds\{4d36e97d-e325-11ce-bfc1-08002be10318}]
..
"XKmdfDriver.inf"=hex(0):
```

在`[SYSTEM\DriverDatabase\DriverInfFiles\XKmdfDriver.inf]`子项，该活动的 INF 文件指定的项`"Active"="xkmdfdriver.inf_arm_c8e7ab79be6b088b"`。

`"Active"`条目指向活动驱动程序 INF。 当更新该驱动程序包，则有多个 INF 设置，和`"Active"`指向最新的一个。

``` syntax
[SYSTEM\DriverDatabase\DriverInfFiles\XKmdfDriver.inf]
"Active"="xkmdfdriver.inf_arm_c8e7ab79be6b088b"
@=hex(7):78,00,6b,00,6d,00,64,00,66,00,64,00,72,00,69,00,76,00,65,00,72,00,2e,\
00,69,00,6e,00,66,00,5f,00,61,00,72,00,6d,00,5f,00,63,00,38,00,65,00,37,00,\
61,00,62,00,37,00,39,00,62,00,65,00,36,00,62,00,30,00,38,00,38,00,62,00,00,\
00,00,00
"Configurations"=hex(7):58,00,4b,00,4d,00,44,00,46,00,44,00,52,00,49,00,56,00,\
45,00,52,00,2e,00,4e,00,54,00,00,00,00,00
```

`[SYSTEM\DriverDatabase\DriverPackages\xkmdfdriver.inf_arm_c8e7ab79be6b088b]`子项包含复制 XKmdfDriver.inf 目录中的。

``` syntax
[SYSTEM\DriverDatabase\DriverPackages\xkmdfdriver.inf_arm_c8e7ab79be6b088b]
@="XKmdfDriver.inf"
"BootCritical"=dword:00000001
"Provider"="Microsoft"
"SignerName"=""
"SignerScore"=dword:0d000003
"Version"=hex:ff,ff,05,00,00,00,00,00,7d,e9,36,4d,25,e3,ce,11,bf,c1,08,00,2b,\
e1,03,18,00,40,f9,d5,c3,b7,cd,01,00,00,00,00,00,00,01,00,00,00,00,00,00,00,\
00,00
```

此子项引用与该系统驱动程序关联的服务︰

``` syntax
[SYSTEM\DriverDatabase\DriverPackages\xkmdfdriver.inf_arm_c8e7ab79be6b088b\Configurations\XKMDFDRIVER.NT]
"ConfigFlags"=dword:00000000
"Service"="XKmdfDriver"
```

此子项设置驱动程序说明字符串︰

``` syntax
[SYSTEM\DriverDatabase\DriverPackages\xkmdfdriver.inf_arm_c8e7ab79be6b088b\Descriptors\Root\XKmdfDriver]
"Configuration"="XKMDFDRIVER.NT"
"Description"="%xkmdfdriver_devdesc%"
"Manufacturer"="%StdMfg%"
```

此子项设置驱动程序描述字符串的值︰

``` syntax
[SYSTEM\DriverDatabase\DriverPackages\xkmdfdriver.inf_arm_c8e7ab79be6b088b\Strings]
"xkmdfdriver_devdesc"="X KMDF Driver"
```

### <a name="span-idcontrolsetenumerationspanspan-idcontrolsetenumerationspanspan-idcontrolsetenumerationspancontrol-set-enumeration"></a><span id="Control_set_enumeration"></span><span id="control_set_enumeration"></span><span id="CONTROL_SET_ENUMERATION"></span>控件设置枚举

`[SYSTEM\ControlSet001\Enum\ROOT\XKmdfDriver]`操作系统安装成功的匹配的设备驱动程序 INF 文件时创建。 有关详细信息，请参阅[HKLM\\系统\\开目前控制设置\\枚举注册表树](http://msdn.microsoft.com/library/windows/hardware/ff546173.aspx)在 MSDN 上。

`Control`子项包含用于控制系统启动和设备的某些方面的信息。 有关详细信息，请参阅[HKLM\\系统\\开目前控制设置\\控制注册表树](http://msdn.microsoft.com/library/windows/hardware/ff546165.aspx)在 MSDN 上。

`SYSTEM\ControlSet001\Control\Class\{4d36e97d-e325-11ce-bfc1-08002be10318}\0120`指示驱动程序必须在系统类驱动程序之间的 120th 秩。 该子项包含驱动程序日期和版本如下所示︰

``` syntax
[SYSTEM\ControlSet001\Control\Class\{4d36e97d-e325-11ce-bfc1-08002be10318}\0120]
"DriverDesc"="X KMDF Driver"
"ProviderName"="Microsoft"
"DriverDateData"=hex:00,40,f9,d5,c3,b7,cd,01
"DriverDate"="11-1-2012"
"DriverVersion"="1.0.0.0"
"InfPath"="XKmdfDriver.inf"
"InfSection"="XKMDFDRIVER.NT"
"MatchingDeviceId"="ROOT\\XKmdfDriver"
```

DeviceClasses 子项包含的设备实例 ID:

``` syntax
[SYSTEM\ControlSet001\Control\DeviceClasses\{5cdce65b-f1bc-4e15-a1f8-c541f21c43f2}\##?#ROOT#XKmdfDriver#0000#{5cdce65b-f1bc-4e15-a1f8-c541f21c43f2}]
"DeviceInstance"="ROOT\\XKmdfDriver\\0000"
```

此下一步的子项将 XKmdfDriver 与系统 containerId 00000000-0000-0000-ffff-ffffffffffff 相关联︰

``` syntax
[SYSTEM\ControlSet001\Control\DeviceContainers\{00000000-0000-0000-FFFF-FFFFFFFFFFFF}\BaseContainers\{00000000-0000-0000-FFFF-FFFFFFFFFFFF}]
..
"ROOT\\XKmdfDriver\\0000"=hex(0):
..
```

`[SYSTEM\ControlSet001\Enum\ROOT\XKmdfDriver\0000]`包含有关安装的驱动程序的信息。 它具有一个实例中， `XKmdfDriver\0000`:

``` syntax
[SYSTEM\ControlSet001\Enum\ROOT\XKmdfDriver\0000]
"HardwareID"=hex(7):52,00,4f,00,4f,00,54,00,5c,00,58,00,4b,00,6d,00,64,00,66,\
  00,44,00,72,00,69,00,76,00,65,00,72,00,00,00,00,00
"ConfigFlags"=dword:00000000
"DeviceReported"=dword:00000001
"Service"="XKmdfDriver"
"Capabilities"=dword:00000000
"ClassGUID"="{4d36e97d-e325-11ce-bfc1-08002be10318}"
"DeviceDesc"="@XKmdfDriver.inf,%xkmdfdriver_devdesc%;X KMDF Driver"
"Driver"="{4d36e97d-e325-11ce-bfc1-08002be10318}\\0120"
"Mfg"="@XKmdfDriver.inf,%StdMfg%;"
"ContainerID"="{00000000-0000-0000-FFFF-FFFFFFFFFFFF}"
```

`[SYSTEM\ControlSet001\services\XKmdfDriver]`包含驱动程序文件"ImagePath"值;它是以十六进制二进制格式编码的 ASCII 字符。 实际值是"ImagePath"= REG\_展开\_SZ:"\\系统根目录\\System32\\驱动程序\\XKmdfDriver.sys"。 有关详细信息，请参阅 MSDN 上的[注册表值类型](http://msdn.microsoft.com/library/windows/desktop/ms724884.aspx)。

``` syntax
[SYSTEM\ControlSet001\services\XKmdfDriver]
"DisplayName"="@XKmdfDriver.inf,%xkmdfdriver_DevDesc%;X KMDF Driver"
"ErrorControl"=dword:00000001
"ImagePath"=hex(2):5c,00,53,00,79,00,73,00,74,00,65,00,6d,00,52,00,6f,00,6f,00,\
74,00,5c,00,53,00,79,00,73,00,74,00,65,00,6d,00,33,00,32,00,5c,00,64,00,72,\
00,69,00,76,00,65,00,72,00,73,00,5c,00,58,00,4b,00,6d,00,64,00,66,00,44,00,\
72,00,69,00,76,00,65,00,72,00,2e,00,73,00,79,00,73,00,00,00
"Start"=dword:00000001
"Type"=dword:00000001
"Owners"=hex(7):58,00,4b,00,6d,00,64,00,66,00,44,00,72,00,69,00,76,00,65,00,72,\
00,2e,00,69,00,6e,00,66,00,00,00,00,00
```

`[SYSTEM\ControlSet001\services\XKmdfDriver\Parameters\Wdf]`包含 WDF 的版本号︰

``` syntax
[SYSTEM\ControlSet001\services\XKmdfDriver\Parameters\Wdf]
"WdfMajorVersion"=dword:00000001
"WdfMinorVersion"=dword:0000000b
"TimeOfLastSqmLog"=hex(b):20,41,89,d7,2c,c0,cd,01
```

## <a name="span-idclosethetoolsspanspan-idclosethetoolsspanspan-idclosethetoolsspanclose-the-tools-and-eject-the-device"></a><span id="CloseTheTools"></span><span id="closethetools"></span><span id="CLOSETHETOOLS"></span>关闭工具并弹出设备


1.  在注册表编辑器中，单击**文件**&gt;卸载**卸载配置单元**`DRIVER_VERSION1`配置单元，以使 PC 注册表还原到其以前的状态。

2.  关闭注册表编辑器。

3.  关闭命令提示符窗口和查看临时文件夹时所用的任何打开 Windows 资源管理器实例。

4.  弹出电话 （使用**安全删除硬件和弹出媒体**中的通知区域或 Windows 资源管理器**弹出**命令），然后再断开设备的连接，从电脑。

## <a name="span-idbuildingtheversion2spanspan-idbuildingtheversion2spanspan-idbuildingtheversion2spanbuild-the-version-2-driver-package"></a><span id="BuildingTheVersion2"></span><span id="buildingtheversion2"></span><span id="BUILDINGTHEVERSION2"></span>生成版本 2 驱动程序包


如上文所述，新的驱动程序版本将为 2/19/2013,1.32.00.00，将包含在新的软件包版本 8.00.10211.25。

1.  创建第二个副本中的驱动程序文件的\\Version2 目录。

2.  编辑 XKmdfDriver.inf 文件并更改`DriverVer`到 02/19/2013,1.32.00.00。

3.  添加新的注册表值，名为"DW123"的 DWORD 类型。 此项存在被用作其他指示第 2 版驱动程序处于活动状态。

    ``` syntax
    [Version]
    Signature="$WINDOWS NT$"
    Class=System
    ClassGuid={4d36e97d-e325-11ce-bfc1-08002be10318}
    Provider=%MSFT%
    DriverVer=02/19/2013,1.32.00.00
    [XKMDFDRIVER.NT.HW]
    AddReg=XKMDFDRIVER.AddReg

    [XKMDFDRIVER.AddReg]
    HKR,," DW123",    %REG_DWORD%, 0x4567
    ...
    ```

4.  移动到\\Version2 目录设置包版本，然后生成包。

    ``` syntax
    cd \Version2
    set PKGVER=8.00.10211.25
    pkggen  XKmdfDriver.pkg.xml /version:%PKGVER% /build:fre /cpu:ARM /config:"%AK_ROOT%\Tools\bin\i386\pkggen.cfg.xml" /output:. /variables:"HIVE_ROOT=%AK_ROOT%\CoreSystem"
    ```

## <a name="span-idaddingtheversion2spanspan-idaddingtheversion2spanspan-idaddingtheversion2spanadd-the-version-2-driver-to-the-os"></a><span id="AddingTheVersion2"></span><span id="addingtheversion2"></span><span id="ADDINGTHEVERSION2"></span>添加到操作系统的版本 2 驱动程序


使用以下步骤包含在 OS 中使用 IUTool 和生产的第 2 版驱动程序或测试生成︰

1.  通过 USB 电缆连接到计算机的设备。

2.  使用 IuTool 版本 2 驱动程序包添加到现有图像。

    ``` syntax
    IuTool -p OEMName.Phone.Test.BaseOS.XKmdfDriver.spkg
    ```

3.  确认 IUTool 已能够将包部署到设备

## <a name="span-idconfirmthattheupdateddriverspanspan-idconfirmthattheupdateddriverspanspan-idconfirmthattheupdateddriverspanconfirm-that-the-updated-driver-is-active"></a><span id="ConfirmThatTheUpdatedDriver"></span><span id="confirmthattheupdateddriver"></span><span id="CONFIRMTHATTHEUPDATEDDRIVER"></span>确认更新的驱动程序处于活动状态


使用以下过程来确认更新的驱动程序处于活动状态。

1.  [查看驱动程序的注册表设置](#viewtheregistry)在前面描述的过程可用于加载和查看系统注册表配置单元。

2.  DriverPackages 应具有两个 INF 注册表键集︰ 分别为以前安装的驱动程序和更新后的驱动程序。

    ``` syntax
    [SYSTEM\DriverDatabase\DriverPackages\xkmdfdriver.inf_arm_6ec7dae5e1ab5fd5]
    [SYSTEM\DriverDatabase\DriverPackages\xkmdfdriver.inf_arm_c8e7ab79be6b088b]
    ```

3.  `Active`在 XKmdfDriver.inf 中应指向新的 INF 键︰

    ``` syntax
    [SYSTEM\DriverDatabase\DriverInfFiles\XKmdfDriver.inf]
    "Active"="xkmdfdriver.inf_arm_6ec7dae5e1ab5fd5"
    ```

4.  驱动程序仍然有 120th 等级下系统类驱动程序，但应更新的日期和版本。

    -   "DriverDate"="2-19-2013年"

    -   "DriverVersion"="1.32.0.0"

    ``` syntax
    [SYSTEM\ControlSet001\Control\Class\{4d36e97d-e325-11ce-bfc1-08002be10318}\0120]
    "DriverDate"="2-19-2013"
    "DriverDateData"=hex:00,c0,69,0f,34,0e,ce,01
    "DriverDesc"="X KMDF Driver"
    "DriverVersion"="1.32.0.0"
    "InfPath"="XKmdfDriver.inf"
    "InfSection"="XKMDFDRIVER.NT"
    "MatchingDeviceId"="ROOT\\XKmdfDriver"
    "ProviderName"="Microsoft"
    ```

5.  新添加的 DWORD 注册表值 DW123 应该出现在`Device Parameters`的子项。

    ``` syntax
    [SYSTEM\ControlSet001\Enum\ROOT\XKmdfDriver\0000\Device Parameters]
    "DWORD123"="0x4567"
    ```

6.  [关闭工具和弹出电话](#closethetools)中前面所述的过程用于安全断开设备连接

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[更新](index.md)

 

 







---
author: Justinha
Description: "WinPE︰ 创建应用程序"
ms.assetid: 93848579-fd6d-4d51-bb51-f5f412833ad8
MSHAttr: PreferredLib:/library/windows/hardware
title: "WinPE︰ 创建应用程序"
ms.openlocfilehash: 69e2ce341fb028c481356bfb38159efa657c6e16
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="winpe-create-apps"></a>WinPE︰ 创建应用程序


Windows PE (WinPE) 授权于独立软件供应商 (Isv) 和原始设备制造商 (Oem) 来创建自定义的部署和恢复实用程序。 本主题提供有关 Isv 和 Oem 开发部署和恢复应用程序运行在 Windows PE 的准则。

**请注意**  
Windows PE 不是一般用途的操作系统。 它不可能用于部署和恢复以外的任何目的。 它不应作为瘦客户端或嵌入式的操作系统使用。 有其他 Microsoft® 产品，如 Windows 嵌入式 CE，可能用于这些目的。

 

## <a name="span-idextensibilityspanspan-idextensibilityspanspan-idextensibilityspanextensibility"></a><span id="Extensibility"></span><span id="extensibility"></span><span id="EXTENSIBILITY"></span>可扩展性


Windows PE 应用程序大部分是固定功能外壳应用程序提供自己的 GUI。 两个示例是 Windows 安装程序的应用程序和 Windows 恢复环境 (Windows RE)。

-   如果它是可接受，若要显示一个命令提示符，然后修改 Startnet.cmd-这是最方便的方法来自动启动应用程序。 请参阅[WinPE︰ 安装和自定义](winpe-mount-and-customize.md)。

-   要绕过命令行，并在 GUI 中启动应用程序，请使用 Winpeshl.exe、 Wpeinit.exe、 wpeutil.exe 和 wpeutil.dll。

## <a name="span-idwinpeshlexewpeinitexewpeutilexeandwpeutildllspanspan-idwinpeshlexewpeinitexewpeutilexeandwpeutildllspanspan-idwinpeshlexewpeinitexewpeutilexeandwpeutildllspanwinpeshlexe-wpeinitexe-wpeutilexe-and-wpeutildll"></a><span id="Winpeshl.exe__Wpeinit.exe__wpeutil.exe__and_wpeutil.dll"></span><span id="winpeshl.exe__wpeinit.exe__wpeutil.exe__and_wpeutil.dll"></span><span id="WINPESHL.EXE__WPEINIT.EXE__WPEUTIL.EXE__AND_WPEUTIL.DLL"></span>Winpeshl.exe、 Wpeinit.exe、 wpeutil.exe 和 wpeutil.dll


默认情况下，Winpeshl.exe 是第一个进程运行在 Windows PE 启动时。 这由以下注册表值的类型 REG\_SZ。

``` syntax
HKEY_LOCAL_MACHINE
   System
      Setup
         CmdLine
```

Winpeshl.exe 搜索名为 Winpeshl.ini 的文件。 如果该文件不存在，Winpeshl.exe 将启动 Cmd.exe 进程执行的 Startnet.cmd 脚本。 如果 Winpeshl.ini 确实存在，而且它包含要启动的应用程序，这些应用程序而不是 Cmd.exe 执行。

Wpeinit.exe 安装插即用 (PnP) 设备，启动网络栈中，并在 Windows PE 启动时处理 Unattend.xml 设置。 有关详细信息，请参阅[Wpeinit 和 Startnet.cmd︰ 使用 WinPE 启动脚本](wpeinit-and-startnetcmd-using-winpe-startup-scripts.md)。

通过允许 Wpeinit.exe 运行 Windows PE 启动时，或通过运行[Wpeutil 命令行选项](wpeutil-command-line-options.md)的命令来运行，可以在任何时候启动网络。

自定义应用程序可以直接插入 Wpeutil.dll 的[则](http://go.microsoft.com/fwlink/?LinkId=203026)和[GetProcAddress](http://go.microsoft.com/fwlink/?LinkId=203027)函数与调用的 shell。 相关的信息，请参阅[信息︰ 使用 GetProcAddress() 与 LoadLibrary() 的替代方法](http://go.microsoft.com/fwlink/?LinkId=203028)。

下面的代码示例中所示，每个由 Wpeutil.dll 导出的函数有[WinMain 函数](http://go.microsoft.com/fwlink/?LinkId=203029)相同的函数签名。

``` syntax
int InitializeNetworkingW(
HINSTANCE hInstance,
HINSTANCE hPrevInstance,
LPSTR lpCmdLine,
int nCmdShow
);
```

下面的代码示例演示如何初始化网络。

``` syntax
#include <windows.h>
#include <tchar.h>
#include <stdio.h>
typedef int (*WpeutilFunction)( 
HINSTANCE hInst, 
HINSTANCE hPrev, 
LPTSTR lpszCmdLine, 
int nCmdShow 
);
int __cdecl _tmain( int argc, TCHAR *argv[] )
{
    
HMODULE         hWpeutil          = NULL;
    
WpeutilFunction InitializeNetwork = NULL;
    
int             result            = 0;
    
TCHAR           szCmdLine[]       = _T("");
    
hWpeutil = LoadLibrary( _T("wpeutil") );
    
if( NULL == hWpeutil )
    
{
        _tprintf( _T("Unable to load wpeutil.dll \ n") );
        
return GetLastError();
}
    
InitializeNetwork = (WpeutilFunction)GetProcAddress( 
hWpeutil, 
"InitializeNetworkW" 
);
    
if( NULL == InitializeNetwork )
    
{
        
FreeLibrary( hWpeutil );
        
return GetLastError();
    
}
    
result = InitializeNetwork( NULL, NULL, szCmdLine, SW_SHOW );
    
if( ERROR_SUCCESS == result )
    
{
        _tprintf( _T("Network initialized. \ n") );
    
}
  
else
    
{
        _tprintf( _T("Initialize failed: 0x%08x"), result );
    
}
    
FreeLibrary( hWpeutil );

return result;}
```

Wpeutil.dll 导出的完整列表，请参阅[Wpeutil 命令行选项](wpeutil-command-line-options.md)。

## <a name="span-idvisualstudioprojectsettingsspanspan-idvisualstudioprojectsettingsspanspan-idvisualstudioprojectsettingsspanvisual-studio-project-settings"></a><span id="Visual_Studio_project_settings"></span><span id="visual_studio_project_settings"></span><span id="VISUAL_STUDIO_PROJECT_SETTINGS"></span>Visual Studio 项目设置


一些基本的 Visual Studio 项目设置可能不同于创建 Visual Studio 项目向导的默认设置。 确保您设置项目的生成设置要生成的应用程序和 Dll 与兼容的 Windows PE，如下所示︰

1.  必须开发 Windows PE 应用程序与本机 C 或 c + + 代码不使用 MFC 或 atl。 因此，如果您使用 Visual Studio 项目向导，选择一个 Win32 项目并确保 MFC 或 ATL 均不进行检查。

2.  设置项目选项将链接到静态 C/c + + 运行时库，不 Msvcrt.dll.dll 版本。

3.  打开项目属性并设置**配置属性\\C/c + + 运行时库**对**多线程**或**多线程的调试**，没有一个.dll 版本。 如果您没有执行此步骤，您的应用程序可能无法运行在 Windows PE 上。

4.  如果您准备托管您的应用程序在 64 位版本的 Windows PE，将项目设置生成选项来编译使用 x64 的所有二进制文件在 Visual Studio 中的编译器。

5.  如果您准备托管您的应用程序在 32 位版本的 Windows PE，设置的项目选项来编译与 x86 编译器。

6.  确保您的项目没有 /clr︰ 编译器选项集。 此选项将生成托管的 c + + 代码，这将不会运行在 Windows PE 上。

**警告**  
您的应用程序可以使用自定义的.dll 文件的编写或从第三方许可。 为 Windows PE，这些.dll 文件添加到您的应用程序。 但是，不要使用 Msvcrt.dll 并不包括不属于 Windows PE 的其他 Windows.dll 文件。

 

## <a name="span-idapicompatibilityreferencespanspan-idapicompatibilityreferencespanspan-idapicompatibilityreferencespanapi-compatibility-reference"></a><span id="API_Compatibility_reference"></span><span id="api_compatibility_reference"></span><span id="API_COMPATIBILITY_REFERENCE"></span>API 兼容性参考


Windows PE 是轻量级、 引导操作系统基于 Windows 操作系统中的组件的子集。 它被设计为主机部署和恢复应用程序。 在这种情况下，它包含很多 Windows 二进制文件所需主机对这些类的应用程序的最重要的 Api。 由于大小和其他设计的限制，并不是所有 Windows 二进制文件都都在 Windows PE 中，并因此不是所有的 Windows Api 都是存在或无法使用。

### <a name="span-idsupportedapisinwindowspespanspan-idsupportedapisinwindowspespanspan-idsupportedapisinwindowspespansupported-apis-in-windows-pe"></a><span id="Supported_APIs_in_Windows_PE"></span><span id="supported_apis_in_windows_pe"></span><span id="SUPPORTED_APIS_IN_WINDOWS_PE"></span>在 Windows PE 中受支持的 Api

在 Windows PE 中支持以下 Api:

1.  [Windows API 设置 (Mincore.lib)](http://go.microsoft.com/fwlink/?LinkId=330240)。

2.  [部署映像服务和管理 (DISM) API (Dismapi.lib)](http://go.microsoft.com/fwlink/?LinkId=330239)。

3.  [图像处理的窗口 (Wimgapi.lib) 的 Api](http://go.microsoft.com/fwlink/?LinkId=330241)。

如果 API 行为与上完整的 Windows 操作系统和 Windows SDK 的 Windows 操作系统中所述，将其视为受支持，除非另有说明，否则，应用程序可以使用基本相同。 因为 Windows PE 基于来自 Windows 组件，它包含重大发布在 Windows SDK 的 Windows 操作系统的 Windows Api 的子集。 除非它们受到了唯一的 Windows PE 环境，将相同或几乎相同的作为完整的 Windows 操作系统上的参数、 调用约定和这些受支持的 Api 的行为。 应用程序使用这些 Api 只应该是完整的 Windows 操作系统和 Windows PE 之间移植。

在某些情况下，将可用的 Windows PE 可能的参数值的子集。 这可能是因为运行时环境，如运行在只读介质，没有对持久状态或其他设计限制访问的唯一条件。 在这种情况下，API 可能不受支持，但仍可能会用来完成特定的任务，如果没有其他选择。

一般情况下，如果 API 不正确或根本不在 Windows PE，它不支持，不能使用，即便它驻留在 Windows PE 中包含的二进制文件。 由于 Windows PE 是一个子集的 Windows 操作系统，或者运行时设计的特定注意事项 Windows PE 可能失败的 API。 此类故障，不考虑 Windows PE 中的 bug。

因为很多 Windows 组件未包含在 Windows PE 中，很多 Api 都不可用。 因为他们所在的 Windows 二进制文件不存在，他们可能会完全丢失。 或者，它们可能只部分存在因为驻留在其中的 Windows 二进制是存在，虽然不是它们所依赖的一个或多个二进制文件。 此外，一些存在于 Windows PE 的 Api 不正常运行，比它们在 Windows 中的行为不同。 这些 Api 不受支持，不得使用，因为它们在 Windows PE 的行为未定义。

有时，可能是没有合适的 API 来完成特定的任务。 若要查找的备选方案，将需要不同的应用程序逻辑、 不同的算法设计或重定义的基础问题。

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>相关的主题


[对于 Windows 10 WinPE](winpe-intro.md)

[WinPE︰ 调试应用程序](winpe-debug-apps.md)

 

 







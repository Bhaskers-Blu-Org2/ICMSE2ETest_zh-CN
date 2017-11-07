---
author: kpacquer
Description: "在 MMO 的触摸界面的访问"
ms.assetid: 4455627d-ba59-48f1-9327-c9e2c30509da
MSHAttr: PreferredLib:/library/windows/hardware
title: "在 MMO 的触摸界面的访问"
ms.openlocfilehash: b73d8a7b7901b0005ada895989fbba057c448b2b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="access-the-touch-interface-in-mmos"></a>在 MMO 的触摸界面的访问


可以捕获并在 MMO 使用正确的触摸驱动程序支持触摸控制器输出。 触控界面示例说明了如何可以收集触摸 MMO 来实现制造测试中的坐标。

## <a name="span-idtouchsamplerequirementsspanspan-idtouchsamplerequirementsspanspan-idtouchsamplerequirementsspantouch-sample-requirements"></a><span id="Touch_sample_requirements"></span><span id="touch_sample_requirements"></span><span id="TOUCH_SAMPLE_REQUIREMENTS"></span>触摸屏输入示例要求


该代码示例要求 Microsoft.Input.TchHID.spkg 包装，以包括在映像 （主操作系统或 MMO）。 Microsoft.Input.TchHID.spkg 包包含 tchhid.sys，实现**CreateFile**和**Readfile**函数使用的示例代码。

## <a name="span-idtouchsamplecodespanspan-idtouchsamplecodespanspan-idtouchsamplecodespantouch-sample-code"></a><span id="Touch_sample_code"></span><span id="touch_sample_code"></span><span id="TOUCH_SAMPLE_CODE"></span>触摸屏输入的示例代码


此示例用户模式应用程序显示触摸屏幕驱动程序接收到的触摸坐标。

示例应用程序使用**CreateFile**函数打开设备接收原始触摸样本独占句柄。 设备名称"TouchRaw0"由 tchhid.sys 公开，HID 触摸类驱动程序由 Microsoft 提供的包括在 Microsoft.Input.TchHID.spkg。

``` syntax
#define TOUCH_RAW_SAMPLES_DEVICE_NAME L"\\\\.\\TouchRaw0"
```

成功打开句柄后，应用程序循环，直到接触接触点接收屏幕的左上角附近。 应用程序读取并显示坐标和关联的触摸屏输入联系人 id。

``` syntax
#include "sample.h"
#include <cfgmgr32.h>
#include <strsafe.h>

int main()
{
    HANDLE testDriver = INVALID_HANDLE_VALUE;
    BOOL exit = FALSE;
    INT32 i;
    TouchInfo touchInfo = {0};

    //
    // Open an exclusive handle to the device to get raw samples
    //
    testDriver = CreateFile(
        L"\\\\.\\TouchRaw0",
        GENERIC_READ,
        0,
        NULL,
        OPEN_EXISTING,
        0,
        NULL);


    if (INVALID_HANDLE_VALUE == testDriver)
    {
        goto exit;
    }

    //
    // Loop, printing touches to the debugger.
    // Release in upper-left corner ends the test.
    //
    while (!exit)
    {
        DWORD touchInfoBytesRead = 0;

        //
        // Wait for data
        //
        if (!ReadFile(
            testDriver,
            &touchInfo,
            sizeof(TouchInfo),
            &touchInfoBytesRead,
            NULL))
        {
            goto exit;
        }

        if (touchInfoBytesRead == 0)
        {
            goto exit;
        }

        //
        // Print to debugger
        //
        for (i=0; i<touchInfo.ContactCount; i++)
        {
            WCHAR infoString[MAX_PATH] = {0};

            StringCchPrintf(
                infoString,
                MAX_PATH,
                L"%d: Contact ID %d, at (%d,%d) is %s\r\n",
                GetTickCount(),
                touchInfo.ContactArray[i].ContactID,
                touchInfo.ContactArray[i].ScreenX,
                touchInfo.ContactArray[i].ScreenY,
                FLAGS_TO_STRING(touchInfo.ContactArray[i].Flags));
                
            OutputDebugString(infoString);
        }

        //
        // Look for program exit
        //
        for (i=0; i<touchInfo.ContactCount; i++)
        {
            if ((touchInfo.ContactArray[i].ScreenX < 50) &&
                (touchInfo.ContactArray[i].ScreenY < 50) &&
                (touchInfo.ContactArray[i].Flags & InputEventFlag_Up))
            {
                OutputDebugString(L"Touch below (50,50), quitting!\r\n");
                exit = TRUE;
            }
        }
    }

exit:
    if (testDriver != INVALID_HANDLE_VALUE)
    {
        CloseHandle(testDriver);
    }

    return 0;
}
```

应用程序使用 TouchInfo 和 TouchContact 数据结构中，%WPDKCONTENTROOT%中定义了\\包括\\um\\WinPhoneInput.h。 此处显示的标头代码了。

``` syntax
#pragma once

#include <windows.h>
#include <initguid.h>
#include <devguid.h>

//
// This device name is used to access raw touch samples from user mode.
//

#define TOUCH_RAW_SAMPLES_DEVICE_NAME L"\\\\.\\TouchRaw0"

enum InputEventFlag
{
    InputEventFlag_None     = 0x0000,
    
    InputEventFlag_Down     = 0x0001,
    InputEventFlag_Move     = 0x0002,
    InputEventFlag_Hold     = 0x0002,
    InputEventFlag_Up       = 0x0004,
    
    InputEventFlag_Empty    = 0x1000,
    InputEventFlag_Invalid  = 0x2000,
    
    InputEventFlag_TestSync = 0x8000
};

typedef struct _TouchContact
{
    UINT16         ContactID;
    UINT16         Flags;            // See InputEventFlag_*
    INT16          ScreenX;          // Screen Space X-Position
    INT16          ScreenY;          // Screen Space Y-Position
    INT16          WindowX;          // Ignore
    INT16          WindowY;          // Ignore
} TouchContact;

typedef struct _TouchInfo
{
    UINT16         Size;             // Size, in bytes, of this structure (includes n contacts)
    UINT16         Flags;            // Ignore
    UINT32         TimeStamp;        // Driver timestamp
    HANDLE         Source;           // Ignore
    UINT32         SessionID;        // Ignore
    INT32          ContactCount;     // Count of touch contact data points
    TouchContact   ContactArray[10]; // Collection of contacts
} TouchInfo;

#define FLAGS_TO_STRING(x) \
    (x & InputEventFlag_Down) ? L"Down" : \
    (x & InputEventFlag_Move) ? L"Move" : \
    (x & InputEventFlag_Up)   ? L"Up"   : \
    L"Unknown"
```

## <a name="span-idbuildinganddeployingthesampleapplicationspanspan-idbuildinganddeployingthesampleapplicationspanspan-idbuildinganddeployingthesampleapplicationspanbuilding-and-deploying-the-sample-application"></a><span id="Building_and_deploying_the_sample_application"></span><span id="building_and_deploying_the_sample_application"></span><span id="BUILDING_AND_DEPLOYING_THE_SAMPLE_APPLICATION"></span>构建和部署示例应用程序


若要生成用户模式下测试应用程序，请完成以下步骤。

1.  在 Visual Studio 中创建一个新的用户模式应用程序项目。 有关详细信息，请参阅[开发 MMO 测试应用程序](develop-mmos-test-applications.md)

2.  向项目中添加了示例代码的头文件。

3.  生成解决方案，确保它生成成功。

4.  禁用代码完整性在 MMO，或签名测试可执行程序。 有关更多信息，请参见[测试应用程序的开发的 MMO](develop-mmos-test-applications.md)"安全中 MMO，"。

5.  将可执行文件部署到设备并运行该应用程序。 有关详细信息，请参阅[部署和测试 MMO 在用户模式下测试应用程序](deploy-and-test-a-user-mode-test-application-in-mmos.md)。

 

 






---
author: kpacquer
Description: "您可以确定该设备是否处于制造模式或不能通过使用内核模式或用户模式 API。"
ms.assetid: fc888a9a-a004-4689-9972-a40b4d5ba50c
MSHAttr: PreferredLib:/library/windows/hardware
title: "检测到制造模式"
ms.openlocfilehash: f4607ffafca8fbd79b499637cd4795bcb8e50ca8
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="detect-manufacturing-mode"></a>检测到制造模式


您可以确定该设备是否处于制造模式或不能通过使用内核模式或用户模式 API。

在内核模式下，一个新的 API 中定义了 wdm.h:

``` syntax
_IRQL_requires_max_(APC_LEVEL)
NTKERNELAPI
BOOLEAN
ExIsManufacturingModeEnabled (
    VOID
    );
```

下面是如何使用它的一个示例︰

``` syntax
BOOLEAN ManufacturingModeEnabled = FALSE;

NTSTATUS
DriverEntry(
    PDRIVER_OBJECT DriverObject,
    PUNICODE_STRING RegistryPath
    )
{
...
    ManufacturingModeEnabled = ExIsManufacturingModeEnabled();
...
}

NTSTATUS
DoManufacturingOperation(
    VOID
    )
{
    if (ManufacturingModeEnabled == FALSE) {
        return STATUS_NOT_SUPPORTED;
    }
...
    return STATUS_SUCCESS;
}
```

在用户模式下，API 是在 sysinfoapi.h 中定义的︰

``` syntax
WINBASEAPI
BOOL
WINAPI
GetOsManufacturingMode(
    _Out_ PBOOL pbEnabled
    );
```

下面是如何使用它的一个示例︰

``` syntax
DWORD
DoManufacturingOperation(
    VOID
    )
{
    DWORD Error = ERROR_SUCCESS;
    BOOL ManufacturingModeEnabled = FALSE;

    if (!GetOsManufacturingMode(&ManufacturingModeEnabled)) {
        Error = GetLastError();
    }

    if ((Error != ERROR_SUCCESS) ||
        (ManufacturingModeEnabled == FALSE)) {
        return ERROR_NOT_SUPPORTED;
    }
...
    return ERROR_SUCCESS;
}
```

 

 






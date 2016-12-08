---
title: stackwalk
description: stackwalk
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 00864c2f-0a49-4d6f-a65d-a792245f2875
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: f02db1488480c0320c7d64d5ceea61106c5509b2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="stackwalk"></a>stackwalk


显示堆栈审核选项。 直接在命令行上或文件中，则可以指定堆栈审核标志。

``` syntax
xperf -on base -stackwalk ThreadCreate+ProcessCreate
```

- 或者-

``` syntax
xperf -on base -stackwalk ThreadCreate -stackwalk ProcessCreate
```

- 或者-

``` syntax
xperf -on base -stackwalk @stack.txt
```

- 或者-

``` syntax
xperf -on base -stackwalk 0x0501
```

## <a name="remarks"></a>备注


可以指定自定义堆栈审核标志格式︰ 0xmmnnmmnn**，其中*mm*是事件组， *nn*是事件类型。

该文件可以包含空行或前缀加一个感叹号 （！） 的意见。

下面的列表显示堆栈审核的识别的标志︰

-   AlpcClosePort

-   AlpcConnectFail

-   AlpcConnectRequest

-   AlpcConnectSuccess

-   AlpcReceiveMessage

-   AlpcSendMessage

-   AlpcUnwait

-   AlpcWaitForNewMessage

-   AlpcWaitForReply

-   CcCanIWriteFail

-   CcFlushCache

-   CcFlushSection

-   CcLazyWriteScan

-   CcReadAhead

-   CcWorkitemComplete

-   CcWorkitemDequeue

-   CcWorkitemEnqueue

-   CcWriteBehind

-   ContiguousMemoryGeneration

-   CritSecCollision

-   CSwitch

-   DiskFlushInit

-   DiskReadInit

-   DiskWriteInit

-   ExecutiveResource

-   FileCleanup

-   宏

-   文件

-   文件删除

-   FileDirEnum

-   FileDirNotify

-   FileFlush

-   FileFSCTL

-   FileOpEnd

-   FileQueryInformation

-   FileRead

-   FileRename

-   FileSetInformation

-   FileWrite

-   HardFault

-   HeapAlloc

-   HeapCreate

-   HeapDestroy

-   HeapFree

-   HeapRangeCreate

-   HeapRangeDestroy

-   HeapRangeRelease

-   HeapRangeReserve

-   HeapRealloc

-   ImageLoad

-   ImageUnload

-   KernelQueueDequeue

-   KernelQueueEnqueue

-   KernelSignal

-   KernelSignalInit

-   KernelSync

-   KernelSyncAll

-   KernelWaitSync

-   KernelWaitSyncAll

-   映射文件

-   标记

-   MiniFilterPostOpInit

-   MiniFilterPreOpInit

-   PagefaultAV

-   PagefaultCopyOnWrite

-   PagefaultDemandZero

-   PagefaultGuard

-   PagefaultHard

-   PagefaultTransition

-   PagefileBackedImageMapping

-   PageRangeAccess

-   PageRangeRelease

-   PoolAlloc

-   PoolAllocSession

-   PoolFree

-   PoolFreeSession

-   PowerDeviceNotify

-   PowerDeviceNotifyComplete

-   PowerIdleStateChange

-   PowerPerfStateChange

-   PowerPostSleep

-   PowerPreSleep

-   PowerSessionCallout

-   PowerSessionCalloutReturn

-   PowerSetDevicesState

-   PowerSetDevicesStateReturn

-   PowerSetPowerAction

-   PowerSetPowerActionReturn

-   PowerThermalConstraint

-   ProcessCreate

-   ProcessDelete

-   配置文件

-   ProfileSetInterval

-   ReadyThread

-   RegCloseKey

-   RegCreateKey

-   RegDeleteKey

-   RegDeleteValue

-   RegEnumerateKey

-   RegEnumerateValueKey

-   RegFlush

-   RegKcbCreate

-   RegKcbDelete

-   RegOpenKey

-   RegQueryKey

-   RegQueryMultipleValue

-   RegQueryValue

-   RegSetInformation

-   RegSetValue

-   RegVirtualize

-   SplitIO

-   SyscallEnter

-   SyscallExit

-   ThreadCreate

-   ThreadDelete

-   ThreadPoolCallbackCancel

-   ThreadPoolCallbackDequeue

-   ThreadPoolCallbackEnqueue

-   ThreadPoolCallbackStart

-   ThreadPoolCallbackStop

-   ThreadPoolClose

-   ThreadPoolCreate

-   ThreadPoolSetMaxThreads

-   ThreadPoolSetMinThreads

-   ThreadSetBasePriority

-   ThreadSetPriority

-   TimerSetOneShot

-   TimerSetPeriodic

-   UnMapFile

-   VirtualAlloc

-   VirtualFree

## <a name="example"></a>示例


堆栈审核标志文件可以包含任意数量的堆栈遍历每个行，分隔由空格，加号 （+），或在新行中，如下面的示例中所示的标志。

``` syntax
ThreadCreate ProcessCreate
DiskReadInit+DiskWriteInit+DiskFlushInit
CSwitch
```

## <a name="related-topics"></a>相关的主题


[Xperf 选项](xperf-options.md)

 

 








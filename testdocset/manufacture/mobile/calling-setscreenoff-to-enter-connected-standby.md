---
author: kpacquer
Description: "调用 SetScreenOff 输入备用连接"
ms.assetid: b9fddd1f-485b-4b09-9b18-93b994ebc076
MSHAttr: PreferredLib:/library/windows/hardware
title: "调用 SetScreenOff 输入备用连接"
ms.openlocfilehash: b5b6a8a9ed011b731f3e6a99ee9ca0e2f10e777a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="calling-setscreenoff-to-enter-connected-standby"></a>调用 SetScreenOff 输入备用连接


调用**SetScreenOff**函数关闭屏幕和背景光，这将导致手机进入连接备用电源状态。 此低耗电状态很有帮助的测试功耗。

**重要**  
此函数将只能在微软制造操作系统使用。

 

## <a name="span-idsyntaxspanspan-idsyntaxspanspan-idsyntaxspansyntax"></a><span id="Syntax"></span><span id="syntax"></span><span id="SYNTAX"></span>语法


``` syntax
HRESULT SetScreenOff();
```

## <a name="span-idparametersspanspan-idparametersspanspan-idparametersspanparameters"></a><span id="Parameters"></span><span id="parameters"></span><span id="PARAMETERS"></span>参数


无

## <a name="span-idreturnvaluespanspan-idreturnvaluespanspan-idreturnvaluespanreturn-value"></a><span id="Return_Value"></span><span id="return_value"></span><span id="RETURN_VALUE"></span>返回值


HRESULT

## <a name="span-idremarksspanspan-idremarksspanspan-idremarksspanremarks"></a><span id="Remarks"></span><span id="remarks"></span><span id="REMARKS"></span>备注


不是要将设备恢复到全功率状态的等效函数。

## <a name="span-idexamplespanspan-idexamplespanspan-idexamplespanexample"></a><span id="Example"></span><span id="example"></span><span id="EXAMPLE"></span>示例


若要使用 SetScreenOff，包括头和调用不带任何参数。

``` syntax
#include <ManufacturingConnectedStandbyControl.h>
SetScreenOff();
```

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>要求


**标头︰**ManufacturingConnectedStandbyControl.h

**库︰**ManufacturingConnectedStandbyControl.lib

 

 






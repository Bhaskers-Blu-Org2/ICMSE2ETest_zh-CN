---
title: "这是只是一个标记的测试"
description: "这是只是一个标记的测试"
Search.SourceType: 
ms.assetid: 
ms.openlocfilehash: 86c9c37f3a382e9bc9bce3270a172f018ae64811
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="lost-space-between-character-formatting-tags"></a>丢失字符格式设置标记之间的空间

本主题存在只是为了说明一个问题。 在临时服务器上，空白是零之间关闭和打开字符的格式。 例如，这些行之一︰

```
<b>command -option1</b> <i>parameter</i> <b>-option2</b>
**command -option1** *parameter* **-option2**
```

用于呈现零空间之前或之后"参数"的出版物︰

<b>命令的选项 1</b><i>参数</i><b>-组件 2</b>

**命令的选项 1***参数***-组件 2**

HTML 和减价的解决方法是添加**\&nbsp;**之间的标记组成的字符串。 这可能可以正常在大多数命令行中，但这是好些有保留，而不是丢失的空白。 可能出现的非换行空格不是很理想的情况。





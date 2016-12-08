---
title: "文章标题 |服务名称"
description: 
keywords: 
author: GITHUB USERNAME
manager: ALIAS
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: GET ONE FROM guidgenerator.com
ms.openlocfilehash: cabb720ffd42484be0cc23924f460b5ccfc2edd2
ms.sourcegitcommit: e608a62703fcc6bfb1e51713ca9cda10b5be3614
translationtype: MT
---
# <a name="metadata-and-markdown-template"></a>元数据和减价模板

该 docs.ms 模板包含减价语法指南设置元数据的示例。 它位于根目录下的每个全身试验存储库 (例如 ~/Azure-RMSDocs-pr /template.md)，并且应读作减价文件中，虽然您可以参考[的已发布的版本](https://stage.docs.microsoft.com/en-us/rights-management/template)，以查看如何减价示例 rendeer。

当创建减价文件 shluld 模板复制到新文件中时，为组指定下面，上面的文章，标题为 H1 标题填充元数据，并删除的内容。 


## <a name="metadata"></a>元数据 

完全元数据块上面，划分为必填的字段和可选字段;[操作元数据速查表](https://ppe.msdn.microsoft.com/en-us/ce-csi-docs/ops/ops-onboarding/managing-content/content-meta-data)有关更多详细信息，请参阅。 主要的一些注意事项︰

- 您**必须**有一个空格的冒号 （:） 和元数据元素的值之间。
- 如果一个可选的元数据元素不没有值，注释掉的元素加一个 # 号 （都不离开它为空，或者使用"na"）;如果给出的 commnted 的元素添加值，，请务必删除 #。
- 一个值 （例如，标题） 中的冒号将元数据分析器。 在原先的位置使用的 HTML 编码 & #58;(如"标题︰ Azure 权限管理 & #58;基本操作 |Azure RMS")。
- **标题**︰ 此标题将显示在搜索引擎结果。 标题应结束使用管道 (|) 后, 跟该服务的名称 （例如见上面）。 标题不需要 （和可能不会） 是在 H1 标题的标题相同。 它应大致在 65 个字符 (包括 |服务名称）
- **作者**、**经理**、**审阅者**: 作者字段应包含**Github 用户名**的作者，不是他们的别名。  另一方面，"经理"和"审阅者"字段应包含别名。 ms.reviewer 指定的 PM 与文章或服务相关联的名称。
- **ms.assetid**︰ 这是从帽的文章的 GUID。 创建新的减价文件时，从[https://www.guidgenerator.com](https://www.guidgenerator.com)中获取一个 GUID。 
- **ms.prod**、 **ms.service**、 **ms.technology**、 **ms.devlang**、 **ms.topic**、 **ms.tgt_pltfrm**︰ 可能对这些元素的值可以找到[这里](https://microsoft.sharepoint.com/teams/STBCSI/Insights/_layouts/15/WopiFrame.aspx?sourcedoc=%7b7A321BF1-0611-4184-84DA-A0E964C435FA%7d&file=WEDCS_MasterList_CSIValues.xlsx&action=default)。

## <a name="basic-markdown-and-gfm"></a>基本的减价和 GFM

支持所有的基本和 Github flavored 减价。 有关这些方面的详细信息，请参阅︰

- [比较基准减价语法](https://daringfireball.net/projects/markdown/syntax)
- [Github flavored 减价 (GFM) 文档](https://guides.github.com/features/mastering-markdown)

## <a name="headings"></a>标题

第一和第二层标题的例子有上面。 

那里**必须只有一个一级标题，您将显示为页面上标题的主题**。  

第二级标题将生成页面上目录显示在页面上标题下的"在这篇文章"部分中。

### <a name="third-level-heading"></a>第三级标题
#### <a name="fourth-level-heading"></a>第四个二级标题
##### <a name="fifth-level-heading"></a>第五个级别的标题
###### <a name="sixth-level-heading"></a>第六级标题

## <a name="text-styling"></a>文本样式

*斜体* 

**加粗** 

~~删除线~~



## <a name="links"></a>链接

要链接到同一 repo 减价文件，请使用[相对链接](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2)。 

- 示例︰[什么是 Azure 权限管理](./understand-explore/what-is-azure-rms.md)

要链接到同一减价文件中的标题，查看已发布的文章的来源，发现头部的 id (例如`id="blockquote"`，并使用 # + id 链接 (例如`#blockquote`)。

- 例如︰ [Blockquotes](#blockquote)

若要链接到的减价文件中同一 repo 头，使用相对链接 + hashtag 链接。

- 示例︰[在注册过程中的技术概述](./understand-explore/rms-for-individuals-user-sign-up.md#technical-overview-of-the-sign-up-process)

要链接到外部文件，请使用完整的 URL 作为链接。

- [Github](http://www.github.com)的示例︰

如果减价文件中会出现一个 URL，它将转换为可点击的链接。

- 示例︰ http://www.github.com

## <a name="lists"></a>列表

### <a name="ordered-lists"></a>有序列的表

1. 这 
1. 是
1. 一个
1. 有序
1. List  


#### <a name="ordered-list-with-an-embedded-list"></a>订购带有嵌入列表的列表

1. 这里
1. 来自
1. 一个
1. 嵌入的
    1. 思念王兰
    1. 教授李子
1. 有序
1. 列表


### <a name="unordered-lists"></a>未排序的列表

- 这
- ，则它仅检查默认的
- a
- 项目符号列表
- 列表


##### <a name="unordered-list-with-an-embedded-lists"></a>与嵌入列表未排序的列表

- 这 
- 项目符号列表 
- 列表
    - 太太潘金
    - 先生绿色
- contains  
- 其他
    1. Colonel Mustard
    1. 白夫人
- 列表


## <a name="horizontal-rule"></a>水平线规则

---

## <a name="tables"></a>表

| 表        | 正在           | 冷却  |
| ------------- |:-------------:| -----:|
| 是列 3      | 右对齐 | 1600 美元 |
| 是列 2      | 居中对齐      |   12 美元 |
| col 1 是默认值 | 左对齐     |    $ 1 |


## <a name="code"></a>代码

### <a name="codeblock"></a>Codeblock

    function fancyAlert(arg) {
      if(arg) {
        $.docs({div:'#foo'})
      }
    }

### <a name="in-line-code"></a>内嵌代码

这是一种`in-line code`。

## <a name="blockquotes"></a>Blockquotes

> Drought 有一千万多年，现在持续和统治的可怕的蜥蜴有早已结束。 这里在赤道，在其中将一天被称为非洲大陆上存在的斗争已达到 ferocity，新 climax，victor 还没有在视线中。 在 barren 和 desiccated 这片土地，只有小型或 swift 或激烈未能花边，或甚至希望能经受得住。

## <a name="images"></a>图片

### <a name="static-image"></a>静态图像

![这是 alt 文本](./media/AzRMS_elements.png)

### <a name="linked-image"></a>链接的图像

[![链接图像的 alt 文本](./media/AzRMS_elements.png)](https://azure.microsoft.com) 

### <a name="animated-gif"></a>动态的 gif

![动态的 gif](./media/hololens.gif)

## <a name="alerts"></a>通知

### <a name="note"></a>注意

> [!NOTE]
> 这是注释

### <a name="warning"></a>警告

> [!WARNING]
> 这警告

### <a name="tip"></a>提示

> [!TIP]
> 这是提示

### <a name="important"></a>重要说明

> [!IMPORTANT]
> 这非常重要

## <a name="videos"></a>视频

### <a name="channel-9"></a>第 9 频道

<iframe src="http://channel9.msdn.com/Series/Azure-Active-Directory-Videos-Demos/Azure-Active-Directory-Connect-Express-Settings/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>


### <a name="youtube"></a>Youtube

<iframe width="420" height="315" src="https://www.youtube.com/embed/R6_eWWfNB54" frameborder="0" allowfullscreen></iframe>

## <a name="docsms-extentions"></a>docs.ms 扩展

### <a name="button"></a>按钮

> [!div class="button"]
[按钮链接](/rights-management)

### <a name="selector"></a>选择器

> [!div class="op_single_selector"]
- [foo](/rights-management/template.md)
- [栏](/rights-management/scratch.md)

### <a name="step-by-step"></a>分步

>[!div class="step-by-step"]
[Pre](https://www.example.com)
[下一步](https://www.example.com)
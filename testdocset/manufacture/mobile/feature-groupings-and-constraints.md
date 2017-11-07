---
title: "分组功能和约束"
description: "功能组和功能约束允许额外的逻辑添加到生成系统支持 OEMInput 的 XML 的智能处理。"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b2079741-e3a8-44ab-b76f-75b287d0cd66
ms.openlocfilehash: d3f78e455f7a87e93cbc022d9e298e13cf1c47db
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="feature-groupings-and-constraints"></a>分组功能和约束


功能组和功能约束允许额外的逻辑添加到生成系统支持 OEMInput 的 XML 的智能处理。

## <a name="feature-groupings"></a>功能组


分组功能允许可选功能，更好地管理并允许更易于管理的产品包的组织结构。 分组功能用于实现功能约束由 Microsoft 和 OEM （可选）。

## <a name="feature-constraints"></a>功能约束


可以指定功能约束，以避免不合逻辑或不适当的生成配置。

某些设置是互相排斥的只有一种设置应指定一次。 例如，请考虑功能，发布\_生产和发行\_测试。 这些功能是互相排斥的。 这意味着，如果发行\_测试集，版本\_不能设置生产。

在 Microsoft 和 OEM 的功能级别分为约束。 Oem 不能替代 Microsoft 约束。 支持下列约束︰

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>元素</th>
<th>说明</th>
<th>至少一个功能是必需的</th>
<th>是互相排斥的功能</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>OneOrMore</p></td>
<td><p>必须指定一个或多个功能。</p></td>
<td><p>true</p></td>
<td><p>false</p></td>
</tr>
<tr class="even">
<td><p>ZeroOrOne</p></td>
<td><p>可以指定一个功能或没有的功能。</p></td>
<td><p>false</p></td>
<td><p>true</p></td>
</tr>
<tr class="odd">
<td><p>OneAndOnlyOne</p></td>
<td><p>一项功能是必需的可以指定只有一个功能。</p></td>
<td><p>true</p></td>
<td><p>true</p></td>
</tr>
<tr class="even">
<td><p>ZeroOrMore</p></td>
<td><p>这是默认值，该值指示没有任何约束。 此选项仅用于组功能发布目的并在图像处理过程中将被忽略。</p></td>
<td><p>false</p></td>
<td><p>false</p></td>
</tr>
</tbody>
</table>

 

以下 XML 示例阐释了使用约束来适当地 restrain 假调制解调器功能。

``` syntax
<Features>
  <Microsoft>
    <FeatureGroup Constraint="OneAndOnlyOne">
           <FeatureIDs>
           <FeatureID>MS_IMGFAKEMODEM</FeatureID>
           <FeatureID>MS_IMGNOFAKEMODEM</FeatureID> 
          </FeatureIDs>
    </FeatureGroups >
  </Microsoft>
</Features>
```

在此示例中的约束指定必须选择 IMGFAKEMODEM 或 IMGNOFAKEMODEM。 不能同时设置两个值。 一次，必须设置一个且只有一个值。 因为假调制解调器测试功能必须启用或禁用此约束是必需的。

以下 XML 示例阐释了使用约束来适当地 restrain 生产生成设置。 此示例演示如何多个约束条件可以与单个功能相关联。

``` syntax
<Features>
  <Microsoft>
    <FeatureGroups>
        <FeatureGroup Constraint="ZeroOrOne">
         <FeatureIDs>
          <FeatureID>RELEASE_PRODUCTION</FeatureID> 
          <FeatureID>MS_CODEINTEGRITY_PROD</FeatureID> 
        </FeatureIDs>
    </FeatureGroup>
         <FeatureGroup Constraint="ZeroOrOne">
           <FeatureIDs>
            <FeatureID>RELEASE_PRODUCTION</FeatureID>
            <FeatureID>MS_DISABLETESTSIGNING</FeatureID> 
         </FeatureIDs>
    </FeatureGroup>
  </Microsoft>
</Features>
```

当&lt;ReleaseType&gt;生产&lt;/ReleaseType&gt; OEMInput 文件，发布到此映射中设置\_生产。 有关发布类型的详细信息，请参阅[OEMInput 文件的内容](oeminput-file-contents.md)。

在此示例中的约束指定的︰

-   任何一个发行版\_生产或 MS\_CODEINTEGRITY\_生产可以选择，但它们均未选择在同一时间。 这是因为自动启用生产代码完整性时释放\_生产处于选中状态，因此不能手动启用。

-   任何一个发行版\_生产或 MS\_DISABLETESTSIGNING 可以选择，但它们均未选择在同一时间。 这是因为自动禁用测试签名时释放\_生产处于选中状态，因此不能手动禁用。

生成选项更复杂，在下面的 XML 表示。

``` syntax
FeatureGroup Constraint="OneAndOnlyOne">
  <FeatureIDs>
    <FeatureID>RELEASE_PRODUCTION</FeatureID> 
      <FeatureID>MS_TEST</FeatureID> 
      <FeatureID>MS_HEALTH</FeatureID> 
      <FeatureID>MS_PRODUCTION</FeatureID> 
      <FeatureID>MS_SELFHOST</FeatureID> 
    </FeatureIDs>
  </FeatureGroup>
<FeatureGroup Constraint="OneAndOnlyOne">
  <FeatureIDs>
    <FeatureID>RELEASE_PRODUCTION</FeatureID> 
    <FeatureID>MS_PRODUCTION_CORE</FeatureID> 
    <FeatureID>MS_TEST</FeatureID> 
  </FeatureIDs>
</FeatureGroup>
```

这些示例中的设置指定生产\_核心是互斥发行版\_生产和测试，但它不能与健康、 生产或 SELFHOST 互相排斥。

有关生成功能的其他信息，请参阅[构建映像的可选功能](optional-features-for-building-images.md)。

## <a name="implicit-feature-ids"></a>隐式功能 Id


隐式功能 Id 生成基于 XML 输入用来定义中的功能清单文件的功能。 功能约束必须使用隐式功能 Id。 本节提供 XML 输入的值和生成隐式特征 Id 之间的映射。

**预定义的版本类型隐式功能 Id**

有两个可用于功能约束的预定义隐式功能 Id。

-   版本\_测试

-   版本\_生产

发布类型的详细信息，请参阅[构建映像的可选功能](optional-features-for-building-images.md)。

**OEM 和 Microsoft 隐式功能 Id**

对于每个 OEM 和 Microsoft 功能，系统会自动创建隐式功能 Id。 这是我预先追加任何一个*MS\_ * microsoft 或*OEM\_*为 OEM 定义的功能。

如果 OEM 创建名为 TEST 的功能，例如\_FEATURE1 使用如下所示的 XML、 隐式功能 ID 将*OEM\_测试\_FEATURE1*。

``` syntax
<Features>
    <OEM>
     <PackageFile Path="%oempackageroot%\test\" 
      Name="Contoso.Test.MinTE.spkg">
        <FeatureIDs>
          <FeatureID>TEST_FEATURE1</FeatureID>
        </FeatureIDs>
      </PackageFile>
   </OEM>
</Features>
```

若要创建一个功能约束来确保该测试功能仅随测试版本类型，请使用下面的 XML。

``` syntax
<FeatureGroup Constraint="ZeroOrOne">
   <FeatureIDs>
      <FeatureID>RELEASE_PRODUCTION</FeatureID>
      <FeatureID>OEM_TEST_FEATURE1</FeatureID> 
   </FeatureIDs>
</FeatureGroup>
```

**SOC 隐式功能 Id**

SOC 功能是预附加与 SOC\_。 如果功能中指定*DCD6000* ，则示例清单 XML，就是隐式功能 ID *SOC\_DCD6000*。

**SV 隐式功能 Id**

SV 功能都与 SV 预附加\_。 示例如果*CONTOSO*指定在功能清单 XML，就是隐式功能 ID *SV\_CONTOSO*。

**设备隐式功能 Id**

设备功能是预附加设备\_。 示例如果在功能指定*测试*清单 XML，就是隐式功能 ID*设备\_测试版*。

有关使用 SOC、 SV 和设备属性的详细信息，请参阅[功能清单文件的内容](feature-manifest-file-contents.md)。

## <a name="related-topics"></a>相关的主题


[为构建映像的可选功能](optional-features-for-building-images.md)

 

 

[发送有关此主题的意见的评论](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Feature%20groupings%20and%20constraints%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "发送有关此主题的意见的评论")






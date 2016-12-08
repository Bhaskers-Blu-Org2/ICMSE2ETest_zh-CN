---
author: kpacquer
Description: "测试更新"
ms.assetid: cdeecf1c-a239-4d7a-87b8-a366e8e26f06
MSHAttr: PreferredLib:/library/windows/hardware
title: "测试更新"
ms.openlocfilehash: c5fb1b50fa97cd9a196a21044305a1cce6404945
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="test-an-update"></a>测试更新


正在开发的第一个图像时，应该开始更新测试。  测试您的驱动程序，预加载应用程序及其他内容可以在整个过程中进行更新。

当您正在构建测试映像的阶段，应进行本地测试的更新、 运行兼容性测试之前和之后的更新，并查找相同的结果。  这是时间，您可以更轻松地测试自动化的电话功能全面及早发现更新的问题。  不要等到直到即将制造和零售设备测试。

通过空中传输 (OTA) 更新仅可在零售设备上，这是更加困难，因为在零售设备上更高的安全性测试。  因此，是重要的您执行深入功能测试在测试图像上，并在零售电话确保 OTA 更新成功完成按照更新部分网络测试中的指导将测试重点放。

Oem 必须确保通过全面测试之前将其提交到 Microsoft 更新的 OEM 更新质量。 至少，OEM 必须执行以下操作。

-   验证软件包更新测试零售映像时不会包含任何测试证书。

-   验证固件版本号已正确更改，可以通过导航到**设置** &gt; **系统** &gt; **有关**设备上。 有关版本控制信息的详细信息，请参阅[更新的要求](update-requirements.md)。

-   验证 OEM 更新程序包工作正常。

-   测试更新了用户数据，以确保其数据被保留的设备上。 以下是一些示例的测试，您可以确保用户数据在更新后没有被修改。

    -   所有用户设置都都相同。

    -   启动屏幕拼块具有相同的位置和大小。

    -   用户数据仍处于设备 （图片、 应用程序、 SMS 历史、 音乐文件、 视频文件等）

## <a name="span-idlocaltestingofupdatesspanspan-idlocaltestingofupdatesspanspan-idlocaltestingofupdatesspanlocal-testing-of-updates"></a><span id="Local_testing_of_updates"></span><span id="local_testing_of_updates"></span><span id="LOCAL_TESTING_OF_UPDATES"></span>本地测试的更新


提交更新之前，请本地对其进行测试。 在测试过程中将使用的 PC，请执行以下步骤︰

1.  将更新后的测试包部署到设备。 您可以收到来自已经被批准的使用[Get SignedFirmwareSubmission cmdlet](get-signedfirmwaresubmission-cmdlet.md)来测试更新的更新程序包。

2.  验证已成功更新并具有对设备的行为没有意外效果。

## <a name="span-idnetworktestingofupdatesspanspan-idnetworktestingofupdatesspanspan-idnetworktestingofupdatesspannetwork-testing-of-updates"></a><span id="Network_testing_of_updates"></span><span id="network_testing_of_updates"></span><span id="NETWORK_TESTING_OF_UPDATES"></span>网络测试的更新


若要准备接收来自 Microsoft 测试更新服务器上的更新，请完成以下步骤。

1.  获取测试更新资源调配从 Microsoft 程序包后已经注册，可提交的固件和更新提交的请求。

2.  通过使用 IUTool.exe 适用于设备的供应包。

3.  与设备建立连接到蜂窝或 Wi-fi 网络，并将设备连接到充电器。

    **请注意**  
    我们建议使用 Wi-fi 下载更新程序，以便您不要运行任何约束到移动运营商与测试时。 在使用其蜂窝数据连接时，移动运营商可以指定更新的下载大小限制。

     

4.  启动更新过程，通过**设置** &gt; **更新和恢复** &gt; **电话更新**。

5.  当出现更新时，请按照提示和完成更新过程。

6.  验证已成功更新并具有对设备的行为没有意外效果。

## <a name="span-idtestcasesforfeaturesafteranupdatespanspan-idtestcasesforfeaturesafteranupdatespanspan-idtestcasesforfeaturesafteranupdatespantest-cases-for-features-after-an-update"></a><span id="Test_cases_for_features_after_an_update"></span><span id="test_cases_for_features_after_an_update"></span><span id="TEST_CASES_FOR_FEATURES_AFTER_AN_UPDATE"></span>更新后的功能的测试用例


### <a name="wi-fi"></a>Wi-Fi

先决条件︰ 无

测试步骤︰

<ol>
<li><p>在应用程序列表中，点击<strong>设置</strong> &gt; <strong>网络&amp;无线</strong> &gt; <strong>Wi-fi</strong>。</p></li>
<li><p>选择受保护的无线网络。 使用适当的凭据登录。</p></li>
<li><p>确认网络的状态显示为"已连接"。</p></li>
<li><p>验证设备的顶部的<strong>Wi-Fi</strong>图标此时将显示。</p>
<div class="alert">
<strong>请注意</strong>  
<p>图标应该闪存设备连接时，连接电话后保持稳定。 几秒钟后该设备连接，该图标可能会消失。 可以通过点击屏幕顶部的中间再次显示的图标。</p>
</div>
<div>
 
</div></li>
<li><p>点击<strong>开始</strong>，然后点击<strong>Internet Explorer</strong>。</p>
<div class="alert">
<strong>请注意</strong>  
<p>当第一次启动浏览器时，会弹出一个对话框询问"使用推荐的设置吗？" 点击<strong>推荐</strong>按钮。</p>
</div>
<div>
 
</div></li>
<li><p>点击地址栏，输入网站的 URL。 点击转到站点虚拟键盘上的 enter 键。</p></li>
<li><p>验证加载页面。</p></li>
<li><p>点击<strong>开始</strong>以返回到开始屏幕，然后在应用程序列表中，点击<strong>设置</strong> &gt;<strong>网络&amp;无线</strong> &gt; <strong>Wi-fi</strong>。</p></li>
<li><p>选择并连接到不安全的无线网络。</p></li>
<li><p>请按<strong>开始</strong>以返回到开始屏幕，然后点击<strong>Internet Explorer</strong>。</p></li>
<li><p>点击地址栏，输入一个不同的网站的 URL。</p></li>
<li><p>验证正确加载该页面。</p></li>
<li><p>点击<strong>开始</strong>以返回到开始屏幕上，并在应用程序列表中，点击<strong>设置</strong> &gt;<strong>网络&amp;无线</strong> &gt; <strong>Wi-Fi</strong> &gt; <strong>管理</strong>。</p></li>
<li><p>验证两个网络名称存在已知的网络列表中。</p></li>
<li><p>点击并按住<strong>开放网络</strong>。</p></li>
<li><p>点击<strong>删除</strong>。</p></li>
<li><p>请验证该设备连接到安全网络自动从第 2 步。</p></li>
</ol>

### <a name="maps"></a>映射

先决条件︰ 无

测试步骤︰

<ol>
<li><p>在应用程序列表中，点击<strong>地图</strong>。</p></li>
<li><p>验证位置提示出现时第一次启动时映射。</p></li>
<li><p>点击<strong>允许</strong>启用位置感知。 该应用程序将加载当前所在的位置。</p></li>
<li><p>当完全加载映射时，请验证以下各项。</p>
<ol>
<li><p>放大图，以便在本地区的道路都可见。</p></li>
<li><p><strong>我</strong>图标 （菱形或圈形） 位于电话的位置。</p></li>
<li><p><strong>我</strong>图标的中心圆应匹配电话主题的颜色。</p></li>
</ol></li>
<li><p>请验证映射应用程序栏将显示与以下四个按钮的底部。</p>
<ol>
<li><p><strong>侦察</strong>（按钮是建筑物的行）。</p></li>
<li><p><strong>说明</strong>（按钮是一个箭头）。</p></li>
<li><p><strong>我</strong>（按钮是圆圈圆）。</p></li>
<li><p><strong>搜索</strong>（按钮是一个放大镜）。</p></li>
</ol>
<div class="alert">
<strong>请注意</strong>  
<p>对于某些图像，侦察不是可用的。</p>
</div>
<div>
 
</div></li>
<li><p>平移离设备位置的映射，然后点击详细<strong></strong>按钮上。 验证映射返回电话中心<strong>我</strong>图标位置。</p></li>
<li><p>点击<strong>侦察</strong>按钮。 验证本地侦察在几秒钟内加载并显示<strong>吃 + 饮用</strong>数据透视表，其中列出的提供食物和饮料的企业。</p>
<ol>
<li><p>验证在<strong>吃 + 饮用</strong>数据透视表中显示每个项包含公司名称和地址。</p></li>
<li><p>请验证侦察，加载两个其他数据透视表<strong>请参见 + 不要</strong>进行<strong>网上购物</strong>。</p></li>
</ol></li>
<li><p>返回映射应用程序，然后点击<strong>方向</strong>按钮。</p>
<ol>
<li><p>离开开始字段默认设置为"我的位置。"</p></li>
<li><p>点击结束字段，然后输入一个结束点 （西雅图）。 查看行车方案虚拟键盘上按 enter 键。</p></li>
<li><p>验证的分步指导都具有映射的带区顶部的列表窗体中显示。</p></li>
<li><p>起点处，地图应显示一个"A"。</p></li>
<li><p>滚动方向。 请验证映射更新以显示每个新的方向。</p></li>
<li><p>滚动到末尾。 验证映射显示在终点处"B"。</p></li>
</ol></li>
<li><p>返回映射应用程序。 点击<strong>搜索</strong>按钮。</p>
<ol>
<li><p>输入搜索条件，"在北京的餐馆"。 点击要执行搜索的虚拟键盘上的 enter 键。</p></li>
<li><p>验证最多 10 个搜索结果显示，在地图上的针脚为第一针展开的以便您可以查看其名称。 （该名称可能会被截掉右边缘）。</p></li>
</ol></li>
</ol>

### <a name="lock-screen-testing"></a>锁定屏幕测试

先决条件︰ 无

测试步骤︰

<ol>
<li><p>在应用程序列表中，点击&gt;<strong>设置</strong> &gt;<strong>个性化设置</strong> &gt; <strong>锁定屏幕</strong>。</p></li>
<li><p>将"屏幕超时之后"字段设置为"30 秒"。</p></li>
<li><p>保持 30 秒闲置设备。 屏幕转到睡眠、 按下和刷屏幕验证没有任何反应后, 该设备已被锁定。</p></li>
<li><p>按下电源按钮以将设备解锁。 刷上解除锁定屏幕。</p></li>
<li><p>请验证该设备成功解锁。</p></li>
<li><p>在锁定屏幕上，请打开密码为"打开"。</p></li>
<li><p>创建一个密码。</p></li>
<li><p>保持 30 秒电话空闲。 屏幕进入睡眠状态后，按下和刷屏幕验证，将不会发生情况和设备已被锁定。</p></li>
<li><p>按下电源按钮以将设备解锁。 刷上解除锁定屏幕。 验证出现输入密码的提示。</p></li>
<li><p>输入了错误的密码。 请验证不会解锁设备，必须输入正确的密码。</p></li>
<li><p>请输入正确的密码。 请验证该设备成功解除。</p></li>
</ol>

### <a name="capturing-photos-with-the-camera"></a>用相机捕捉的照片

先决条件︰ 无

测试步骤︰

<ol>
<li><p>锁定设备并使其保持为空闲状态，使其进入睡眠模式。</p></li>
<li><p>按下并保持相机硬件键以启动摄像头。 然后，验证摄像机启动默认摄像头应用程序或摄像头应用程序。 点击<strong>取消</strong>以&quot;允许相机以使用您的位置&quot;屏幕。</p>
<div class="alert">
<strong>请注意</strong>  
<p>如果手机没有摄像头硬件按钮，直接启动摄像头应用程序。</p>
</div>
<div>
 
</div>
<div class="alert">
<strong>请注意</strong>  
<p>"允许...位置"提示符会记住以前的设置，如果最近使用过的相机不会显示。</p>
</div>
<div>
 
</div></li>
<li><p>验证默认设置的照相机是为&quot;图片&quot;模式。</p></li>
<li><p>In 和 out 用摄像机屏幕上手指捏紧并验证摄像机屏幕和缩小缩放。</p></li>
<li><p>如果您的设备有照相机硬件键，按和保持它一半并验证矩形框将显示在屏幕上的自动对焦功能。 同时，验证完成照相机焦点时，可以听到蜂鸣音。</p></li>
<li><p>在屏幕上点击或按硬件相机按钮并验证蜂鸣音听到后拍照。</p></li>
<li><p>刷有待检查只是拍摄的图片，并检查有以下。</p>
<ol>
<li><p>错误的颜色。</p></li>
<li><p>灰尘在相机窗口下。 照片中较暗的区域时，您会发现这样。</p></li>
<li><p>模糊图像</p></li>
<li><p>过亮或暗图像。 由此可见，有问题的相机传感器。</p></li>
</ol></li>
</ol>

### <a name="recording-videos-with-the-camera"></a>摄像头录制视频

先决条件︰ 无

测试步骤︰

<ol>
<li><p>锁定设备并使其保持为空闲状态，使其进入睡眠模式。</p></li>
<li><p>按下并保持相机硬件密钥来启动摄像头或启动该应用程序直接从应用程序列表。 点击<strong>取消</strong>以&quot;允许相机以使用您的位置&quot;屏幕。</p>
<div class="alert">
<strong>请注意</strong>  
<p>如果设备没有相机硬件按钮，直接启动摄像头应用程序。</p>
</div>
<div>
 
</div>
<div class="alert">
<strong>请注意</strong>  
<p>"允许...位置"提示符会记住以前的设置，如果最近使用过的相机不会显示。</p>
</div>
<div>
 
</div></li>
<li><p>更改为视频捕捉模式。</p></li>
<li><p>In 和 out 捏使用手指在屏幕上并验证摄像机屏幕和缩小缩放。</p></li>
<li><p>如果设备有照相机硬件按钮，按下它开始录制视频。</p></li>
<li><p>验证有蜂鸣报警和录制开始的计数器。</p></li>
<li><p>如果该设备有照相机硬件按钮，它再次以停止录制视频后按 15 秒。</p></li>
<li><p>左摄像机屏幕上的刷卡并按上捕获的视频的<strong>播放</strong>。</p></li>
<li><p>验证视频正确捕获和播放 15 秒钟。</p></li>
</ol>

### <a name="front-facing-camera"></a>前面向照相机

先决条件︰ 无

测试步骤︰

<ol>
<li><p>锁定设备并使其保持为空闲状态，将手机放入睡眠模式。</p></li>
<li><p>按下并保持相机硬件键以启动摄像头。 点击<strong>取消</strong>以&quot;允许相机以使用您的位置&quot;屏幕。</p>
<div class="alert">
<strong>请注意</strong>  
<p>如果设备没有相机硬件按钮，直接启动摄像头应用程序。</p>
</div>
<div>
 
</div>
<div class="alert">
<strong>请注意</strong>  
<p>"允许...位置"提示符会记住以前的设置，如果最近使用过的相机不会显示。</p>
</div>
<div>
 
</div></li>
<li><p>验证︰ 默认情况下应该将相机设置为&quot;图片&quot;模式面向背面的摄像头。</p></li>
<li><p>在应用程序栏中，点击<strong>正面</strong>图标</p></li>
<li><p>验证正面<strong>摄像头</strong>图标现在被突出显示。</p></li>
<li><p>In 和 out 用摄像机屏幕上手指捏紧并验证摄像机屏幕和缩小缩放。</p></li>
<li><p>一直向下按相机硬件键或点击屏幕拍摄一张照片，如果设备没有硬件按钮。</p></li>
<li><p>验证采取了图片之后，听到蜂鸣音。</p></li>
<li><p>刷有待检查只是拍摄的图片，并检查有以下。</p>
<ol>
<li><p>错误的颜色。</p></li>
<li><p>灰尘在相机窗口下。 照片中较暗的区域时，您会发现这样。</p></li>
<li><p>模糊图像。</p></li>
<li><p>过亮或暗图像。 由此可见，有问题的相机传感器。</p></li>
</ol></li>
</ol>

### <a name="calling-with-a-bluetooth-device"></a>调用时使用 Bluetooth 设备

先决条件： 

<ul>
<li><p>Bluetooth 设备连接至测试设备</p></li>
<li><p>第二个电话呼叫功能测试。</p></li>
</ul>

测试步骤︰

<ol>
<li><p>在应用程序列表中，点击<strong>设置</strong> &gt; <strong>设备</strong> &gt; <strong>Bluetooth</strong>、 上启用 Bluetooth。</p></li>
<li><p>连接/对测试设备的 Bluetooth 设备</p></li>
<li><p>调用测试设备</p></li>
<li><p>验证呼叫测试设备上，会出现屏幕上注意到。</p></li>
<li><p>验证，可以通过使用测试设备连接 Bluetooth 设备听到电话铃声</p></li>
<li><p>使用连接的 Bluetooth 设备测试设备呼叫应答。</p></li>
<li><p>验证可以通过 Bluetooth 设备测试设备上听到来自第二个设备的音频。</p></li>
<li><p>验证音频通过 Bluetooth 设备的测试设备可以发出声音的第二个设备。</p></li>
<li><p>结束呼叫使用 Bluetooth 设备。</p></li>
</ol>

### <a name="bluetooth-and-nfc-tapsend"></a>Bluetooth 和 NFC （点击 + 发送）

先决条件： 

<ul>
<li><p>必须启用 Bluetooth。</p></li>
<li><p>若要验证点击 + 发送功能的第二个电话。</p></li>
</ul>

测试步骤︰

<ol>
<li><p>转到<strong>照片</strong> &gt; <strong>唱片集</strong>，然后选择一张照片。</p></li>
<li><p>选择图片的选项。</p></li>
<li><p>共享通过 NFC/点击 + 发送照片。</p></li>
<li><p>用于传输一个弹出屏幕将出现在第二个设备。 点击<strong>接受</strong>并等待传输完成后。</p></li>
<li><p>转到<strong>照片</strong> &gt; <strong>专辑</strong> &gt; <strong>保存图片</strong>。</p></li>
<li><p>验证传输的照片出现在相册中。</p></li>
</ol>

### <a name="proximity-sensor"></a>近程传感器

先决条件︰ 无

测试步骤︰

<ol>
<li><p>在启动屏幕上，点击<strong>电话</strong>。</p></li>
<li><p>先打电话给第二个设备</p></li>
<li><p>将手指放在耳机区域。 验证显示器将关闭。</p></li>
<li><p>断开呼叫。</p></li>
</ol>

### <a name="video-streaming"></a>视频流

先决条件： 

<ul>
<li><p>该设备必须连接到 Wi-fi 或要使用的 web 浏览器连接到 internet。</p></li>
<li><p>要打电话的第二个设备。</p></li>
<li><p>Bluetooth 设备。</p></li>
</ul>

测试步骤︰

<ol>
<li><p>在启动屏幕上，点击<strong>Internet Explorer</strong>。</p>
<div class="alert">
<strong>请注意</strong>  
<p>当第一次启动浏览器时，会弹出一个对话框询问到&quot;使用推荐的设置？&quot; 点击<strong>推荐</strong>按钮。</p>
</div>
<div>
 
</div></li>
<li><p>点击地址栏，转到支持视频的网站。</p></li>
<li><p>从网站中选择视频，然后点击<strong>播放</strong>。</p></li>
<li><p>验证视频启动缓冲，并最终开始播放。 根据网络连接的速率，它可能需要 15-20 秒的视频开始播放。</p></li>
<li><p>点击视频屏幕上的<strong>暂停</strong>按钮。</p></li>
<li><p>验证视频暂停。</p></li>
<li><p>点击视频屏幕上的<strong>播放</strong>按钮。</p></li>
<li><p>验证视频恢复起未出现任何问题。</p></li>
<li><p>验证传入呼叫的警报音 Bluetooth 通过音频停止播放。</p></li>
<li><p>接收传入呼叫按 Bluetooth 按钮，并验证在调用连接。</p></li>
<li><p>断开到 Bluetooth 呼叫并点击视频屏幕上的<strong>播放</strong>按钮。</p></li>
<li><p>验证视频开始播放，音频路由通过 Bluetooth 设备。</p></li>
<li><p>从第二个设备的测试设备发送文本消息。</p></li>
<li><p>请验证接收手机上的文字通知和在传入消息 Bluetooth 音频通知的。 请点击<strong>忽略</strong>忽略该文本消息。</p>
<div class="alert">
<strong>请注意</strong>  
<p>对于某些地区，不支持语音，并在设备上显示一条消息。 点击<strong>关闭</strong>，然后进行测试。</p>
</div>
<div>
 
</div></li>
<li><p>点击视频屏幕上的<strong>播放</strong>按钮。</p></li>
<li><p>在视频开始播放未出现任何问题和音频都经过 Bluetooth 验证。</p></li>
</ol>

### <a name="audio-streaming"></a>音频流

先决条件： 

<ul>
<li><p>第二个设备呼叫支持。</p></li>
<li><p>A2DP Bluetooth 设备。</p></li>
<li><p>Desi 音乐下载应用程序。</p></li>
</ul>

测试步骤︰

<ol>
<li><p>使用您的 Microsoft 帐户登录。</p></li>
<li><p>在应用程序列表中，点击<strong>设置</strong> &gt; <strong>设备</strong> &gt; <strong>Bluetooth</strong>。 启用 Bluetooth。</p></li>
<li><p>在 paring 模式下放置 A2DP Bluetooth 设备。 它将列在该设备上的搜索结果，请点击它。 验证的 Bluetooth 设备的状态显示为"已连接的声音音乐"。</p></li>
<li><p>按硬件后退<strong>按钮</strong>以返回到应用程序列表。 点击"Desi 音乐"应用程序。</p></li>
<li><p><strong>新建</strong>数据透视表中，并点击相册到左刷。</p></li>
<li><p>点击专辑的曲目之一。</p></li>
<li><p>跟踪启动缓冲，并最终开始播放 Bluetooth 通过验证。 根据网络连接的速率，时间可能长达 15-20 秒的音频开始播放。</p></li>
<li><p>从第二个设备，请调用测试设备。</p></li>
<li><p>验证传入呼叫的警报音 Bluetooth 通过音频暂停。</p></li>
<li><p>接收传入呼叫使用 Bluetooth 按钮。</p></li>
<li><p>验证呼叫连接。</p></li>
<li><p>通过 Bluetooth 设备上断开呼叫连接。</p></li>
<li><p>请验证轨道自动恢复。</p></li>
<li><p>从第二个设备的测试设备发送文本消息。</p></li>
<li><p>验证设备上显示的文本通知，并且音频通告接收传入消息 Bluetooth 设备上。</p></li>
<li><p>点击文本通知和发送响应。</p></li>
<li><p>验证音频继续播放未出现任何问题。</p></li>
<li><p>两次点击 Bluetooth<strong>后退</strong>按钮。</p></li>
<li><p>按 Bluetooth<strong>前进</strong>按钮。</p></li>
<li><p>确认下一曲目开始播放。</p></li>
<li><p>按 Bluetooth<strong>快退</strong>按钮。</p></li>
<li><p>确认上一曲目开始播放。</p></li>
<li><p>按 Bluetooth<strong>暂停</strong>按钮。</p></li>
<li><p>请验证轨道会暂停。</p></li>
<li><p>再次按下 Bluetooth<strong>暂停</strong>按钮。</p></li>
<li><p>请验证轨道继续播放。</p></li>
</ol>

### <a name="smsmms-messaging"></a>SMS/MMS 消息

先决条件： 

<ul>
<li><p>两个额外设备可供测试的消息传递服务。</p></li>
<li><p>在设备上有照片和视频</p></li>
</ul>

测试步骤︰

<ol>
<li><p>在启动屏幕上，点击<strong>消息</strong>，，然后点击<strong>新建</strong>。</p></li>
<li><p>创建新的文本消息。</p></li>
<li><p>验证带有空地址栏打开的聊天卡片，回复框。</p></li>
<li><p>在"收件人"字段中键入第二个设备的电话号码。</p></li>
<li><p>键入简短的文本&quot;Hello&quot;到答复中并发送该邮件。</p></li>
<li><p>验证在聊天卡显示已发送的邮件。</p></li>
<li><p>验证第二个设备成功接收消息。</p></li>
<li><p>在聊天上，点击<strong>附件</strong>按钮并选择要附加图片。</p></li>
<li><p>从相机辊中选择图片，然后发送消息。</p></li>
<li><p>验证第二个设备成功接收的图片。</p></li>
<li><p>回复发带有图片附件的第二个设备。</p></li>
<li><p>验证测试设备接收图片消息。</p></li>
<li><p>从测试设备与视频附件进行答复。</p></li>
<li><p>验证第二个设备接收并可以播放视频。</p></li>
<li><p>回复发视频附件的第二个设备。</p></li>
<li><p>验证测试设备接收视频，并可播放。</p></li>
<li><p>在测试设备上，请按硬件后退按钮，创建另一个短消息。</p></li>
<li><p>验证聊天卡打开并且具有空地址栏，回复框。</p></li>
<li><p>键入一个电话号码，然后输入一个分号，并在"收件人"字段中键入联系人的电话号码。</p></li>
<li><p>在答复框中键入具有超过 320 个字符的邮件，点击<strong>发送</strong>。</p></li>
<li><p>验证字符计数器出现前或何时达到字符限制。</p></li>
<li><p>验证在聊天卡片显示已发送的邮件。</p></li>
<li><p>验证多部分的 SMS 消息成功接收的第二个和第三个设备</p></li>
<li><p>对测试设备从第二个或第三个设备发送 SMS 回复消息。</p></li>
<li><p>验证测试设备上的音频通知可以听到有关收到的短信。</p></li>
<li><p>验证在聊天卡片作为最新的消息显示答复。</p></li>
</ol>

### <a name="fm-radio"></a>调频广播

先决条件： 

<ul>
<li><p>一套耳机作为调频收音机的天线。</p></li>
<li><p>呼叫支持第二个设备。</p></li>
</ul>

测试步骤︰

<ol>
<li><p>插上一副耳机。</p></li>
<li><p>在应用程序列表中，点击<strong>调频收音机</strong>。</p>
<div class="alert">
<strong>请注意</strong>  
<p>如果请求，允许对位置服务的调频广播访问。</p>
</div>
<div>
 
</div></li>
<li><p>按<strong>向前</strong>或向<strong>后</strong>按钮翻阅站。 该调谐器通过扫描工作站进行适当的验证。</p></li>
<li><p>点击<strong>暂停</strong>按钮，并验证无线电会暂停。 点击<strong>播放</strong>，然后验证无线电播放恢复。</p></li>
<li><p>从第二个设备，请调用测试设备。</p></li>
<li><p>验证传入呼叫的警报音 Bluetooth 通过音频停止播放。</p></li>
<li><p>接收传入呼叫按 Bluetooth 按钮，并验证呼叫连接。</p></li>
<li><p>断开到 Bluetooth 呼叫并验证无线电自动恢复。</p></li>
<li><p>按<strong>添加到收藏夹</strong>按钮将当前工作站保存到收藏夹中。</p></li>
<li><p>通过刷屏幕滚动站和确认调谐器能够领取各种站。</p></li>
<li><p>请按<strong>开始</strong>以返回到启动屏幕。 验证单选继续播放。</p></li>
<li><p>在应用程序列表中，点击<strong>设置</strong> &gt; <strong>设备</strong> &gt; <strong>Bluetooth</strong>。 关闭 Bluetooth。</p></li>
<li><p>按硬件后退按钮。 打开飞机模式，然后验证无线电停止播放。 关闭飞机模式。</p></li>
<li><p>在应用程序列表中，点击<strong>调频收音机</strong>。</p></li>
<li><p>点击<strong>收藏</strong>。 验证以前添加的喜爱站出现，然后选择该电台以及无线电，调整到该收藏电台。</p></li>
<li><p>请点击<strong>...</strong>在右下角。 请点击<strong>切换到扬声器</strong>音频源自扬声器的验证。</p></li>
<li><p>从第二个设备，请调用测试设备。</p></li>
<li><p>验证传入呼叫的警报可以听到音频停止播放。</p></li>
<li><p>接收传入呼叫并验证呼叫连接。</p></li>
<li><p>断开呼叫连接，并验证无线电自动恢复。</p></li>
</ol>

### <a name="rebooting-the-device"></a>重新启动设备

先决条件︰ 无

测试步骤︰

<ol>
<li><p>按下并保持设备上的电源按钮</p></li>
<li><p>验证&quot;关闭电源中下滑&quot;屏幕显示和向下刷屏幕。</p></li>
<li><p>请验证该设备处于关闭状态。</p></li>
<li><p>按住电源按钮再次。</p></li>
<li><p>请验证该设备引导至主操作系统屏幕成功不崩溃的情况下。</p></li>
<li><p>重复步骤 1-5。</p></li>
</ol>

### <a name="messagingfamily-room"></a>消息/客厅

先决条件： 

<ul>
<li><p>两个其他 Microsoft 帐户。</p></li>
<li><p>其他两个设备。</p></li>
</ul>

测试步骤︰

<ol>
<li><p>测试设备的联系人列表中添加第二个和第三个设备的数字。</p></li>
<li><p>在应用程序列表中，点击<strong>人员</strong>和刷留给<strong>一起</strong>透视。</p></li>
<li><p>点击<strong>添加 （+）</strong>按钮并从&quot;新增&quot;屏幕上，点击<strong>文件室</strong>。</p></li>
<li><p>验证&quot;您的名称空间&quot;显示在屏幕上输入友好名称的文件室。 然后，点击<strong>保存</strong>。</p></li>
<li><p>从&quot;编辑室&quot;屏幕，点击<strong>邀请</strong>按钮从应用程序栏中添加步骤 1 中创建的联系人。</p></li>
<li><p>接受来自另一台设备的邀请</p></li>
<li><p>验证在成员屏幕中列出了您创建的所有联系人。</p></li>
<li><p>刷卡左到<strong>聊天</strong>数据透视表并在消息框中输入一些文本。</p></li>
<li><p>验证所有组成员都接收您发送的文本的。</p></li>
<li><p>从第二个设备响应开机自检并验证 （包括测试设备） 的所有组成员都接收的邮件。</p></li>
<li><p>从测试设备中，点击硬件后退按钮并再次留给<strong>日历</strong>数据透视刷。</p></li>
<li><p>点击应用程序栏中的<strong>新建</strong>图标，创建新的约会，为即将到来的时间。</p></li>
<li><p>验证新的约会将显示在测试设备以及其它手机<strong>日历</strong>数据透视表中。</p></li>
<li><p>启动<strong>照片</strong>数据透视表，然后点击<strong>添加</strong>按钮在应用程序栏中添加&quot;照片和视频&quot;。</p></li>
<li><p>验证已上载的照片和视频测试手机以及其他设备的<strong>照片</strong>数据透视表中所示。</p></li>
<li><p>将左刷到<strong>备注</strong>数据透视并点击<strong>添加</strong>按钮在应用程序栏中添加注释。</p></li>
<li><p>验证创建的注释将保存在<strong>注意</strong>数据透视表的测试设备和其他设备。</p></li>
</ol>

### <a name="search"></a>搜索

先决条件： 

<ul>
<li><p>连接到 Wi-fi。</p></li>
<li><p>使用 Microsoft 帐户签名。</p></li>
</ul>

测试步骤︰

<ol>
<li><p>点击搜索按钮启动搜索在电话上。</p></li>
<li><p>点击搜索编辑框内，输入搜索词&quot;狗。"</p></li>
<li><p>按 enter 键来搜索。</p></li>
<li><p>验证多个支枢上的搜索结果。</p></li>
<li><p>验证所有支枢，填入相关的结果，或者，没有消息表明没有任何结果。</p>
<div class="alert">
<strong>请注意</strong>  
<p>对于非美国图像，搜索结果可能会有所不同。 所有支枢可能不会出现。</p>
</div>
<div>
</div></li>
</ol>

### <a name="alarm"></a>警报

先决条件︰ 无

测试步骤︰

<ol>
<li><p>在应用程序列表中，点击<strong>警告&amp;时钟</strong>。</p></li>
<li><p>创建新警报。</p></li>
<li><p>保存新的警报。</p></li>
<li><p>验证警报将创建带有正确的信息。</p></li>
<li><p>验证警报音和名称闹钟响铃在使用正确的指定时间。</p></li>
</ol>

### <a name="themes"></a>主题

先决条件︰ 无

测试步骤︰

<ol>
<li><p>在应用程序列表中，点击<strong>设置</strong> &gt; <strong>个性化设置</strong> &gt; <strong>主题</strong>。</p></li>
<li><p><strong>背景</strong>和<strong>强调文字颜色</strong>更改的值。</p></li>
<li><p>请按<strong>开始</strong>以返回到开始屏幕。</p></li>
<li><p>确认设备的主题已被修改。</p></li>
</ol>

### <a name="contacts"></a>联系人

先决条件︰ 无

测试步骤︰

<ol>
<li><p>在启动屏幕上，点击<strong>人</strong>平铺。</p></li>
<li><p>从<strong>联系人</strong>数据透视表，单击应用程序栏上的<strong>添加 （+）</strong>按钮。</p></li>
<li><p>请输入电话号码，并将其保存。</p></li>
<li><p>验证新的数字被保存到联系人页。</p></li>
<li><p>选择已保存的电话号码。</p></li>
<li><p>点击<strong>编辑</strong>以修改所选的号码。 输入该联系人的名称，然后保存它。</p></li>
<li><p>验证正确修改联系人。</p></li>
<li><p>验证，将新的联系人保存到正确的名称在联系人页。</p></li>
<li><p>选择已保存的联系人。</p></li>
<li><p>点击<strong>选项</strong>。</p></li>
<li><p>点击<strong>删除</strong>。</p></li>
<li><p>验证已从联系人列表中删除该联系人。</p></li>
</ol>

### <a name="email"></a>Email

先决条件： 

从兼容的提供程序的几种有效的电子邮件帐户。

测试步骤︰

<ol>
<li><p>在应用程序列表中，点击<strong>设置</strong> &gt; <strong>帐户</strong> &gt; <strong>电子邮件&amp;帐户</strong>。</p></li>
<li><p>点击<strong>添加帐户</strong> &gt; <strong>Microsoft 帐户</strong>添加帐户。</p></li>
<li><p>在 Outlook 屏幕中，输入一个有效的电子邮件地址和密码。</p></li>
<li><p>请创建该帐户，并且，其同步向上正常未出现任何问题。</p></li>
<li><p>按下<strong>开始</strong>，然后点击<strong>电子邮件</strong>平铺。</p></li>
<li><p>验证电子邮件按预期显示。</p></li>
<li><p>单击<strong>新邮件</strong>（+） 图标。</p></li>
<li><p>撰写并发送电子邮件的主题、 主体，以及 Microsoft Excel 或 Word 文档附加您的帐户。</p></li>
<li><p>验证可以打开和读取计算机上的帐户的电子邮件。 从您的 PC 中的响应回复该电子邮件。</p></li>
<li><p>验证测试设备接收到新电子邮件的指示和拼贴更新以显示新邮件。</p></li>
<li><p>验证可以打开并阅读此邮件。</p></li>
<li><p>重复使用的电子邮件帐户的所有不同类型的步骤。</p></li>
</ol>

### <a name="microsoft-office"></a>Microsoft Office

先决条件︰ 无

测试步骤︰

<ol>
<li><p>在应用程序列表中，点击<strong>办公室</strong>。</p></li>
<li><p>刷卡左到<strong>最近</strong>的数据透视表。</p></li>
<li><p>验证存在至少三个示例文档︰</p>
<ol>
<li><p>示例文档。</p></li>
<li><p>示例演示文稿。</p></li>
<li><p>示例电子表格。</p></li>
</ol></li>
<li><p>请点击<strong>示例文档</strong>。</p></li>
<li><p>验证正确地呈现文档，您可以滚动文档。</p></li>
<li><p>按硬件后退按钮，关闭该文档。</p></li>
<li><p>点击<strong>电子表格的示例</strong>。</p></li>
<li><p>验证是否正确地呈现表 (即行 1，2，等和列 A、 B 等出现在视图中)，并且您可以滚动查看文档。</p></li>
<li><p>点击<strong>演示文稿示例</strong>。</p></li>
<li><p>验证演示文稿通过旋转手机到/从纵向/横向视图来显示手机的方向。 通过 2 至 3 张幻灯片过渡通过刷从右到左和旋转手机。</p></li>
<li><p>验证正确地呈现内容。</p></li>
<li><p>按硬件后退按钮以关闭该演示文稿。</p></li>
<li><p>在<strong>最近</strong>数据透视表，请点击<strong>添加 （+）</strong>按钮以创建新的 Word 文档。</p></li>
<li><p>打开一个空白的 Word 文档，并输入一些内容。 点击<strong>更多 （...）</strong> ，然后点击<strong>保存</strong>。</p></li>
<li><p>选择&quot;电话&quot;为要保存的数据的位置。 点击<strong>保存</strong>按钮保存创建的 Word 文档。</p></li>
<li><p>确认<strong>最近</strong>轴的 Office 应用程序中显示您创建的 Word 文档。</p></li>
<li><p>对 Excel 文档重复步骤 10-13。</p></li>
</ol>

### <a name="calendar"></a>日历

先决条件︰ 无

测试步骤︰

<ol>
<li><p>在应用程序列表中，单击<strong>日历</strong>。</p></li>
<li><p>请验证该日历应用程序将启动。</p></li>
<li><p>点击<strong>日历视图</strong>按钮，然后选择一个月。</p></li>
<li><p>验证您能够滚动日历上的几个月。</p></li>
<li><p>再次点击<strong>查看</strong>按钮，然后选择一天。</p></li>
<li><p>请验证您进入天屏幕。</p></li>
<li><p>在即将到来的小时内点击一个空白的网格上。</p></li>
<li><p>验证内联编辑框启动虚拟键盘。</p></li>
<li><p>在编辑框中输入"主题"文本框。</p></li>
<li><p>点击<strong>保存</strong>应用程序栏按钮。</p></li>
<li><p>确认保存和显示正确的主题和时间约会。</p></li>
<li><p>点击<strong>开始</strong>以返回到开始屏幕。</p></li>
<li><p>验证是否显示约会日历拼贴中的正确。</p></li>
<li><p>按下设备的电源按钮锁定设备。 再次按按钮以查看锁定屏幕。</p></li>
<li><p>确认在锁屏上显示日历约会。</p></li>
</ol>

### <a name="internet-explorer"></a>Internet Explorer

先决条件： 

<ul>
<li><p>必须启用 Bluetooth。</p></li>
<li><p>点击 + 发送测试第二个设备。</p></li>
</ul>

测试步骤︰

<ol>
<li><p>点击开始屏幕从 Internet Explorer。</p>
<div class="alert">
<strong>请注意</strong>  
<p>当第一次启动浏览器时，会弹出一个对话框询问&quot;使用推荐的设置？&quot; 点击<strong>推荐</strong>按钮。</p>
</div>
<div>
 
</div></li>
<li><p>请验证 Internet Explorer 中启动的程序。</p></li>
<li><p>请点击地址栏上。 开始键入网站的名称。</p></li>
<li><p>请验证输入的 URL 为自动建议，到场。</p></li>
<li><p>验证页面，输入的 url 加载内容。</p></li>
<li><p>验证页后，可以添加到收藏夹。</p></li>
<li><p>捏紧和拉伸来放大和缩小。 移动页面。 向上和向下页面滚动。 请验证这些笔势可以正常工作。</p></li>
<li><p>30-60 秒保持空闲的时间。</p></li>
<li><p>验证保留该设备空闲后没有任何问题的页面。</p></li>
<li><p>旋转设备。</p></li>
<li><p>验证从纵向改为横向过渡平稳。</p></li>
<li><p>请验证浏览器转换到正确的方向并在应用程序栏菜单都可见。</p></li>
<li><p>在应用程序栏右下方点击<strong>更多 （...）</strong>并点击<strong>收藏</strong>。</p></li>
<li><p>请验证您可以导航到您的收藏夹中列出的网站。</p></li>
<li><p>与第二个使用 NFC 手机共享网站 / 分路器 + 发送。</p>
<div class="alert">
<strong>请注意</strong>  
<p>如果第二个设备上首次启动浏览器时，将弹出对话框询问&quot;使用推荐的设置？&quot; 点击<strong>推荐</strong>。</p>
</div>
<div>
 
</div></li>
<li><p>验证共享的网站将在第二个设备的浏览器打开</p></li>
</ol>

### <a name="charging"></a>充电

先决条件︰ 无

测试步骤︰

<ul>
<li><p>墙壁充电器连接到设备并检查<strong>充电</strong>图标将显示。 您应该会听到声音指示后插入电缆。 拔下充电器。</p>
<div class="alert">
<strong>请注意</strong>  
<p>该设备没有打开无线充电工作。</p>
</div>
<div>
 
</div></li>
</ul>

### <a name="pc-companion"></a>PC 助理

先决条件︰ 无

测试步骤︰

<ol>
<li><p>将设备连接到计算机的 USB 电缆。</p></li>
<li><p>请检查该设备启动充电。</p></li>
<li><p>验证计算机辅助工具启动自动 PC 上几秒钟之后。</p></li>
</ol>

### <a name="ambient-light-sensor"></a>环境光线传感器

先决条件︰ 无

测试步骤︰

<ol>
<li><p>在应用程序列表中，点击<strong>设置</strong> &gt; <strong>系统</strong> &gt; <strong>显示</strong>。</p></li>
<li><p>验证已打开<strong>自动调整显示亮度</strong>选项。</p></li>
<li><p>请按<strong>开始</strong>以返回到开始屏幕。</p></li>
<li><p>从手电筒/火炬顶部的设备</p></li>
<li><p>验证显示的对比度变化对光的响应。</p></li>
</ol>

### <a name="display-and-accelerometer"></a>显示和加速感应器

先决条件︰ 无

测试步骤︰

<ol>
<li><p>在纵向模式下，通过全键盘运行的手指。</p></li>
<li><p>验证按预期的方式创建一封邮件。</p></li>
<li><p>旋转向左边和右边的设备。</p></li>
<li><p>验证屏幕方向平滑地改变。</p></li>
</ol>

### <a name="download-keyboard"></a>下载键盘

先决条件︰ 无

测试步骤︰

<ol>
<li><p>在应用程序列表中，点击<strong>设置</strong> &gt; <strong>设备</strong> &gt; <strong>键盘</strong>。</p></li>
<li><p>点击<strong>添加键盘</strong>。</p></li>
<li><p>选择一种键盘。</p></li>
<li><p>验证所选键盘语言将显示为&quot;准备下载...&quot;</p></li>
<li><p>验证下载后准备好之后，用户将会安装键盘选项。</p></li>
<li><p>安装键盘。</p></li>
<li><p>验证重新启动设备并安装这些更新。</p></li>
<li><p>从开始屏幕中，启动消息传递应用程序。</p></li>
<li><p>创建新的 SMS 消息。</p></li>
<li><p>点击并按住<strong>ENG</strong>按钮在虚拟键盘上。 从菜单中选择新下载的语言。</p></li>
<li><p>请验证将键盘更改为新语言键盘。</p></li>
<li><p>创建并发送新的短信。</p></li>
<li><p>验证 SMS 消息成功发送和收到的第二个设备上的相同语言</p></li>
</ol>

### <a name="download-app-from-store"></a>从存储库下载应用程序

先决条件： 

必须连接 Wi-fi。

测试步骤︰

<ol>
<li><p>从开始屏幕上，点击<strong>存储</strong>。</p></li>
<li><p>请验证该存储区中启动的程序</p></li>
<li><p>从商店首页中选择应用程序或游戏，并将其安装。</p></li>
<li><p>请验证您可以监视应用程序/游戏的下载进度。</p></li>
<li><p>验证在 5 分钟之内完成游戏下载进度条消失了。</p></li>
<li><p>验证下载后，可启动的应用程序/游戏。</p></li>
</ol>

### <a name="skype-video-calling"></a>Skype （视频通话）

先决条件： 

<ul>
<li><p>您必须连接到 Wi-fi。</p></li>
<li><p>Bluetooth 设备。</p></li>
<li><p>第二个电话</p></li>
<li><p>两个 Microsoft 帐户 （一个用于每个设备） 使用 Skype。</p></li>
</ul>

测试步骤︰

<ol>
<li><p>从开始屏幕上，点击<strong>存储</strong>。</p></li>
<li><p>搜索并下载 Skype 应用程序。</p></li>
<li><p>在应用程序列表中，点击<strong>设置</strong> &gt; <strong>设备</strong> &gt; <strong>Bluetooth</strong>。 启用 Bluetooth。</p></li>
<li><p>在 paring 模式下，将 Bluetooth 设备，然后配对到 Bluetooth 设备的测试设备。</p></li>
<li><p>启动 Skype 应用程序。</p></li>
<li><p>验证的条款和条件页面弹出。</p></li>
<li><p>点击<strong>接受</strong>。</p></li>
<li><p>验证显示登录屏幕。</p></li>
<li><p>滚动到底部的登录页，使用 Microsoft 帐户登录。</p></li>
<li><p>验证允许邮件通知？ 消息弹出的<strong>是</strong>和<strong>无</strong>按钮。</p></li>
<li><p>点击<strong>没有</strong>。</p>
<div class="alert">
<strong>请注意</strong>  
<p>要为 Skype 测试做好准备的第二个设备上执行相同的步骤。</p>
</div>
<div>
 
</div></li>
<li><p>第二个电话，<strong>人们</strong>透视和选择 Skype 就是刷与测试设备</p></li>
<li><p>请使用第二个设备的测试设备的音频呼叫。</p></li>
<li><p>在测试设备上，请验证传入的呼叫，听到铃声。</p></li>
<li><p>应答呼叫使用 Bluetooth 设备。</p></li>
<li><p>验证 （测试设备上的音频应该通过 Bluetooth 设备路由） 这两个设备上可以听到音频。</p></li>
<li><p>检查静音和取消静音功能适用于测试，第二个电话。</p></li>
<li><p>断开呼叫使用 Bluetooth 设备的连接。</p></li>
<li><p>验证呼叫断开后，听不到音频。</p></li>
<li><p>关闭 Bluetooth。</p></li>
<li><p>在测试设备上，刷卡<strong>人</strong>轴向左，请选择第二个设备的 Skype 帐户。</p></li>
<li><p>进行到第二个设备发送视频通话。</p></li>
<li><p>验证传出的电话通知时听到从测试设备的扬声器</p></li>
<li><p>收到第二个设备上传入的视频通话。</p></li>
<li><p>验证呼叫连接。</p></li>
<li><p>验证在两个设备上使用视频和音频。</p></li>
<li><p>验证这两台设备的工作静音和取消静音功能。</p></li>
<li><p>断开测试设备的呼叫。</p></li>
<li><p>验证呼叫断开后，听不到音频。</p></li>
</ol>

### <a name="play-a-game"></a>玩游戏

先决条件： 

从应用程序商店下载生气的小鸟游戏。

测试步骤︰

<ol>
<li><p>在应用程序列表中，启动生气的小鸟游戏.</p></li>
<li><p>确认，在 15-20 秒加载游戏。</p></li>
<li><p>验证主菜单上播放背景音乐。</p></li>
<li><p>验证可以静音和 unmuted 音乐。</p></li>
<li><p>按<strong>播放</strong>按钮位于屏幕的中心。</p></li>
<li><p>请验证游戏，加载到可播放的级别。</p></li>
<li><p>播放此级别。</p></li>
<li><p>检查游戏的视觉效果和音频平稳。</p></li>
<li><p>请验证该游戏不崩溃。</p></li>
<li><p>验证可以暂停和取消暂停游戏。</p></li>
</ol>

### <a name="backup-and-restore-content"></a>备份和恢复内容

先决条件： 

<ul>
<li><p>连接到 Wi-fi。</p></li>
<li><p>应用程序下载到设备上</p></li>
<li><p>Microsoft 的帐户。</p></li>
</ul>

测试步骤︰

<ol>
<li><p>在应用程序列表中，点击<strong>设置</strong> &gt; <strong>个性化设置</strong> &gt; <strong>主题</strong>。</p></li>
<li><p>更改背景和强调 aolor。</p></li>
<li><p>在应用程序列表中，点击<strong>设置</strong> &gt; <strong>帐户</strong> &gt; <strong>电子邮件&amp;帐户</strong>。</p></li>
<li><p>使用您的 Microsoft 帐户登录。</p></li>
<li><p>启动 Internet Explorer。</p></li>
<li><p>转到网站，并将其添加到您的收藏夹。</p></li>
<li><p>请转到第二个网站并将其添加到您的收藏夹。</p></li>
<li><p>在应用程序列表中，点击<strong>设置</strong> &gt; <strong>更新&amp;恢复</strong> &gt; <strong>备份</strong>。</p></li>
<li><p>打开备份。</p></li>
<li><p>在应用程序列表中，点击<strong>设置</strong> &gt; <strong>系统</strong> &gt; <strong>有关</strong> &gt; <strong>重置您的电话</strong>。</p></li>
<li><p>A&quot;警告 ！&quot; 弹出消息将显示两次。 请点击&quot;是&quot;两次重置设备</p></li>
<li><p>验证，则重置该设备，然后继续完成 OOBE。</p></li>
<li><p>当在 OOBE 期间出现提示，请连接到 Wi-fi 网络。</p></li>
<li><p>当在 OOBE 期间出现提示，请输入您一直使用同一个 Microsoft 帐户。</p></li>
<li><p>当在 OOBE 期间出现提示，请选择要将刚创建的备份还原。</p>
<div class="alert">
<strong>请注意</strong>  
<p>此备份应在备份列表的顶部选择。 检查日期和时间，若要验证，然后选择备份。</p>
</div>
<div>
 
</div></li>
<li><p>继续执行 OOBE 过程的其余部分。</p></li>
<li><p>在开始屏幕中，验证是否强调文字颜色和背景色，与第 2 步所做的更改相匹配。</p></li>
<li><p>启动 Internet Explorer，然后打开您的收藏夹。</p></li>
<li><p>验证在收藏夹中列出了您在前面的步骤中添加的网站。</p></li>
<li><p>在应用程序列表中，验证列出仍到您已下载的应用程序。</p></li>
<li><p>在应用程序列表中，点击<strong>设置</strong> &gt; <strong>帐户</strong> &gt; <strong>电子邮件&amp;帐户</strong>。 已登录的帐户上点击并输入密码。</p></li>
<li><p>请验证您的电子邮件帐户被同步。</p></li>
</ol>

### <a name="kids-corner"></a>儿童天地

先决条件： 

从存储库安装到设备的游戏。

测试步骤︰

<ol>
<li><p>在应用程序列表中，点击<strong>设置</strong> &gt; <strong>儿童天地</strong>。</p></li>
<li><p>验证启动儿童天地的欢迎页面。</p></li>
<li><p>将游戏添加到小孩的角。</p></li>
<li><p>将两个应用程序添加到小孩的角。</p></li>
<li><p>点击<strong>下一步</strong>。</p></li>
<li><p>验证密码对话框弹出。</p></li>
<li><p>创建一个密码。</p></li>
<li><p>点击<strong>完成</strong>。</p></li>
<li><p>验证启动儿童天地时。</p></li>
<li><p>在屏幕上刷。 如果系统提示您，输入密码。</p></li>
<li><p>验证启动儿童天地主页屏幕只有应用程序和游戏设置童角时检查的是出现在屏幕上。</p></li>
<li><p>锁定和解锁设备。</p></li>
<li><p>验证密码对话框弹出。 输入密码，然后将设备解锁。</p></li>
<li><p>验证显示启动屏幕。</p></li>
</ol>

### <a name="nfc-tag-reading"></a>NFC 标记读数

先决条件： 

<ul>
<li><p>要扫描 QR/NFC/URL 标记项。</p></li>
<li><p>连接到 Wi-fi 按照标记路径。</p></li>
</ul>

测试步骤︰

<ol>
<li><p>保留设备闲置，使其进入睡眠状态。 按下设备的电源按钮，弹出锁定屏幕。</p></li>
<li><p>保持<strong>相机</strong>上的按钮 （虽然锁定屏幕） 来打开相机。</p>
<div class="alert">
<strong>请注意</strong>  
<p>如果手机没有照相机按钮，直接启动摄像头应用程序。</p>
</div>
<div>
 
</div></li>
<li><p>选择<strong>镜头</strong>按钮。</p></li>
<li><p>选择<strong>Bing 远景</strong>。</p></li>
<li><p>要扫描 QR 标记保存相机。</p></li>
<li><p>选择框图像/超级扫描后出现。</p></li>
<li><p>请验证您进入相应的页面与扫描标记相关联。</p></li>
<li><p>在应用程序列表中，点击<strong>设置</strong> &gt; <strong>个性化设置</strong> &gt; <strong>锁定屏幕</strong>。</p></li>
<li><p>打开"打开"密码并创建密码。</p></li>
<li><p>保留设备闲置，使其进入睡眠状态。 按下设备的电源按钮，弹出锁定屏幕。</p></li>
<li><p>按住照相机按钮 （虽然在锁屏上） 可以调出照相机。</p></li>
<li><p>按<strong>镜头</strong>。</p></li>
<li><p>选择<strong>Bing 远景</strong>。</p></li>
<li><p>请验证该用户必须输入密码才能访问 Bing 的设想。</p></li>
</ol>

### <a name="lens-picker"></a>镜头的选择器

先决条件： 

<ul>
<li><p>必须登录到 Microsoft 客户安装镜头。</p></li>
<li><p>若要使用共享 NFC，必须开启 Bluetooth。</p></li>
<li><p>NFC 功能的第二个设备。</p></li>
</ul>

测试步骤︰

<ol>
<li><p>按住照相机硬件键以启动摄像头应用程序 （或者如果设备没有相机按钮直接启动应用程序），并点击<strong>取消</strong>以&quot;允许相机以使用您的位置&quot;屏幕。</p>
<div class="alert">
<strong>请注意</strong>  
<p>"允许...位置"提示符会记住以前的设置，如果最近使用过的相机不会显示。</p>
</div>
<div>
 
</div></li>
<li><p>点击<strong>镜头</strong>按钮。</p></li>
<li><p>确认与<strong>Bing 远景</strong>图标和图标的任何已安装的镜头出现镜头覆盖。</p></li>
<li><p>选择已安装的镜头之一。 如果没有镜头的应用程序已安装，您将需要下载一个。</p>
<ol>
<li><p>选择"查找更多的镜头"</p></li>
<li><p>选择并安装应用程序列表中。</p></li>
</ol></li>
<li><p>请验证您可以使用应用程序已安装的镜头的图片。</p></li>
<li><p>验证，显示图片和最新图片和相机之间滚动。</p></li>
<li><p>选择一个新的图片。</p></li>
<li><p>验证您可以共享照片使用 NFC / 分路器 + 共享。</p></li>
</ol>

### <a name="local-scout-load-time"></a>本地侦察加载时间

先决条件︰ 无

测试步骤︰

<ol>
<li><p>启动<strong>本地侦察</strong>。</p></li>
<li><p>如果您第一次启动本地侦察，允许访问您当前所在的位置。</p></li>
<li><p>验证您能够看到不同类型的本地机构的各个选项卡。</p></li>
<li><p>选择一家餐馆。</p></li>
<li><p>请确保已提供餐馆的相应信息。</p></li>
<li><p>选择方向。</p></li>
<li><p>请验证映射，加载到餐馆的方向。</p></li>
<li><p>请验证本地侦察，在可接受的一段时间加载位置中的结果。</p></li>
</ol>

### <a name="download-maps"></a>下载地图

先决条件： 

连接到 Wi-fi 下载地图。

测试步骤︰

<ol>
<li><p>在应用程序列表中，点击<strong>地图</strong> &gt; <strong>更多 （...）</strong>&gt; <strong>设置</strong>。</p>
<div class="alert">
<strong>请注意</strong>  
<p>如果第一次启动应用程序，该应用程序将询问电话位置的访问权。 允许访问的位置。</p>
</div>
<div>
 
</div></li>
<li><p>选择<strong>下载地图</strong>。</p></li>
<li><p>点击<strong>添加 （+）</strong>按钮。</p></li>
<li><p>选择<strong>北美和中美洲</strong> &gt; <strong>美国</strong> &gt; <strong>印地安那州</strong>。</p></li>
<li><p>等待要完成下载的映射。</p></li>
<li><p>请按<strong>开始</strong>以返回到开始屏幕。</p></li>
<li><p>在应用程序列表中，点击<strong>设置</strong> &gt; <strong>飞机模式</strong> &gt; <strong>打开</strong>。</p></li>
<li><p>按<strong>开始</strong>，然后在应用程序列表中，点击<strong>地图</strong>。</p></li>
<li><p>点击<strong>搜索</strong>（放大镜），然后搜索"Butte，蒙大纳"。</p></li>
<li><p>验证不能下载地图中找到的 Butte，蒙大纳。</p></li>
<li><p>搜索"Indianapolis，印地安那州"。</p></li>
<li><p>请验证映射加载 Indianapolis，印地安那州的下载的地图。</p></li>
</ol>

### <a name="visual-voicemail"></a>可视语音邮件

先决条件： 

您将需要第二台设备。

测试步骤︰

<ol>
<li><p>测试设备关闭电源</p></li>
<li><p>调用使用第二个设备的测试设备。</p></li>
<li><p>验证呼叫转到语音邮件。 保留的语音邮件。</p></li>
<li><p>在测试设备上的电源。</p></li>
<li><p>点击<strong>电话</strong>。</p></li>
<li><p>敲击<strong>语音邮件</strong>图标。</p></li>
<li><p>接受可视语音邮件客户端安装程序。</p></li>
<li><p>验证语音邮件被下载后安装，并且您可以收听语音邮件。</p></li>
<li><p>从第二个设备再次调用测试设备。 没有回答。</p></li>
<li><p>验证呼叫转到语音邮件。 将一条消息。</p></li>
<li><p>确认您收到 SMS 消息，以指示可用的语音邮件。 验证列出了新的语音邮件，您可以收听语音邮件。</p></li>
<li><p>重复步骤 9-10，并将第二个语音邮件。</p></li>
<li><p>验证一个图标显示列出的两个语音邮件。</p></li>
<li><p>播放语音邮件。</p></li>
<li><p>删除语音邮件。</p></li>
</ol>

### <a name="internet-sharing"></a>互联网共享

先决条件： 

<ul>
<li><p>允许共享的数据计划。</p></li>
<li><p>任何 Wi-Fi 的电源设备。</p></li>
</ul>

测试步骤︰

<ol>
<li><p>打开互联网共享。</p></li>
<li><p>与第二个设备，在设备上使用的用户名和密码连接到共享的 Wi-Fi。</p>
<div class="alert">
<strong>请注意</strong>  
<p>第二个设备应有自己 Wi-fi 开启。</p>
</div>
<div>
 
</div></li>
<li><p>验证第二个设备可以浏览互联网。</p></li>
<li><p>请验证该设备显示的来宾数量 （第二个设备） 连接到 Wi-fi 共享。</p></li>
</ol>

### <a name="storage-manager"></a>存储管理器

先决条件︰ 无

测试步骤︰

<ol>
<li><p>在应用程序列表中，点击<strong>设置</strong> &gt; <strong>系统</strong> &gt; <strong>存储有意义</strong>。</p></li>
<li><p>点击设备。</p></li>
<li><p>验证数据使用条形图显示如下︰</p>
<ol>
<li><p>应用程序 + 游戏</p></li>
<li><p>地图</p></li>
<li><p>临时文件</p></li>
<li><p>照片</p></li>
<li><p>音乐</p></li>
<li><p>视频</p></li>
<li><p>文档</p></li>
<li><p>电子邮件 + 消息</p></li>
<li><p>系统</p></li>
<li><p>其他</p></li>
</ol></li>
<li><p>点击该条目。</p></li>
<li><p>请验证您可以滚动查看应用程序的详细信息页面。</p></li>
<li><p>确认显示的每个应用程序的内存空间量。</p></li>
</ol> 
 
 






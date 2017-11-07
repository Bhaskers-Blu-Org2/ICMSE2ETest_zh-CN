---
ms.Toctitle: Video REST API reference
title: "视频的 REST API 参考"
description: "引用使用视频 REST API，来发现、 交往、 并在 SharePoint Online 的 Office 365 视频服务中获取有关视频和渠道的信息。"
ms.ContentId: 4202e210-44be-4289-808d-3b7358181cc0
ms.date: November 17, 2015
ms.openlocfilehash: a4194467f28959785912432fe0e6350aab895bcb
ms.sourcegitcommit: 4648ef0fb81b465cef7e8ccad197fe9b9edabc33
translationtype: MT
---
# <a name="video-rest-api-reference"></a>视频的 REST API 参考


 _**适用于︰**SharePoint 在线 |Office 365_

其余部分视频 API 可用于发现并与 Office 365 视频服务在 SharePoint Online 中的视频进行交互。 可以获取信息的视频和频道、 上载新的视频，并获取到的视频流的信息。

<a name="Overview"> </a>
## <a name="using-the-video-rest-api"></a>使用视频 REST API，

有两种类型的对象与之交互视频 REST API︰ 视频和渠道。

若要与视频 REST API 进行交互，您发送 HTTP 请求，使用受支持的方法︰ 获取、 发布、 合并或删除。

所有视频 API 请求都使用来自发现服务后, 根 URL"视频门户操作"一节中所述。

路径的 URL 资源名称和查询参数都区分大小写。 但是，您指定的值、 实体 Id 和其他 base64 编码的值是区分大小写。

Office 365 Api 使用 Microsoft Azure 活动目录 (AD Azure) 和 OAuth[请求应用程序进行身份验证](..\howto\common-app-authentication-tasks.md)。
若要从应用程序访问视频 API，您需要将其注册 Azure AD 具有[权限在适当范围](..\howto\common-app-authentication-tasks.md#sectionSection0)中。
Office 365 视频 REST API 支持 OData 4.0 标准，并允许使用 RESTful 接口与 Office 365 的视频数据进行交互的应用程序。

权限的应用范围限定为三个自定义组︰

 - 管理员可以更改通道设置和编辑视频。
 - 参与者可以创建、 读取、 更新和删除 (CRUD) 视频。
 - 观众才可以观看视频。

每个通道的通道所有者确定组织中谁落在每个组。 此外，SharePoint 组织管理员可以作出相同的决定。


**请注意**若要了解详细信息，请参阅[在 Office 365 的平台上的开发](..\howto\platform-development-overview.md)。

<a name="VideoPortalOperations"> </a>
## <a name="video-portal-operations"></a>视频门户网站操作

可以获取视频门户网站的根 URL，用于所有其他视频 REST API 操作，并可以发现视频门户网站是否已设置并启用。

****

<a name="GetPortalInformation"></a> 
**获取视频门户网站的信息**

O365[发现服务](..\api\discovery-service-rest-operations.md)用于获取根 SharePoint 网站集 URL (RootSite)，然后从该 URL 以获取在 SharePoint Online，然后在所有后续的调用中使用的视频门户网站的 URL 调用 VideoService.Discover。 确定视频门户设置和启用。

**请注意**若要访问发现服务，您必须登录到 SharePoint 门户网站为您的公司。

通常情况下，SharePoint 的根网站集的端点 URL 可能如下所示 （为虚构公司 Contoso）︰

https://contoso.sharepoint.com/

发现服务返回同一个公司的视频门户的端点 URL 然后会显示如下︰

https://contoso.sharepoint.com/portals/hub

```no-highlight
GET {RootSite}/_api/VideoService.Discover
```

**请注意***RootSite*参数是一个字符串，表示端点 URL 的根站点集合的 SharePoint 中，从发现服务中检索。 |

 **响应类型**

- **IsVideoPortalEnabled** — 如果返回门户网站已启用且，假如果设置未启用或者不设置门户。
- **VideoPortalURL** — 端点 URL 的视频门户网站，所有后续的调用中使用。

**请注意**我们建议您定义并使用此 URL，常数，使它变为可用时，可以轻松地添加版本信息。

[!code-REST-i[Get_Portal_Info](./_data/video_api_get_portal_info.json)]


<a name="ChannelOperations"> </a>
## <a name="channel-operations"></a>信道操作

视频存储通道中。 您可以向其所有通道的用户可以上传视频、 列表和列表中的用户可以查看的所有通道。
此外可以获取有关特定频道，包括一个通道的 ID、 一个通道的颜色、 通道，标题和一组通道包含的所有视频信息。

****

<a name="GetChannelsInfo"> </a>
### <a name="get-information-about-the-channels-the-user-can-view-or-upload-to"></a>获取有关用户可以查看或将上载到的通道信息

<a name="GetUploadChannels"></a> 
**获取的渠道向其用户可以上传视频的列表**

获取列表频道用户可以上传至视频。 这些都是对其有所有者或编辑权限的通道。


```no-highlight
GET {VideoPortalURL}/_api/VideoService/CanEditChannels
```

**请注意**在这和所有的后续调用中， *VideoPortalURL*是一个字符串，表示端点 URL 的视频门户网站，从 VideoService.Discover 调用中检索。


 **响应类型**

返回信道对象的列表。

**请注意**如果视频门户网站有大量的通道，此 API 可以花很长时间才能返回。


****

<a name="GetViewChannels"></a> 
**获得的用户可以查看的频道列表**


获取列表中的用户可以查看的所有通道。 这些都是对其有所有者、 编辑器或查看器权限的通道。


```no-highlight
GET {VideoPortalURL}/_api/VideoService/Channels
```

 **响应类型**

返回信道对象的列表。

[!code-REST-i[Get_ChannelView_Info](./_data/video_api_get_channels_view.json)]


****

<a name="GetChannelInfo"> </a>
### <a name="get-information-about-a-particular-channel"></a>获取有关特定通道的信息

<a name="GetInfo"></a> 
**获取通道 ID、 通道颜色和频道标题**

```no-highlight
GET {VideoPortalURL}/_api/VideoService/Channels('{channelId}')
```
**请求的 URL 参数**

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|channelId|string|通道的 ID。|


 **响应类型**

返回一个通道有关的下列信息︰
- Id — 通道的 ID。
- TileHtmlColor-通道中的颜色。
- 标题-通道的标题。

[!code-REST-i[Get_Channel_Info](./_data/video_api_get_channel_info.json)]



<a name="GetVideoList"></a> 
**获得的信道上的所有视频列表**

获取指定的通道上的列表中的所有视频。

```no-highlight
GET {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos
```

**请求的 URL 参数**

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|channelId|string|通道的 ID。|


 **响应类型**

返回视频对象的列表。

[!code-REST-i[Get_Video_List](./_data/video_api_get_video_list.json)]


****

<a name="GetPlayableVideos"></a> 
**获取信道上的最新可播放的视频的列表**

获取通道和筛选掉所有尚未准备好了，除了那些您已上载的视频的最后一次上载视频排序的列表。

这将返回的所有视频通道，已经完成转换代码，就可以播放排序的列表 (VideoProcessingStatus = 2)，并不是准备好了，如果他们当前登录的用户上传的视频。  

```no-highlight
GET {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/GetAllVideos
```

**请求的 URL 参数**

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|channelId|string|通道的 ID。|


 **响应类型**

返回视频对象的列表

****

<a name="VideoOperations"> </a>
## <a name="video-operations"></a>视频的操作

获取有关特定的信息视频从一个通道、 获取看视频了，多少次的计数和获取播放的信息。 此外，将视频上传到一个通道、 更新的视频频道，并删除信道中的视频。
****


<a name="GetVideoInfo"> </a>
### <a name="get-information-about-a-video"></a>获取有关视频信息

获取有关特定的视频，包括它的创建的日期、 标题、 其持续时间，视频和其处理状态的缩略图的 URL 的信息。

```no-highlight
GET {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')
```

**请求的 URL 参数**

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|channelId|string|通道的 ID。|
|videoId|string|视频的 ID。|

 **响应类型**

返回以下信息︰
- CreatedDate-最初上载视频的日期。
- 标题-视频的标题。
- VideoDurationInSeconds-持续时间的视频中，以秒为单位。
- ThumbnailURL-视频的缩略图图像的 URL。
- VideoProcessingStatus-视频处理过程的状态。 可以采用下列值︰
    - 0-（默认）-视频尚未处理的播放。
    - 1--视频已经领取，并正在处理。
    - 2--视频是准备好了。
    - 3--视频遇到一个错误，虽然它已上载到 Azure 媒体服务以进行处理。
    - 4-错误--一般错误-无法处理的视频流。
    - 5-错误--超时错误-无法处理的视频流。
    - 6-错误--不支持的格式 — 视频文件类型不支持流播放通过 Azure 媒体服务。

[!code-REST-i[Get_Video_Info](./_data/video_api_get_video_info.json)]

****

<a name="GetViewCountInfo"></a> 
**获得的视频已经被浏览的次数计数**

查看计数返回仅在您从终结点搜索，检索视频对象时因为通过搜索分析聚合视图计数。 因此 ViewCount 属性将具有不准确的值，除非它通过集线器或通道 /Search 结束点。
要获得单个视频查看计数，请运行搜索查询使用视频的 id。


```no-highlight
GET {VideoPortalURL}/_api/videoservice/Channels('{channelId}')/search/query('{videoId}')?$Select=ViewCount
```

**请求的 URL 参数**

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|channelId|string|通道的 ID。|
|videoId|string|视频的 ID。|

**查询参数**

|名称|类型|说明|
|:-----|:-----|:-----|
|_ $选择 = ViewCount|string|要在响应中包含视图计数。|

 **响应类型**

返回视频已经被浏览的次数。

[!code-REST-i[Get_View_Count](./_data/video_api_get_view_count.json)]


****

<a name="GetPlaybackInfo"> </a>
### <a name="get-information-about-playing-a-video"></a>获取有关播放视频信息

<a name="GetVideoManifest"></a> 
 **Azure 媒体服务的获取 URL 清单用于视频**

这视频获取 Azure 媒体服务清单 URL。 此清单可以送入播放器播放 Azure 媒体服务资产的支持。

```no-highlight
GET {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')/GetPlaybackUrl('{streamingFormatType}')
```

**请求的 URL 参数**

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|channelId|string|通道的 ID。|
|videoId|string|视频的 ID。|
|streamingFormatType|数字|视频流的格式类型。|

*StreamingFormatType*参数可以采用下列值︰
- 1--平滑流式处理或 MPEG 短划线
- 0--HLS 流

**响应类型**

返回的清单的视频的 URL。

[!code-REST-i[Get_Format_Info](./_data/video_api_get_streaming_format.json)]


****

<a name="GetDecryptionToken"></a> 
**得到的持有者标记访问解密视频**

所有的 O365 视频是 AES 加密。 对于以平滑流式处理或 MPEG 划线的格式播放视频，首先需要获得载体令牌访问来解密内容。 此 API 返回的身份验证令牌允许播放机来解密内容。

但是，HLS 流，不必检索密钥访问令牌分别，因为它已经是清单 URL 时检索 HLS 格式的清单的一部分。


```no-highlight
GET {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')/GetStreamingKeyAccessToken
```

**请求的 URL 参数**

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|channelId|string|通道的 ID。|
|videoId|string|视频的 ID。|


 **响应类型**

返回身份验证令牌，以允许玩家解密内容。

[!code-REST-i[Get_Bearer_Token](./_data/video_api_get_bearer_token.json)]

****

<a name="UploadVideos"> </a>
### <a name="upload-videos-to-a-channel"></a>将视频上传到一个通道

创建一个空的视频对象上载视频作为占位符。

之后执行此操作，您可以上传一次开机自检调用，一个小视频或一个较大的活动，以块的形式，在多个开机自检期间调用。

<a name="CreateEmptyVideoObject"></a> 
**创建上载视频的占位符**


创建一个空的视频对象，充当占位符的位置将要上传视频。

```no-highlight
POST {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos
```

**请求的 URL 参数**

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|channelId|string|通道的 ID。|


**请求正文**

{__metadata: {type: sp。Publishing.VideoItem}，说明: {        *此处输入您的说明文字*
 } '，标题: {        *此处视频的标题*
 }}


|名称|类型|说明|
|:-----|:-----|:-----|
|元数据|SP。Publishing.VideoItem|要更新的对象的类型|
|说明|string|该视频说明。|
|标题|string|视频的标题。|
|FileName|string|视频文件的名称。|


**响应类型**

VideoObject — 在其中上载视频对象。 作为视频的 ID 返回的 ID 用于启动上载到。

****

<a name="UploadSmallVideo"></a> 
**上载单个 post 过程中的一个小视频**

将上载单个视频不够小，无法在一个帖子中传输。


```no-highlight
POST {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')/GetFile()/SaveBinaryStream
```
[//]: # (just checking that the above empty parens for GetFile are intentional)

**请求的 URL 参数**

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|channelId|string|通道的 ID。|
|videoId|string|视频的 ID。|

**请求正文**

该文件的二进制流。 

**响应类型**

返回 200。 没有响应正文。

****

<a name="UploadLargerVideoInChunks"> </a>
###<a name="upload-a-larger-video-in-chunks"></a>上载较大的块视频

使用下面的调用上载太大，无法放入公告一次，或者取消分块的上载的视频。


<a name="StartUploading"></a> 
**开始上载到先前创建的视频对象**

启动该分块的视频上传。

```no-highlight
POST {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')/GetFile()/StartUpload(uploadId=guid'{yourGeneratedGuid}')
```

**请求的 URL 参数**

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|channelId|string|通道的 ID。|
|videoId|string|视频的 ID。|
|yourGeneratedGuid|GUID|在上载会话生成 GUID。|


**响应类型**

返回 200。 没有响应正文。

****

<a name="UploadEachChunk"></a> 
**上载到先前创建的该视频对象的文件的每个块**

继续上传文件的下一区块。 根据需要多次重复。

```no-highlight
POST {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')/GetFile()/ContinueUpload(uploadId=guid'{yourGeneratedGuid}',fileOffset='{offsetSize}')
```

**请求的 URL 参数**

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|channelId|string|通道的 ID。|
|videoId|string|视频的 ID。|
|yourGeneratedGuid|GUID|在上载会话生成 GUID。|
|offsetSize|integer|已上载的字节值。|

**注意︰**如果您上传 8 MB 区块，第一个块区的偏移量为零，而第二个文本块的偏移量 8 * 1024 = 8192。


**请求正文**

此块文件二进制流。

**响应类型**

返回 200。 没有响应正文。

****


<a name="FinishUploading"></a> 
**完成上载到先前创建的该视频对象的文件的最后一个区块**

完成该分块的视频上传。

```no-highlight
POST {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')/GetFile()/FinishUpload(uploadId=guid'{yourGeneratedGuid}',fileOffset='{offsetSize}')
```

**请求的 URL 参数**

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|channelId|string|通道的 ID。|
|videoId|string|视频的 ID。|
|yourGeneratedGuid|GUID|在上载会话生成 GUID。|
|offsetSize|integer|已上载的字节值。|

**请求正文**

最后一个区块文件二进制流。

**响应类型**

返回 200。 没有响应正文。

****

<a name="CancelChunkedUploading"></a> 
**取消上载**

取消该分块的视频上传。

```no-highlight
POST {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')/GetFile()/CancelUpload(uploadId=guid'{yourGeneratedGuid}')
```

**请求的 URL 参数**

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|channelId|string|通道的 ID。|
|videoId|string|视频的 ID。|
|yourGeneratedGuid|GUID|在上载会话生成 GUID。|

**响应类型**

返回 200。 没有响应正文。

****


<a name="UpdateVideo"> </a>
###<a name="update-video-metadata"></a>更新视频元数据
**更新现有的视频通道上的元数据**


更改标题和说明的视频。

```no-highlight
POST {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')
```

**请求的 URL 参数**

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|channelId|string|通道的 ID。|
|videoId|string|视频的 ID。|


**请求标头**

|名称|类型|说明|
|:-----|:-----|:-----|
|X-HTTP 方法|string|合并是 X HTTP 方法的属性的值。|


**请求正文**

{__metadata: {type: SP。Publishing.VideoItem'},'Description': ' {*您的说明文本*}、 标题: {*此处视频的标题*}}

|名称|类型|说明|
|:-----|:-----|:-----|
|元数据|SP。Publishing.VideoItem|视频对象的类型。|
|说明|string|该视频说明。|
|标题|string|视频的标题。|

 **响应类型**

返回 200。 没有响应正文。

****

<a name="DeleteVideos"> </a>
## <a name="delete-videos-from-a-channel"></a>删除视频从一个通道



<a name="DeleteVideo"></a> 
**删除现有的视频从一个通道**


```no-highlight
 POST {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')
```

**请求的 URL 参数**

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|channelId|string|通道的 ID。|
|videoId|string|视频的 ID。|


**请求标头**

|名称|类型|说明|
|:-----|:-----|:-----|
|X-HTTP 方法|string|删除是 X HTTP 方法的属性的值。|

 **响应类型**

返回 200。 没有响应正文。

****

<a name="EmbedVideo"> </a>
## <a name="embed-a-video-in-another-page"></a>在另一个网页中嵌入视频

****

<a name="GetEmbedCodeConfigureParameters"></a> 
**获得，可以嵌入在另一个 web 页中，指定参数值的视频项目的代码**

使用此调用，您可以指定的参数传递，例如宽度和高度的嵌入式的窗口、 视频是否在打开数据访问页中，会自动播放和视频暂停时，视频播放器中显示某些信息是是否值。 这些信息包括视频的标题，其持续时间，多少次打完的计数。 和频道的名称。 

```no-highlight
GET {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')/GetVideoEmbedCode?width={width}&height={height}&autoplay={true/false}&showinfo={true/false}
```

如果不传递的参数值，Office 365 将选择一些适当的默认值，如 120 的宽度和高度 230。

**请求的 URL 参数**

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|channelId|string|通道的 ID。|
|videoId|string|视频的 ID。|
|width|数字|嵌入的视频窗口的宽度。|
|height|数字|嵌入的视频窗口的高度。|
|自动播放|真/假|是否嵌入的视频将自动启动。|
|ShowInfo|真/假|无论视频标题、 持续时间、 查看计数和信道名称时才显示在播放机中视频暂停。|


**响应类型**

返回嵌入代码。

****

<a name="GetEmbedCodeDefaultValues"></a> 
**获得，允许您将视频项目在使用默认值的其他网页中嵌入的代码**

使用此调用，您可以指定默认值为嵌入式视频播放器嵌入代码。

```no-highlight
GET {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')/?$Select=Title,DefaultEmbedCode
```

"DefaultEmbedCode"属性不会自动返回视频对象。 若要获取"DefaultEmbedCode"，您需要使用 $select 选项。

通过使用 $select 选项，您可以请求返回的任何视频属性，包括标题和默认嵌入代码，如下所示的视频项目。

**请求的 URL 参数**

|**必选的参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|channelId|string|通道的 ID。|
|videoId|string|视频的 ID。|


**响应类型**

返回通过使用 $select，包括默认请求任何默认属性嵌入代码。

****

<a name="GetVideoItemFromPlayerPageURL"></a> 
**获得视频项目的信息和默认值嵌入播放器的网页的 URL 的代码**

使用此调用后，如果您知道视频的 O365 视频播放器门户页面的 URL，您可以获得视频 ID、 通道 ID 和其他有关视频信息。

```no-highlight
POST {VideoPortalURL}/_api/VideoService/GetVideoByURL?$Select=Title,Description,CreatedDate,DefaultEmbedCode,VideoDurationInSeconds,ID,VideoProcessingStatus
```

通过使用 $select 选项，您可以请求，返回视频项目的任何视频属性，包括标题和默认嵌入代码，如下所示。


**请求标头**

接受 = 应用程序/json; odata = 详细

内容类型 = 应用程序/json; odata = 详细


**请求正文**

{videoFileRelativeUrl: https: / /*root_SharePoint_site*/portals/hub/_layouts/15/PointPublishing.aspx?app=video & p = p & chid b74774cb-faad-43a0-8de9-cb263e38d75d & vid = = e5b66725-9f87-4813-9b50-b24fe80c9c20}

其中， **videoFileRelativeURL**是视频的 O365 视频门户播放页的相对或绝对 URL。

****

<a name="NextSteps"> </a>
## <a name="next-steps"></a>下一步行动

无论您是准备开始构建应用程序，或只是想要了解更多，我们有您的要求。


- 准备好开始了吗？ 首先[设置您的环境](..\howto\setup-development-environment.md)。

- 要使用这些 Api 的更多亲身体验？ 通过该[视频的 Api 的实践性实验室](http://dev.office.com/hands-on-labs/4589)工作。

或者，了解有关使用 Office 365 的平台︰

- [在 Office 365 的平台上开发](..\howto\platform-development-overview.md)

- [Office 365 应用程序身份验证](..\howto\common-app-authentication-tasks.md)

- [手动添加到 Office 365 提供应用程序的常见的同意](..\howto\add-common-consent-manually.md)

- [禁用或重新启用 Office 365 视频](https://support.office.com/en-us/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da#BKMK_Disabling)

- [日历的其他操作](..\api\calendar-rest-operations.md)

- [联系人的其他操作](..\api\contacts-rest-operations.md)

- [OneDrive API](https://dev.onedrive.com/)

- [发现服务其他操作](..\api\discovery-service-rest-operations.md)

- [邮件其余操作](..\api\mail-rest-operations.md)

- [OneDrive API](https://dev.onedrive.com/)

# <a name="user-findmeetingtimes"></a>用户︰ findMeetingTimes
查找会议时间的建议基于组织者和与会者的可用性，以及时间或地点指定为参数的约束。

如果**findMeetingTimes**不能返回任何会议的建议，响应将指示中**emptySuggestionsHint**属性的原因。 根据此值，您可以更好地调整参数并重新调用**findMeetingTimes** 。

**请注意**

目前， **findMeetingTimes**的假设如下︰

- 是个人 （而不是资源） 的任何[与会者](../resources/attendee.md)是必须出席的与会者。 因此，指定`required`人和`resource`为相应的**类型**属性，作为**与会者**集合参数的一部分中的资源。
- 仅组织者或与会者的工作时间内发生任何会议的建议。 您可以忽略指定[timeConstraint](../resources/timeConstraint.md)的**activityDomain**属性。 


## <a name="prerequisites"></a>先决条件
执行此 API 所需的以下**范围**︰ *Calendars.Read*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /me/findMeetingTimes
POST /users/<id|userPrincipalName>/findMeetingTimes
```
## <a name="request-headers"></a>请求标头
| 名称       | 值|
|:---------------|:----------|
| 授权  | 持有者<code>|
| 喜欢︰ outlook.timezone | 一个字符串，它表示特定时区的响应，例如，"太平洋标准时间"。 |


## <a name="request-body"></a>请求正文
下面列出了所有受支持的参数。 这取决于您的方案，每个请求主体中必要的参数指定一个 JSON 对象。 根据指定的参数，则**findMeetingTimes**检查中的主要组织者和与会者的日历的忙/闲状态。 该操作计算最佳会议时间，并返回任何会议的建议。


| 参数    | 类型   |说明|
|:---------------|:--------|:----------|
|与会者|[attendeeBase](../resources/attendeebase.md)集合|与会者或会议资源的集合。 空集合会导致**findMeetingTimes**查找可用时间段只有组织者。|
|locationConstraint|[locationConstraint](../resources/locationconstraint.md)|关于会议地点的组织者的要求，如会议地点有关的建议是否必需的或有特定的位置，只在其中可以召开会议。|
|timeConstraint|[timeConstraint](../resources/timeconstraint.md)|应会议开始和结束的时间范围。 您可以指定时区为此参数**start**和**end**属性的一部分。 但是，此时区影响仅**timeConstraint**参数;时间值返回响应，如果有的话，是仍在缺省 UTC。 您可以使用`Prefer: outlook.timezone`请求标头可以在响应中指定特定时区的时间值。 |
|meetingDuration|Edm.Duration|会议的长度表示[ISO8601](http://www.iso.org/iso/iso8601)格式。 例如，1 小时可表示为 PT1H，其中 P，是持续时间指示符，' T ' 是时间指示符，'H' 是小时指示符。 如果不指定任何会议持续时间，则**findMeetingTimes**将使用默认值为 30 分钟。 |
|maxCandidates|Edm.Int32|会议的最大数目时要返回的建议。|
|isOrganizerOptional|Edm.Boolean|`True`如果不需要，组织者的出勤`false`否则为。|
|returnSuggestionHints|Edm.Boolean|`True`在**suggestionHint**属性中返回每个会议的建议的原因。 默认值是`false`不能返回该属性。|

## <a name="response"></a>响应
如果成功，此方法返回`200, OK`响应代码和[meetingTimeCandidatesResult](../resources/meetingtimecandidatesresult.md)在响应正文中。 

**MeetingTimeCandidatesResult**包括会议建议和**emptySuggestionsHint**属性的集合。 每个建议被指[meetingTimeCandidate](../resources/meetingtimecandidate.md)，平均拥有信心，50%几率的级别或更高版本的与会者参加。 

默认情况下，每个会议时间的建议将以返回 UTC。 

## <a name="example"></a>示例

下面的示例演示如何查找时间，以满足在一个预先确定的位置，并请求原因的所有建议，通过在请求正文中指定以下参数︰

- **与会者**
- **locationConstraint**
- **timeConstraint**
- **meetingDuration**
- **returnSuggestionHints**

通过设置**returnSuggestionHints**参数，也获得在**suggestionHint**属性中的说明每个建议，如果**findMeetingTimes**返回的任何建议。

请注意该请求在太平洋标准时间时区和会议时间的建议以 UTC，默认情况下该响应返回指定的时间。 您可以使用`Prefer: outlook.timezone`请求标头，指定响应中的时间值以及太平洋标准时间。

##### <a name="request"></a>请求
下面是示例请求。
<!-- {
  "blockType": "request",
  "name": "user_findmeetingtimes"
}-->
```http
POST https://graph.microsoft.com/beta/me/findMeetingTimes


{ 
  "attendees": [ 
    { 
      "type": "required",  
      "emailAddress": { 
        "address": "alexd@contoso.onmicrosoft.com" 
      } 
    } 
  ],  
  "locationConstraint": { 
    "isRequired": "false",  
    "suggestLocation": "false",  
    "locations": [ 
      { 
        "displayName": "Conf room Hood" 
      } 
    ] 
  },  
  "timeConstraint": { 
    "timeslots": [ 
      { 
        "start": { 
          "date": "2016-06-20",  
          "time": "7:00:00",  
          "timeZone": "Pacific Standard Time" 
        },  
        "end": { 
          "date": "2016-06-20",  
          "time": "17:00:00",  
          "timeZone": "Pacific Standard Time" 
        } 
      } 
    ] 
  },  
  "meetingDuration": "PT2H",
  "returnSuggestionHints": "true"
}
```

##### <a name="response"></a>响应
下面是一个示例响应。 注意︰ 为了简单起见，此处所示的响应对象可能被截断。 从实际调用将返回的所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.meetingTimeCandidatesResult",
  "isCollection": false
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json


{
   "@odata.context":"https://graph.microsoft.com/beta/$metadata#microsoft.graph.meetingTimeCandidatesResult",
   "meetingTimeSlots":[
      {
         "meetingTimeSlot":{
            "start":{
               "date":"2016-06-20",
               "time":"15:00:00.0000000",
               "timeZone":"UTC"
            },
            "end":{
               "date":"2016-06-20",
               "time":"17:00:00.0000000",
               "timeZone":"UTC"
            }
         },
         "confidence":100,
         "organizerAvailability":"free",
         "attendeeAvailability":[
            {
               "attendee":{
                  "type":"required",
                  "emailAddress":{
                     "address":"alexd@contoso.onmicrosoft.com"
                  }
               },
               "availability":"free"
            }
         ],
         "locations":[
            {
               "displayName":"Conf room Hood"
            }
         ],
         "suggestionHint":"Suggested because it is one of the nearest times when all attendees are available."
      },
      {
         "meetingTimeSlot":{
            "start":{
               "date":"2016-06-20",
               "time":"17:00:00.0000000",
               "timeZone":"UTC"
            },
            "end":{
               "date":"2016-06-20",
               "time":"19:00:00.0000000",
               "timeZone":"UTC"
            }
         },
         "confidence":100,
         "organizerAvailability":"free",
         "attendeeAvailability":[
            {
               "attendee":{
                  "type":"required",
                  "emailAddress":{
                     "address":"alexd@contoso.onmicrosoft.com"
                  }
               },
               "availability":"free"
            }
         ],
         "locations":[
            {
               "displayName":"Conf room Hood"
            }
         ],
         "suggestionHint":"Suggested because it is one of the nearest times when all attendees are available."
      }
   ],
   "emptySuggestionsHint":""
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "user: findMeetingTimes",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
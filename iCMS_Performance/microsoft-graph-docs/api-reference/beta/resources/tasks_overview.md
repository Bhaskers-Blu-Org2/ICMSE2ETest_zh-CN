# <a name="groups-plans-and-tasks"></a>组、 计划和任务
新的 Office 365 任务 API 使您能够创建任务并将其分配给 Office 365 中的某个组中的用户。

## <a name="basics"></a>基础知识
着手试验任务 API 之前，有必要了解任务 API 中的主要对象与彼此以及 Office 365 组。

## <a name="groups"></a>组
Office 365 组是在 API 中的任务的计划的负责人。
如今，每个组可以拥有不超过一个计划。
若要将组拥有的计划，使下面的 HTTP 请求。

```http
GET /groups/<id>/plans
```
当创建新的计划，需要通过简单地设置使一组其所有者`owner`计划对象如果组不拥有一个计划一个组对象的 id 属性。 

**请注意，您需要确保已创建计划的用户组的成员。当您创建新的组使用 API 时，您都不自动添加到组成员身份。这已可使用不同的 API 调用。** 

## <a name="plans"></a>计划
计划是任务的容器。 若要在组中创建一个任务，将`planId`为该计划的 id 任务对象上对象归组。
若要检索计划中的任务，使下面的 HTTP 请求。

```http
GET /plans/<id>/tasks
```
每个计划还有计划详细信息对象以及计划的对象创建的。 若要访问计划的详细信息的对象，使下面的 HTTP 请求。

```http
GET /plans/<id>/details
```

## <a name="tasks"></a>任务
每个任务可以分配给用户通过设置`assignedTo`在任务对象的用户对象的 id 属性。 它还具有一个任务详细信息对象以及任务的对象创建的。 若要访问此任务的详细信息，请进行下面的 HTTP 请求。

```http
GET /tasks/<id>/details
```

## <a name="api-reference"></a>API 参考
在左侧的链接显示在任务 API 提供的对象。 每个对象的页面链接包含的属性、 关系和对象上的方法的说明。
探讨在左侧以了解详细信息链接。
# <a name="manage-focused-inbox"></a>管理重点的收件箱

重点收件箱，您可以查看重要的消息，在`Focused`的收件箱和收件箱中的邮件的其他选项卡`Other`选项卡。 分类系统最初组织收件箱邮件中的默认方式。 您可以更正，然后随时间通过用户界面或通过编程方式训练系统。 您使用的越多，系统可以更好地推断为重要的传入消息。

级别的编程专注于收件箱 REST API，致力于指定的用户的邮件，并支持为每个消息的**inferenceClassification**属性。 可能的值为`Focused`， `Other`，它指示是否用户认为该消息一样，分别更重要的是，并不太重要。 若要更正系统如何对邮件，[更新该消息的 inferenceClassification 属性](../api/message_update.md)进行分类。 随着时间的推移这些更正还训练邮件分类系统。

专注于收件箱 REST API 还允许您创建重写。 由[inferenceClassificationOverride](../resources/inferenceClassificationOverride.md)实例，每个重写是始终将来自特定发件人的邮件指定以一致的方式 （即，始终作为"焦点"或始终为"其他"），而不考虑任何以前学习方法的分类系统的指令。 您可以[创建](../api/inferenceclassification_post_overrides.md)、[列表](../api/inferenceclassification_list_overrides.md)、[更新](../api/inferenceclassificationoverride_update.md)和[删除](../api/inferenceclassificationoverride_delete.md)指定的用户重写。 该用户的覆盖，如果有的话，都可以访问**inferenceClassification**导航属性，它是**inferenceClassificationOverride**实例的集合中。 替代允许用户更好地控制接收的邮件，分类和生成更高信任度的分类系统。

注意分类系统学习并应用分类只对传入的邮件在收件箱中。 其他文件夹中的邮件在默认情况下，"焦点"。 重写设置会影响将来邮件到达收件箱;重写并不修改任何文件夹包括收件箱中的现有邮件中的**inferenceClassification**属性。

## <a name="focused-inbox-api"></a>具有焦点的收件箱 API

**邮件分类系统的培训**

[更新消息的 inferenceClassification 属性](../api/message_update.md)


**使用重写每个发件人以一致的方式分类**

[创建发件人重写](../api/inferenceclassification_post_overrides.md) | [列出所有用户重写](../api/inferenceclassification_list_overrides.md) | 
[更新发件人重写](../api/inferenceclassificationoverride_update.md) | [删除发件人重写](../api/inferenceclassificationoverride_delete.md) 

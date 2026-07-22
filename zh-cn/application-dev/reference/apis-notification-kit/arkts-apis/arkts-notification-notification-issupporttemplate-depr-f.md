# isSupportTemplate

## isSupportTemplate

```TypeScript
function isSupportTemplate(templateName: string, callback: AsyncCallback<boolean>): void
```

在使用[通知模板](arkts-notification-notificationtemplate-notificationtemplate-i.md)发布通知前，可以通过该接口查询是否支持对应的通知模板。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** isSupportTemplate

<!--Device-notification-function isSupportTemplate(templateName: string, callback: AsyncCallback<boolean>): void--><!--Device-notification-function isSupportTemplate(templateName: string, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| templateName | string | 是 | 模板名称。当前仅支持'downloadTemplate'。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 查询模板是否存在的回调函数。 |


## isSupportTemplate

```TypeScript
function isSupportTemplate(templateName: string): Promise<boolean>
```

在使用[通知模板](arkts-notification-notificationtemplate-notificationtemplate-i.md)发布通知前，可以通过该接口查询是否支持对应的通知模板。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** isSupportTemplate

<!--Device-notification-function isSupportTemplate(templateName: string): Promise<boolean>--><!--Device-notification-function isSupportTemplate(templateName: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.Notification.Notification

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| templateName | string | 是 | 模板名称。当前仅支持'downloadTemplate'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise方式返回模板是否存在的结果。 |


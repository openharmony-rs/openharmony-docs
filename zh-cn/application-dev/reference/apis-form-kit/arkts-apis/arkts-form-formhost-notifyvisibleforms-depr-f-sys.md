# notifyVisibleForms（系统接口）

## 导入模块

```TypeScript
```

## notifyVisibleForms

```TypeScript
function notifyVisibleForms(formIds: Array<string>, callback: AsyncCallback<void>): void
```

向卡片框架发送通知以使指定的卡片可见。该方法调用成功后，会调用onVisibilityChange通知卡片提供方。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [notifyVisibleForms](arkts-form-formhost-notifyvisibleforms-f-sys.md)

**需要权限：** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function notifyVisibleForms(formIds: Array<string>, callback: AsyncCallback<void>): void--><!--Device-formHost-function notifyVisibleForms(formIds: Array<string>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | 是 | 卡片标识列表。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当向卡片框架发送通知以使指定的卡片可见成功，error为undefined，否则为错误对象。 |


## notifyVisibleForms

```TypeScript
function notifyVisibleForms(formIds: Array<string>): Promise<void>
```

向卡片框架发送通知以使指定的卡片可见。该方法调用成功后，会调用onVisibilityChange通知卡片提供方。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [notifyVisibleForms](arkts-form-formhost-notifyvisibleforms-f-sys.md)

**需要权限：** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function notifyVisibleForms(formIds: Array<string>): Promise<void>--><!--Device-formHost-function notifyVisibleForms(formIds: Array<string>): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | 是 | 卡片标识列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |


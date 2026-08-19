# notifyFormsEnableUpdate（系统接口）

## 导入模块

```TypeScript
```

## notifyFormsEnableUpdate

```TypeScript
function notifyFormsEnableUpdate(
    formIds: Array<string>,
    isEnableUpdate: boolean,
    callback: AsyncCallback<void>
  ): void
```

通知卡片是否启用更新状态。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [notifyFormsEnableUpdate](arkts-form-formhost-notifyformsenableupdate-f-sys.md)

**需要权限：** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function notifyFormsEnableUpdate(    formIds: Array<string>,    isEnableUpdate: boolean,    callback: AsyncCallback<void>  ): void--><!--Device-formHost-function notifyFormsEnableUpdate(    formIds: Array<string>,    isEnableUpdate: boolean,    callback: AsyncCallback<void>  ): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | 是 | 卡片标识列表。 |
| isEnableUpdate | boolean | 是 | 是否使能更新。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当通知卡片是否启用更新状态成功，error为undefined，否则为错误对象。 |


## notifyFormsEnableUpdate

```TypeScript
function notifyFormsEnableUpdate(formIds: Array<string>, isEnableUpdate: boolean): Promise<void>
```

通知卡片是否启用更新状态。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [notifyFormsEnableUpdate](arkts-form-formhost-notifyformsenableupdate-f-sys.md)

**需要权限：** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function notifyFormsEnableUpdate(formIds: Array<string>, isEnableUpdate: boolean): Promise<void>--><!--Device-formHost-function notifyFormsEnableUpdate(formIds: Array<string>, isEnableUpdate: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | 是 | 卡片标识列表。 |
| isEnableUpdate | boolean | 是 | 是否使能更新。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |


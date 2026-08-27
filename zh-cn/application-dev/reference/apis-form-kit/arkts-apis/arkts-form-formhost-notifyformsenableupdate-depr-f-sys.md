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

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array & lt;string & gt; | 是 | 卡片标识列表。 |
| isEnableUpdate | boolean | 是 | 是否使能更新。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当通知卡片是否启用更新状态成功，error为undefined，否则为错误对象。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let formIds: string[] = new Array('12400633174999288', '12400633174999289');
formHost.notifyFormsEnableUpdate(formIds, true, (error: Base.BusinessError) => {
  if (error.code) {
    console.error(`formHost notifyFormsEnableUpdate, error: ${JSON.stringify(error)}`);
  }
});
```


## notifyFormsEnableUpdate

```TypeScript
function notifyFormsEnableUpdate(formIds: Array<string>, isEnableUpdate: boolean): Promise<void>
```

通知卡片是否启用更新状态。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [notifyFormsEnableUpdate](arkts-form-formhost-notifyformsenableupdate-f-sys.md)

**需要权限：** ohos.permission.REQUIRE_FORM

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array & lt;string & gt; | 是 | 卡片标识列表。 |
| isEnableUpdate | boolean | 是 | 是否使能更新。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 无返回结果的Promise对象。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let formIds: string[] = new Array('12400633174999288', '12400633174999289');
formHost.notifyFormsEnableUpdate(formIds, true).then(() => {
  console.info('formHost notifyFormsEnableUpdate success');
}).catch((error: Base.BusinessError) => {
  console.error(`formHost notifyFormsEnableUpdate, error: ${JSON.stringify(error)}`);
});
```

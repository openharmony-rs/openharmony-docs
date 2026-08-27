# enableFormsUpdate（系统接口）

## 导入模块

```TypeScript
```

## enableFormsUpdate

```TypeScript
function enableFormsUpdate(formIds: Array<string>, callback: AsyncCallback<void>): void
```

向卡片框架发送通知以使指定的卡片可以更新。该方法调用成功后，卡片刷新状态设置为使能，卡片可以接收来自卡片提供方的更新。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [enableFormsUpdate](arkts-form-formhost-enableformsupdate-f-sys.md)

**需要权限：** ohos.permission.REQUIRE_FORM

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array & lt;string & gt; | 是 | 卡片标识列表。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当向卡片框架发送通知以使指定的卡片可以更新成功，error为undefined，否则为错误对象。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let formIds: string[] = ['12400633174999288'];
formHost.enableFormsUpdate(formIds, (error: Base.BusinessError) => {
  if (error.code) {
    console.error(`formHost enableFormsUpdate, error: ${JSON.stringify(error)}`);
  }
});
```


## enableFormsUpdate

```TypeScript
function enableFormsUpdate(formIds: Array<string>): Promise<void>
```

向卡片框架发送通知以使指定的卡片可以更新。该方法调用成功后，卡片刷新状态设置为使能，卡片可以接收来自卡片提供方的更新。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [enableFormsUpdate](arkts-form-formhost-enableformsupdate-f-sys.md)

**需要权限：** ohos.permission.REQUIRE_FORM

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array & lt;string & gt; | 是 | 卡片标识列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 无返回结果的Promise对象。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let formIds: string[] = ['12400633174999288'];
formHost.enableFormsUpdate(formIds).then(() => {
  console.info('formHost enableFormsUpdate success');
}).catch((error: Base.BusinessError) => {
  console.error(`formHost enableFormsUpdate, error: ${JSON.stringify(error)}`);
});
```

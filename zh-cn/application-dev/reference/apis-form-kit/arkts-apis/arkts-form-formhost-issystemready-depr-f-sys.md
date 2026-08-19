# isSystemReady（系统接口）

## 导入模块

```TypeScript
```

## isSystemReady

```TypeScript
function isSystemReady(callback: AsyncCallback<void>): void
```

检查系统是否准备好。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isSystemReady](arkts-form-formhost-issystemready-f-sys.md)

<!--Device-formHost-function isSystemReady(callback: AsyncCallback<void>): void--><!--Device-formHost-function isSystemReady(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当检查系统是否准备好成功，error为undefined，否则为错误对象。 |


## isSystemReady

```TypeScript
function isSystemReady(): Promise<void>
```

检查系统是否准备好。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [isSystemReady](arkts-form-formhost-issystemready-f-sys.md)

<!--Device-formHost-function isSystemReady(): Promise<void>--><!--Device-formHost-function isSystemReady(): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |


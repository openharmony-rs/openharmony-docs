# requestForm（系统接口）

## 导入模块

```TypeScript
```

## requestForm

```TypeScript
function requestForm(formId: string, callback: AsyncCallback<void>): void
```

请求卡片更新。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [requestForm](arkts-form-formhost-requestform-f-sys.md)

**需要权限：** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function requestForm(formId: string, callback: AsyncCallback<void>): void--><!--Device-formHost-function requestForm(formId: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片标识。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当请求卡片更新成功，error为undefined；否则为错误对象。 |


## requestForm

```TypeScript
function requestForm(formId: string): Promise<void>
```

请求卡片更新。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [requestForm](arkts-form-formhost-requestform-f-sys.md)

**需要权限：** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function requestForm(formId: string): Promise<void>--><!--Device-formHost-function requestForm(formId: string): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |


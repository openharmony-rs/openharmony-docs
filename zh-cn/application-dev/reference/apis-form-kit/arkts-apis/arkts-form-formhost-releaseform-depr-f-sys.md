# releaseForm（系统接口）

## 导入模块

```TypeScript
```

## releaseForm

```TypeScript
function releaseForm(formId: string, callback: AsyncCallback<void>): void
```

释放指定的卡片。调用此方法后，应用程序将无法使用该卡片，但卡片管理器服务仍然保留有关该卡片的缓存信息和存储信息。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [releaseForm](arkts-form-formhost-releaseform-f-sys.md)

**需要权限：** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function releaseForm(formId: string, callback: AsyncCallback<void>): void--><!--Device-formHost-function releaseForm(formId: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片标识。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当释放指定的卡片成功，error为undefined；否则为错误对象。 |


## releaseForm

```TypeScript
function releaseForm(formId: string, isReleaseCache: boolean, callback: AsyncCallback<void>): void
```

释放指定的卡片。调用此方法后，应用程序将无法使用该卡片，卡片管理器服务保留有关该卡片的存储信息，可以选择是否保留缓存信息。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [releaseForm](arkts-form-formhost-releaseform-f-sys.md)

**需要权限：** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function releaseForm(formId: string, isReleaseCache: boolean, callback: AsyncCallback<void>): void--><!--Device-formHost-function releaseForm(formId: string, isReleaseCache: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片标识。 |
| isReleaseCache | boolean | 是 | 是否释放缓存。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当释放指定的卡片成功，error为undefined；否则为错误对象。 |


## releaseForm

```TypeScript
function releaseForm(formId: string, isReleaseCache?: boolean): Promise<void>
```

释放指定的卡片。调用此方法后，应用程序将无法使用该卡片，卡片管理器服务保留有关该卡片的存储信息，可以选择是否保留缓存信息。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [releaseForm](arkts-form-formhost-releaseform-f-sys.md)

**需要权限：** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function releaseForm(formId: string, isReleaseCache?: boolean): Promise<void>--><!--Device-formHost-function releaseForm(formId: string, isReleaseCache?: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片标识。 |
| isReleaseCache | boolean | 否 | 是否释放缓存，默认为false。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |


# deleteInvalidForms（系统接口）

## 导入模块

```TypeScript
```

## deleteInvalidForms

```TypeScript
function deleteInvalidForms(formIds: Array<string>, callback: AsyncCallback<number>): void
```

根据列表删除应用程序的无效卡片。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [deleteInvalidForms](arkts-form-formhost-deleteinvalidforms-f-sys.md)

**需要权限：** ohos.permission.REQUIRE_FORM

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array & lt;string & gt; | 是 | 有效卡片标识列表。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当根据列表删除应用程序的无效卡片成功，error为undefined，data为删除的卡片个数；否则为错误对象。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let formIds: string[] = new Array('12400633174999288', '12400633174999289');
formHost.deleteInvalidForms(formIds, (error: Base.BusinessError, data: number) => {
  if (error.code) {
    console.error(`formHost deleteInvalidForms, error: ${JSON.stringify(error)}`);
  } else {
    console.info(`formHost deleteInvalidForms, data: ${JSON.stringify(data)}`);
  }
});
```


## deleteInvalidForms

```TypeScript
function deleteInvalidForms(formIds: Array<string>): Promise<number>
```

根据列表删除应用程序的无效卡片。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [deleteInvalidForms](arkts-form-formhost-deleteinvalidforms-f-sys.md)

**需要权限：** ohos.permission.REQUIRE_FORM

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formIds | Array & lt;string & gt; | 是 | 有效卡片标识列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象。返回删除的卡片个数。 |

**示例**

```TypeScript
import Base from '@ohos.base';

let formIds: string[] = new Array('12400633174999288', '12400633174999289');
formHost.deleteInvalidForms(formIds).then((data: number) => {
  console.info(`formHost deleteInvalidForms, data: ${JSON.stringify(data)}`);
}).catch((error: Base.BusinessError) => {
  console.error(`formHost deleteInvalidForms, error: ${JSON.stringify(error)}`);
});
```

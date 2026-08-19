# updateForm

## 导入模块

```TypeScript
```

## updateForm

```TypeScript
function updateForm(
    formId: string,
    formBindingData: formBindingData.FormBindingData,
    callback: AsyncCallback<void>
  ): void
```

更新指定的卡片，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [updateForm](arkts-form-formprovider-updateform-f.md)

<!--Device-formProvider-function updateForm(    formId: string,    formBindingData: formBindingData.FormBindingData,    callback: AsyncCallback<void>  ): void--><!--Device-formProvider-function updateForm(    formId: string,    formBindingData: formBindingData.FormBindingData,    callback: AsyncCallback<void>  ): void-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 请求更新的卡片标识。 |
| formBindingData | formBindingData.FormBindingData | 是 | 用于更新的数据。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { formProvider, formBindingData } from '@kit.FormKit';

// 使用时需要用已经存在formId
let formId: string = '12400633174999288';
let param: Record<string, string> = {
  'temperature': '22c',
  'time': '22:00'
}
let obj: formBindingData.FormBindingData = formBindingData.createFormBindingData(param);
formProvider.updateForm(formId, obj, (error: BusinessError) => {
  if (error.code) {
    console.error(`formProvider updateForm, errorCode: ${error.code}, errorMessage: ${error.message}`);
  }
});
```


## updateForm

```TypeScript
function updateForm(formId: string, formBindingData: formBindingData.FormBindingData): Promise<void>
```

更新指定的卡片，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [updateForm](arkts-form-formprovider-updateform-f.md)

<!--Device-formProvider-function updateForm(formId: string, formBindingData: formBindingData.FormBindingData): Promise<void>--><!--Device-formProvider-function updateForm(formId: string, formBindingData: formBindingData.FormBindingData): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 请求更新的卡片标识。 |
| formBindingData | formBindingData.FormBindingData | 是 | 用于更新的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { formProvider, formBindingData } from '@kit.FormKit';

// 使用时需要用已经存在formId
let formId: string = '12400633174999288';
let param: Record<string, string> = {
  'temperature': '22c',
  'time': '22:00'
}
let obj: formBindingData.FormBindingData = formBindingData.createFormBindingData(param);
formProvider.updateForm(formId, obj).then(() => {
  console.info('formProvider updateForm success');
}).catch((error: BusinessError) => {
  console.error(`formProvider updateForm, errorCode: ${error.code}, errorMessage: ${error.message}`);
});
```


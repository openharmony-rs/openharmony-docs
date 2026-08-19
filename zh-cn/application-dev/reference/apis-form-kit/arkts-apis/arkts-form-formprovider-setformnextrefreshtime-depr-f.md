# setFormNextRefreshTime

## 导入模块

```TypeScript
```

## setFormNextRefreshTime

```TypeScript
function setFormNextRefreshTime(formId: string, minute: number, callback: AsyncCallback<void>): void
```

设置指定卡片的下一次刷新时间，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [setFormNextRefreshTime](arkts-form-formprovider-setformnextrefreshtime-f.md)

<!--Device-formProvider-function setFormNextRefreshTime(formId: string, minute: number, callback: AsyncCallback<void>): void--><!--Device-formProvider-function setFormNextRefreshTime(formId: string, minute: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片标识。 |
| minute | number | 是 | 指定多久之后刷新。单位分钟，大于等于5。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { formProvider } from '@kit.FormKit';
// 使用时需要用已经存在formId
let formId: string = '12400633174999288';
formProvider.setFormNextRefreshTime(formId, 5, (error: BusinessError) => {
  if (error.code) {
    console.error(`formProvider setFormNextRefreshTime, errorCode: ${error.code}, errorMessage: ${error.message}`);
  }
});
```


## setFormNextRefreshTime

```TypeScript
function setFormNextRefreshTime(formId: string, minute: number): Promise<void>
```

设置指定卡片的下一次刷新时间，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [setFormNextRefreshTime](arkts-form-formprovider-setformnextrefreshtime-f.md)

<!--Device-formProvider-function setFormNextRefreshTime(formId: string, minute: number): Promise<void>--><!--Device-formProvider-function setFormNextRefreshTime(formId: string, minute: number): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片标识。 |
| minute | number | 是 | 指定多久之后刷新。单位分钟，大于等于5。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { formProvider } from '@kit.FormKit';
// 使用时需要用已经存在formId
let formId: string = '12400633174999288';
formProvider.setFormNextRefreshTime(formId, 5).then(() => {
  console.info('formProvider setFormNextRefreshTime success');
}).catch((error: BusinessError) => {
  console.error(`formProvider setFormNextRefreshTime, errorCode: ${error.code}, errorMessage: ${error.message}`);
});
```


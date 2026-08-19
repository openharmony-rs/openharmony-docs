# getPublishedFormInfoById

## 导入模块

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## getPublishedFormInfoById

```TypeScript
function getPublishedFormInfoById(formId: string): Promise<formInfo.FormInfo>
```

获取设备上当前应用程序已添加到桌面的指定卡片信息，使用Promise异步回调。

**起始版本：** 18

**废弃版本：** 20

**替代接口：** [getPublishedRunningFormInfoById](arkts-form-formprovider-getpublishedrunningforminfobyid-f.md)

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-formProvider-function getPublishedFormInfoById(formId: string): Promise<formInfo.FormInfo>--><!--Device-formProvider-function getPublishedFormInfoById(formId: string): Promise<formInfo.FormInfo>-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;formInfo.FormInfo&gt; | Promise对象。返回查询到符合条件的卡片信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |

**示例**

```TypeScript
import { formInfo, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

const formId: string = '388344236';
try {
  formProvider.getPublishedFormInfoById(formId).then((data: formInfo.FormInfo) => {
    console.info(`formProvider getPublishedFormInfoById, data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```


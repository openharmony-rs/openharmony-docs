# getPublishedFormInfos

## 导入模块

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## getPublishedFormInfos

```TypeScript
function getPublishedFormInfos(): Promise<Array<formInfo.FormInfo>>
```

获取设备上当前应用所有已添加到桌面的卡片信息，使用Promise异步回调。

**起始版本：** 18

**废弃版本：** 20

**替代接口：** [getPublishedRunningFormInfos](arkts-form-formprovider-getpublishedrunningforminfos-f.md)

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-formProvider-function getPublishedFormInfos(): Promise<Array<formInfo.FormInfo>>--><!--Device-formProvider-function getPublishedFormInfos(): Promise<Array<formInfo.FormInfo>>-End-->

**系统能力：** SystemCapability.Ability.Form

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;formInfo.FormInfo&gt;&gt; | Promise对象。返回查询到符合条件的卡片信息。 |

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

try {
  formProvider.getPublishedFormInfos().then((data: formInfo.FormInfo[]) => {
    console.info(`formProvider getPublishedFormInfos, data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```


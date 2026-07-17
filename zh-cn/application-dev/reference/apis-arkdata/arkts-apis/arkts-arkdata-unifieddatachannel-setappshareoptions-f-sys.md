# setAppShareOptions（系统接口）

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## setAppShareOptions

```TypeScript
function setAppShareOptions(intention: Intention, shareOptions: ShareOptions): void
```

设置应用内拖拽通道数据可使用的范围[ShareOptions](arkts-arkdata-unifieddatachannel-shareoptions-e.md)，目前仅支持DRAG类型数据通道的管控设置。调用成功后，应用内拖拽通道数据的使用范围被设置为指定的ShareOptions值。

**起始版本：** 14

**需要权限：** 
- API版本14+：ohos.permission.MANAGE_UDMF_APP_SHARE_OPTION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unifiedDataChannel-function setAppShareOptions(intention: Intention, shareOptions: ShareOptions): void--><!--Device-unifiedDataChannel-function setAppShareOptions(intention: Intention, shareOptions: ShareOptions): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| intention | [Intention](arkts-arkdata-unifieddatachannel-intention-e-sys.md) | 是 | 表示数据操作相关的数据通路类型，目前仅支持DRAG类型数据通道。 |
| shareOptions | [ShareOptions](arkts-arkdata-unifieddatachannel-shareoptions-e.md) | 是 | 指示[UnifiedData](arkts-arkdata-unifieddatachannel-unifieddata-c.md)支持的设备内使用范围。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API.<br>**适用版本：** 12 - 13 |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [20400001](../errorcode-udmf.md#20400001-设置已存在若要重新配置请删除现有的共享选项) | Settings already exist. To reconfigure, remove the existing sharing options. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission "ohos.permission.MANAGE_UDMF_APP_SHARE_OPTION".<br>**适用版本：** 14+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  unifiedDataChannel.setAppShareOptions(unifiedDataChannel.Intention.DRAG, unifiedDataChannel.ShareOptions.IN_APP);
  console.info(`[UDMF]setAppShareOptions success.`);
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`[UDMF]setAppShareOptions throws an exception. code is ${error.code}, message is ${error.message}`);
}

```


# setAppShareOptions

## setAppShareOptions

```TypeScript
function setAppShareOptions(intention: Intention, shareOptions: ShareOptions): void
```

设置应用内拖拽通道数据可使用的范围[ShareOptions]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_，目前仅支持DRAG类型数据通道的管控设置。调用成功后，应用内拖拽通道数据的使用范围被设 置为指定的ShareOptions值。

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**需要权限：** 
- API版本14+：ohos.permission.MANAGE_UDMF_APP_SHARE_OPTION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unifiedDataChannel-function setAppShareOptions(intention: Intention, shareOptions: ShareOptions): void--><!--Device-unifiedDataChannel-function setAppShareOptions(intention: Intention, shareOptions: ShareOptions): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| intention | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 表示数据操作相关的数据通路类型，目前仅支持DRAG类型数据通道。 |
| shareOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指示[UnifiedData]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_支持的设备内使用范围。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12 - 13 |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types;3. Parameter verification failed. |
| [20400001](../errorcode-udmf.md#20400001-设置已存在若要重新配置请删除现有的共享选项) | Settings already exist. To reconfigure, remove the existing sharing options. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission "ohos.permission.MANAGE\_\_\_ESCAPED\_UNDERSCORE\_\_\_UDMF\_\_\_ESCAPED\_UNDERSCORE\_\_\_APP\_\_\_ESCAPED\_UNDERSCORE\_\_\_SHARE\_\_\_ESCAPED\_UNDERSCORE\_\_\_OPTION".\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 14+ |

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


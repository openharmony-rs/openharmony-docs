# grantUriPermissionByKey（系统接口）

## grantUriPermissionByKey

```TypeScript
function grantUriPermissionByKey(key: string, flag: wantConstant.Flags, targetTokenId: number): Promise<void>
```

通过UDMF数据唯一标识key，将当前应用的文件URI访问权限授权给目标应用，权限将在目标应用退出后回收。使用Promise异步回调。
该接口仅在Phone、PC/2in1、Tablet设备中可正常调用，在其他设备中返回801错误码。
**系统接口**：此接口为系统接口。

**起始版本：** 20

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 目标UDMF数据唯一标识。key必须由调用方通过[unifiedDataChannel.insertData](@ohos.data.unifiedDataChannel:unifiedDataChannel.insertData(options: Options, data: UnifiedData, callback: AsyncCallback&lt;string&gt;))创建，且写入的数据均为有权限授权的文件URI。<br>当前仅支持SYSTEM_SHARE、PICKER和MENU类型的[UDMF数据通路](@ohos.data.unifiedDataChannel:unifiedDataChannel.Intention)的key。key的创建与使用方法详见[标准化数据通路实现数据共享](../../../../database/unified-data-channels.md)。 |
| flag | wantConstant.Flags | 是 | URI的读权限或写权限。支持的取值如下：<br>- FLAG_AUTH_READ_URI_PERMISSION：读权限。<br>-FLAG_AUTH_WRITE_URI_PERMISSION：写权限。 |
| targetTokenId | number | 是 | 目标应用的身份标识，可以通过[bundleManager.getApplicationInfo](arkts-ability-getapplicationinfo-f-sys.md#getapplicationinfo-2)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [16000058](../errorcode-ability.md#16000058-指定的uri-flag无效) | Invalid URI flag. |
| [16000060](../errorcode-ability.md#16000060-不支持沙箱应用授权uri) | A sandbox application cannot grant URI permission. |
| [16000091](../errorcode-ability.md#16000091-根据key获取文件uri数据失败) | Failed to get the file URI from the key. |
| [16000092](../errorcode-ability.md#16000092-无权限授权uri) | No permission to authorize the URI. |
| [16000094](../errorcode-ability.md#16000094-目标应用的token-id无效) | The target token ID is invalid. |

**示例：**

```TypeScript
// 接口调用方应用包名为com.example.test
// EntryAbility.ets
import { AbilityConstant, UIAbility, Want, wantConstant, uriPermissionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
  }

  onForeground(): void {
    try {
      // 可以通过unifiedDataChannel.insertData生成key
      let key: string = 'udmf://SystemShare/com.example.test/ap\\t5kKMYTOSHBh9\\f1@817VnBBvxI[e';
      // 可以通过bundleManager.getApplicationInfo接口获取targetTokenId
      // 假设获取的targetTokenId为1001
      let targetTokenId: number = 1001;
      uriPermissionManager.grantUriPermissionByKey(key,
        wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION, targetTokenId)
        .then(() => {
          console.info('grantUriPermissionByKey succeeded.');
        }).catch((error: BusinessError) => {
        console.error('grantUriPermissionByKey failed: ' + JSON.stringify(error));
      });
    } catch (error) {
      console.error('grantUriPermissionByKey failed: ' + JSON.stringify(error));
    }
  }
}

```


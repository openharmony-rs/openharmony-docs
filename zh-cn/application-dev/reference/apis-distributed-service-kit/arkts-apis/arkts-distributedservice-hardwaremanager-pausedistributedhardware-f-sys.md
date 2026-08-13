# pauseDistributedHardware（系统接口）

## pauseDistributedHardware

```TypeScript
function pauseDistributedHardware(description: HardwareDescriptor): Promise<void>
```

暂停被控端分布式硬件业务。使用promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.ACCESS_DISTRIBUTED_HARDWARE

<!--Device-hardwareManager-function pauseDistributedHardware(description: HardwareDescriptor): Promise<void>--><!--Device-hardwareManager-function pauseDistributedHardware(description: HardwareDescriptor): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedHardware.DistributedHardwareFWK

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| description | [HardwareDescriptor](arkts-distributedservice-hardwaremanager-hardwaredescriptor-i-sys.md) | 是 | 硬件描述信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Input parameter error. |
| 24200101 | The specified distributed hardware is not started. |
| 24200102 | The specified source device is not connected. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

## 示例

```TypeScript
import { hardwareManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let description: hardwareManager.HardwareDescriptor = {
    type: 1, // 分布式硬件类型，1表示相机
    srcNetworkId: '1111' // 源端设备网络ID
  };
  hardwareManager.pauseDistributedHardware(description).then(() => { // 暂停分布式硬件业务
    console.info('pause distributed hardware successfully');
  }).catch((error: BusinessError) => {
    console.error(`pause distributed hardware failed, cause: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`pause distributed hardware failed, code: ${err.code}, message: ${err.message}`);
}
```


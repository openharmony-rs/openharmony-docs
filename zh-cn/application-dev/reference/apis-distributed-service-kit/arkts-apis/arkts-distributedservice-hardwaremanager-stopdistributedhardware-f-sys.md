# stopDistributedHardware（系统接口）

## 导入模块

```TypeScript
import { hardwareManager } from '@kit.DistributedServiceKit';
```

## stopDistributedHardware

```TypeScript
function stopDistributedHardware(description: HardwareDescriptor): Promise<void>
```

停止被控端分布式硬件业务。被控端对应的分布式硬件业务停止。使用promise异步回调。停止后无法通过resumeDistributedHardware恢复业务，需要重新启动分布式硬件服务，不能再调用pauseDistributedHardware或resumeDistributedHardware。调用此方法前需确保分布式硬件已启动。使用场景：当应用退出或不再需要分布式硬件功能时；当用户主动关闭分布式硬件服务时；当设备断开连接需要释放分布式硬件资源时。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_DISTRIBUTED_HARDWARE

<!--Device-hardwareManager-function stopDistributedHardware(description: HardwareDescriptor): Promise<void>--><!--Device-hardwareManager-function stopDistributedHardware(description: HardwareDescriptor): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedHardware.DistributedHardwareFWK

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| description | [HardwareDescriptor](arkts-distributedservice-hardwaremanager-hardwaredescriptor-i-sys.md) | 是 | 硬件描述信息，用于指定要操作的分布式硬件类型和源端设备。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，异步操作成功时无返回结果，失败时返回错误码和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Input parameter error. |
| 24200101 | The specified distributed hardware is not started. |
| 24200102 | The specified source device is not connected. |

<!--Del-->
**示例**

```TypeScript
import { hardwareManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let description: hardwareManager.HardwareDescriptor = {
    type: 1,  // 分布式硬件类型，1表示相机
    srcNetworkId: '1111' // 源端设备网络ID
  };
  hardwareManager.stopDistributedHardware(description).then(() => { // 停止分布式硬件业务
    console.info('stop distributed hardware successfully');
  }).catch((error: BusinessError) => {
    console.error(`stop distributed hardware failed, cause: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`stop distributed hardware failed, code: ${err.code}, message: ${err.message}`);
}
```

<!--DelEnd-->

# pauseDistributedHardware（系统接口）

## 导入模块

```TypeScript
import { hardwareManager } from '@kit.DistributedServiceKit';
```

## pauseDistributedHardware

```TypeScript
function pauseDistributedHardware(description: HardwareDescriptor): Promise<void>
```

暂停被控端分布式硬件业务。被控端指通过分布式能力连接的远端设备，分布式硬件业务指通过分布式能力调用的相机、麦克风等硬件功能。使用promise异步回调，暂停后可以调用resumeDistributedHardware恢复业务或stopDistributedHardware停止业务。调用此方法前需确保分布式硬件已启动。使用场景：在多设备协同场景下临时暂停某些设备的硬件功能（如暂停远端相机以节省带宽）；当系统资源紧张时暂停非关键的分布式硬件以释放资源；切换设备配置时暂时停止当前硬件同步。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_DISTRIBUTED_HARDWARE

<!--Device-hardwareManager-function pauseDistributedHardware(description: HardwareDescriptor): Promise<void>--><!--Device-hardwareManager-function pauseDistributedHardware(description: HardwareDescriptor): Promise<void>-End-->

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

<!--DelEnd-->

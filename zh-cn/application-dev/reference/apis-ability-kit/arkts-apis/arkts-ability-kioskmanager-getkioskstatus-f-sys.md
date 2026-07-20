# getKioskStatus（系统接口）

## 导入模块

```TypeScript
import { kioskManager } from '@kit.AbilityKit';
```

<a id="getkioskstatus"></a>
## getKioskStatus

```TypeScript
function getKioskStatus(): Promise<KioskStatus>
```

获取系统Kiosk模式的状态信息（包括当前系统是否处于Kiosk模式、进入Kiosk模式应用的名称和UID）。使用Promise异步回调。该接口仅在Phone、PC/2in1和Tablet设备中可正常调用，在其他设备中返回801错误码。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-kioskManager-function getKioskStatus(): Promise<KioskStatus>--><!--Device-kioskManager-function getKioskStatus(): Promise<KioskStatus>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;KioskStatus&gt; | Promise对象，返回当前Kiosk状态信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Failed to connect to the system service. |

**示例：**

```TypeScript
import { kioskManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('getKioskInfo').margin({ top: 10 })
        .onClick(() => {
          // 获取Kiosk模式状态信息
          kioskManager.getKioskStatus()
            .then((data: kioskManager.KioskStatus) => {
              hilog.info(0x0000, 'testTag', '%{public}s', `getKioskStatus success: ${JSON.stringify(data)}`);
            })
            .catch((error: BusinessError) => {
              hilog.error(0x0000, 'testTag', '%{public}s', `getKioskStatus failed. Code: ${error.code}, message: ${error.message}`);
            });
        })
    }
    .height('100%')
    .width('100%')
  }
}

```


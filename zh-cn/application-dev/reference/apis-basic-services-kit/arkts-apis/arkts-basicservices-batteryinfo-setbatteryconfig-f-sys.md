# setBatteryConfig（系统接口）

## 导入模块

```TypeScript
import { batteryInfo } from '@kit.BasicServicesKit';
```

## setBatteryConfig

```TypeScript
function setBatteryConfig(sceneName: string, sceneValue: string): int
```

按场景名称设置电池配置。调用该接口后，系统将根据传入的场景名称和场景值修改对应的电池充电配置，影响设备充电行为。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-batteryInfo-function setBatteryConfig(sceneName: string, sceneValue: string): int--><!--Device-batteryInfo-function setBatteryConfig(sceneName: string, sceneValue: string): int-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sceneName | string | 是 | 电池充电配置的场景名称，用于标识特定的充电配置场景。支持的场景名称由系统定义。 |
| sceneValue | string | 是 | 电池充电配置场景的值，用于指定场景的具体配置参数。取值由系统定义，例如'0'表示关闭该场景的充电配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回设置电池配置的结果。返回0表示设置成功，返回非0表示设置失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5100101](../errorcode-battery-info.md#5100101-连接服务失败) | Failed to connect to the service. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
try {
  let sceneName = 'xxx';
  let sceneValue = '0';
  let result = batteryInfo.setBatteryConfig(sceneName, sceneValue);

  console.info("The result is: " + result);
} catch(err) {
  console.error('setBatteryConfig failed, err: ' + err);
}
```


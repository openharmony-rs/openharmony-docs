# setBatteryConfig（系统接口）

## setBatteryConfig

```TypeScript
function setBatteryConfig(sceneName: string, sceneValue: string): int
```

按场景名称设置电池配置。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-batteryInfo-function setBatteryConfig(sceneName: string, sceneValue: string): int--><!--Device-batteryInfo-function setBatteryConfig(sceneName: string, sceneValue: string): int-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sceneName | string | 是 | 设置场景名称；该参数必须为字符串类型。 |
| sceneValue | string | 是 | 设置场景的值；该参数必须为字符串类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回设置充电结果。返回0表示设置成功，返回非0表示设置失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5100101](../../apis-basic-services-kit/errorcode-battery-info.md#5100101-连接服务失败) | Failed to connect to the service. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

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


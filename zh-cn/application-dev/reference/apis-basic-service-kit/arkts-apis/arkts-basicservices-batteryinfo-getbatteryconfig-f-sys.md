# getBatteryConfig（系统接口）

## getBatteryConfig

```TypeScript
function getBatteryConfig(sceneName: string): string
```

按场景名称查询电池配置。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-batteryInfo-function getBatteryConfig(sceneName: string): string--><!--Device-batteryInfo-function getBatteryConfig(sceneName: string): string-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sceneName | string | 是 | 设置场景名称；该参数必须为字符串类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回电池充电配置，否则返回""。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [5100101](../../apis-basic-services-kit/errorcode-battery-info.md#5100101-连接服务失败) | Failed to connect to the service. |


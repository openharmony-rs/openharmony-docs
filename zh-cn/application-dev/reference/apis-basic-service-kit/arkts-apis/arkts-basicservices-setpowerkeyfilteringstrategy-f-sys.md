# setPowerKeyFilteringStrategy（系统接口）

## setPowerKeyFilteringStrategy

```TypeScript
function setPowerKeyFilteringStrategy(strategy: PowerKeyFilteringStrategy): void
```

设置电源键过滤策略，在电源服务订阅电源键事件后，用于配置电源键事件的处理方式。

电源键过滤策略见[power.PowerKeyFilteringStrategy](arkts-basicservices-powerkeyfilteringstrategy-e.md)接口。

**起始版本：** 21

**需要权限：** ohos.permission.POWER_MANAGER

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strategy | PowerKeyFilteringStrategy | 是 | 电源键过滤策略。该参数必须为枚举类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permissionrequired to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [4900101](../../apis-basic-services-kit/errorcode-power.md#4900101-连接服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
try {
    power.setPowerKeyFilteringStrategy(power.PowerKeyFilteringStrategy.LONG_PRESS_FILTERING_ONCE);
} catch(err) {
    console.error('setPowerKeyFilteringStrategy failed, err: ' + err);
}

```


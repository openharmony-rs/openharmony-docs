# refreshActivity（系统接口）

## refreshActivity

```TypeScript
function refreshActivity(reason: string): void
```

刷新设备活动状态（如：重设屏幕超时息屏时间等）。

只有设备在活动状态下生效，设备活动状态见[power.isActive](arkts-basicservices-power-isactive-f.md#isActive-1)接口。

**起始版本：** 20

**需要权限：** ohos.permission.REFRESH_USER_ACTION

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | string | 是 | 刷新设备活动状态的原因。该参数必须为字符串类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [4900101](../../errorcode-universal.md#4900101-Failed) | Failed to connect to the service. |
| [4900201](../../errorcode-universal.md#4900201-The) | The device activity is being refreshed too frequently; the minimum time<br/>interval is 100 ms. |

**示例：**

```TypeScript
try {
    power.refreshActivity('refreshActivity_test');
} catch(err) {
    console.error('refreshActivity failed, err: ' + err);
}

```


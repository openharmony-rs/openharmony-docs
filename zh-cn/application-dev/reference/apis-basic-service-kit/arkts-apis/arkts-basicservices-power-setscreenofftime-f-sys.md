# setScreenOffTime（系统接口）

## setScreenOffTime

```TypeScript
function setScreenOffTime(timeout: long): void
```

设置熄屏超时时间。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**需要权限：** 
- API版本19+：ohos.permission.POWER_MANAGER

<!--Device-power-function setScreenOffTime(timeout: long): void--><!--Device-power-function setScreenOffTime(timeout: long): void-End-->

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long | 是 | 熄屏超时时间，单位是毫秒，大于0代表熄屏超时时间，-1代表恢复默认超时时间，其它是无效值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Parameter verification failed. |
| [4900101](../../apis-basic-services-kit/errorcode-power.md#4900101-连接服务失败) | Failed to connect to the service. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 19+ |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. This API cannot work in car devices.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 26.1.0+ |

**示例：**

```TypeScript
try {
    power.setScreenOffTime(30000);
} catch(err) {
    console.error('set screen off time failed, err: ' + err);
}
```


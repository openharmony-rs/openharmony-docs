# setPowerMode（系统接口）

## setPowerMode

```TypeScript
function setPowerMode(mode: DevicePowerMode, callback: AsyncCallback<void>): void
```

设置当前设备的电源模式。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.POWER_OPTIMIZATION

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | DevicePowerMode | 是 | 电源模式；该参数类型是一个枚举类。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当设置电源模式成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permissionrequired to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Parameter verification failed. |
| [4900301](../../apis-basic-services-kit/errorcode-power.md#4900301-电源模式设置失败) | Setting the power mode failed.<br>**适用版本：** 23+ |

**示例：**

```TypeScript
power.setPowerMode(power.DevicePowerMode.MODE_PERFORMANCE, (err: Error) => {
    if (typeof err === 'undefined') {
        console.info('set power mode to MODE_PERFORMANCE');
    } else {
        console.error('set power mode failed, err: ' + err);
    }
});

```


## setPowerMode

```TypeScript
function setPowerMode(mode: DevicePowerMode): Promise<void>
```

设置当前设备的电源模式。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.POWER_OPTIMIZATION

**系统能力：** SystemCapability.PowerManager.PowerManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | DevicePowerMode | 是 | 电源模式；该参数类型是一个枚举类。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permissionrequired to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Parameter verification failed. |
| [4900301](../../apis-basic-services-kit/errorcode-power.md#4900301-电源模式设置失败) | Setting the power mode failed.<br>**适用版本：** 23+ |

**示例：**

```TypeScript
power.setPowerMode(power.DevicePowerMode.MODE_PERFORMANCE)
.then(() => {
    console.info('set power mode to MODE_PERFORMANCE');
})
.catch((err : Error)=> {
    console.error('set power mode failed, err: ' + err);
});

```


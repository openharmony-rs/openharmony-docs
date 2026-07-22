# setValue（系统接口）

## 导入模块

```TypeScript
import { brightness } from '@kit.BasicServicesKit';
```

## setValue

```TypeScript
function setValue(value: number): void
```

设置系统的屏幕亮度。

**起始版本：** 7

<!--Device-brightness-function setValue(value: int): void--><!--Device-brightness-function setValue(value: int): void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 亮度的值。范围：0~255；该参数必须为数字类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2. Incorrect parameter types; |
| [4700101](../../apis-basic-services-kit/errorcode-brightness.md#4700101-连接服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
try {
    brightness.setValue(128);
} catch (err) {
    console.error(`Failed to set brightness. Code: ${err.code}, message: ${err.message}`);
}

```


## setValue

```TypeScript
function setValue(value: number, continuous: boolean): void
```

设置系统的屏幕亮度。用于连续调节亮度的场景，在连续调节亮度过程中，设置continuous为true，结束时设置continuous为false，会有更好的性能。

**起始版本：** 11

<!--Device-brightness-function setValue(value: int, continuous: boolean): void--><!--Device-brightness-function setValue(value: int, continuous: boolean): void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 亮度的值。范围：0~255。 |
| continuous | boolean | 是 | 亮度调节是否连续。true表示亮度调节连续，false表示亮度调节不连续，默认为false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2. Incorrect parameter types; |
| [4700101](../../apis-basic-services-kit/errorcode-brightness.md#4700101-连接服务失败) | Failed to connect to the service. |

**示例：**

```TypeScript
try {
    brightness.setValue(128, true);
} catch (err) {
    console.error(`Failed to set brightness. Code: ${err.code}, message: ${err.message}`);
}

```


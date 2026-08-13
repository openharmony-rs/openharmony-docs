# setValue（系统接口）

## setValue

```TypeScript
function setValue(value: int): void
```

设置系统的屏幕亮度。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-brightness-function setValue(value: int): void--><!--Device-brightness-function setValue(value: int): void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int | 是 | 亮度的值。范围：0~255；该参数必须为数字类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; |
| [4700101](../../apis-basic-services-kit/errorcode-brightness.md#4700101-连接服务失败) | Failed to connect to the service. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

```TypeScript
try {
    brightness.setValue(128);
} catch(err) {
    console.error('set brightness failed, err: ' + err);
}
```


## setValue

```TypeScript
function setValue(value: int, continuous: boolean): void
```

设置系统的屏幕亮度。用于连续调节亮度的场景，在连续调节亮度过程中，设置continuous为true，结束时设置continuous为false，会有更好的性能。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-brightness-function setValue(value: int, continuous: boolean): void--><!--Device-brightness-function setValue(value: int, continuous: boolean): void-End-->

**系统能力：** SystemCapability.PowerManager.DisplayPowerManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int | 是 | 亮度的值。范围：0~255。 |
| continuous | boolean | 是 | 亮度调节是否连续。true表示亮度调节连续，false表示亮度调节不连续，默认为false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; |
| [4700101](../../apis-basic-services-kit/errorcode-brightness.md#4700101-连接服务失败) | Failed to connect to the service. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

```TypeScript
try {
    brightness.setValue(128, true);
} catch(err) {
    console.error('set brightness failed, err: ' + err);
}
```


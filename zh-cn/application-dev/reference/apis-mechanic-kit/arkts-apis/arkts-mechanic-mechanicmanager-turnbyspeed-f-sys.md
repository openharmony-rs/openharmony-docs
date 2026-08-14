# turnBySpeed（系统接口）

## turnBySpeed

```TypeScript
function turnBySpeed(mechId: int, angleSpeed: double, duration: int): Promise<Result>
```

以固定速度原地旋转

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-mechanicManager-function turnBySpeed(mechId: int, angleSpeed: double, duration: int): Promise<Result>--><!--Device-mechanicManager-function turnBySpeed(mechId: int, angleSpeed: double, duration: int): Promise<Result>-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mechId | int | 是 | 具身设备ID。 &lt;br&gt;取值限定为整数。 |
| angleSpeed | double | 是 | 角速度。 |
| duration | int | 是 | 转动时长，单位ms。 &lt;br&gt;取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&gt; | 202 - 非系统应用 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-设备未连接) | Device not connected. |
| [33300003](../errorcode-mechanic.md#33300003-功能不支持) | Feature not supported. |


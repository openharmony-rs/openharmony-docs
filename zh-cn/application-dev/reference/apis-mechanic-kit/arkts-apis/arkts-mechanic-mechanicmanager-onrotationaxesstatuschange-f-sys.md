# onRotationAxesStatusChange（系统接口）

## onRotationAxesStatusChange

```TypeScript
function onRotationAxesStatusChange(callback: Callback<RotationAxesStateChangeInfo>): void
```

Register a listener for axis state changes. The status of the rotation axis changes dynamically, which needs to be monitored.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-mechanicManager-function onRotationAxesStatusChange(callback: Callback<RotationAxesStateChangeInfo>): void--><!--Device-mechanicManager-function onRotationAxesStatusChange(callback: Callback<RotationAxesStateChangeInfo>): void-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;RotationAxesStateChangeInfo&gt; | 是 | Rotate axis state changes callback. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |


# setAppDragSwitchState（系统接口）

## setAppDragSwitchState

```TypeScript
function setAppDragSwitchState(enabled: boolean, bundleName: string): void
```

控制统一拖拽适配应用开关。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-dragInteraction-function setAppDragSwitchState(enabled: boolean, bundleName: string): void--><!--Device-dragInteraction-function setAppDragSwitchState(enabled: boolean, bundleName: string): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Drag

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 设置开关状态。&lt;br&gt;false：关闭，true：开启。 |
| bundleName | string | 是 | 设置指定应用包名。长度取值范围（0, 128]。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. &lt;br&gt;2.Incorrect parameter types.3.Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |


# DeviceSelectCallback（系统接口）

```TypeScript
type DeviceSelectCallback = (selectPurpose: number) => DeviceSelectResult
```

伴随设备选择回调函数类型。当系统需要用户选择伴随设备时（如添加模板或执行认证），会调用此回调，应用需返回用户选择的设备信息。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectPurpose | int | 是 | 选择目的。用于标识当前设备选择的意图，取值参见[SelectPurpose](arkts-userauthentication-selectpurpose-e-sys.md)。SELECT_ADD_DEVICE(1)表示选择添加模板的设备，SELECT_AUTH_DEVICE(2)表示选择认证设备。厂商可自定义扩展值（大于等于10000）。应用应根据选择目的返回相应的设备列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DeviceSelectResult | 设备选择结果。包含用户选择的设备信息列表（deviceKeys）和可选的扩展上下文（selectionContext）。 |


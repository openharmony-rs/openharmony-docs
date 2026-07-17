# DeviceSelectResult（系统接口）

伴随设备选择回调的返回结果。用于在设备选择回调中返回用户选择的设备信息和扩展上下文。

**起始版本：** 23

<!--Device-companionDeviceAuth-interface DeviceSelectResult--><!--Device-companionDeviceAuth-interface DeviceSelectResult-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## deviceKeys

```TypeScript
deviceKeys: DeviceKey[]
```

设备信息列表。包含用户选择的设备业务标识信息，每个DeviceKey包含设备ID类型、设备ID和设备用户ID。系统会根据这些信息执行后续的添加模板或认证操作。

**类型：** DeviceKey[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceSelectResult-deviceKeys: DeviceKey[]--><!--Device-DeviceSelectResult-deviceKeys: DeviceKey[]-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## selectionContext

```TypeScript
selectionContext?: Uint8Array
```

设备选择上下文。携带JSON格式的扩展信息，可用于传递设备选择过程中的额外参数，如认证配置、业务场景标识等。

**类型：** Uint8Array

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceSelectResult-selectionContext?: Uint8Array--><!--Device-DeviceSelectResult-selectionContext?: Uint8Array-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。


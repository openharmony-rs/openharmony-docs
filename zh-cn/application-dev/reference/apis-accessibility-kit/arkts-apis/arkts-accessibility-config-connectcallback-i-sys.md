# ConnectCallback（系统接口）

通过[enableAbilityWithCallback](arkts-accessibility-config-enableabilitywithcallback-f-sys.md#enableabilitywithcallback-1)接口启用辅助扩展应用时提供的回调函数。辅助扩展应用连接断开时，回调函数将被调用。

**起始版本：** 23

<!--Device-config-export interface ConnectCallback--><!--Device-config-export interface ConnectCallback-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { config } from '@kit.AccessibilityKit';
```

## onDisconnect

```TypeScript
onDisconnect: OnDisconnectCallback
```

辅助扩展应用的连接断开时调用的回调函数。

**类型：** OnDisconnectCallback

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ConnectCallback-onDisconnect: OnDisconnectCallback--><!--Device-ConnectCallback-onDisconnect: OnDisconnectCallback-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。


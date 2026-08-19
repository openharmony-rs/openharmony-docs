# AtomicServiceMenuBar(系统接口)（系统接口）

依赖当前原子化服务的UI上下文，创建AtomicServiceMenuBar对象，用于操控右上角菜单功能胶囊的显隐状态。 > **说明：** > > 该组件从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 23

<!--Device-unnamed-export declare class AtomicServiceMenuBar--><!--Device-unnamed-export declare class AtomicServiceMenuBar-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { AtomicServiceMenuBar } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(uiContext: UIContext)
```

AtomicServiceMenuBar的构造函数。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceMenuBar-constructor(uiContext: UIContext)--><!--Device-AtomicServiceMenuBar-constructor(uiContext: UIContext)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | UIContext | 是 | 当前原子化服务的UI上下文信息。 |

## setVisible

```TypeScript
public setVisible(visible: boolean): void
```

设置当前原子化服务菜单功能胶囊的显隐状态。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AtomicServiceMenuBar-public setVisible(visible: boolean): void--><!--Device-AtomicServiceMenuBar-public setVisible(visible: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| visible | boolean | 是 | 菜单功能胶囊预期的状态。true表示显示菜单功能胶囊，false表示隐藏菜单功能胶囊。 |


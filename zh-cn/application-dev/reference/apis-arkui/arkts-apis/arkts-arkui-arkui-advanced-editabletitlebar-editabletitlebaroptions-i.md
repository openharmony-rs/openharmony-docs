# EditableTitleBarOptions

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { EditableLeftIconType, EditableTitleBar, EditableTitleBarMenuItem, EditableTitleBarItem, EditableTitleBarOptions } from '@kit.ArkUI';
```

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

标题栏背景模糊样式。默认值：BlurStyle.NONE

**类型：** BlurStyle

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

标题栏背景色。默认值：'#00000000'

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## safeAreaEdges

```TypeScript
safeAreaEdges?: Array<SafeAreaEdge>
```

配置扩展安全区域的方向。默认值：[SafeAreaEdge.TOP]

**类型：** Array&lt;[SafeAreaEdge](../arkts-components/arkts-arkui-safeareaedge-e.md)&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## safeAreaTypes

```TypeScript
safeAreaTypes?: Array<SafeAreaType>
```

配置扩展安全区域的类型。默认值：[SafeAreaType.SYSTEM]

**类型：** Array&lt;[SafeAreaType](../arkts-components/arkts-arkui-safeareatype-e.md)&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

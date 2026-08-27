# TreeView

树视图作为一种分层显示的列表，适合显示嵌套结构。树视图包含父节点和子节点，支持展开或折叠。树视图适用于效率型应用的侧边导航栏中，如备忘录、电子邮件、图库等。

> **说明：**
> 
> - 该组件仅可在Stage模型下使用。
> 
> - 如果TreeView设置通用属性和通用事件，编译工具链会额
> 外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到TreeView本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议TreeView设置通用属性和通用事
> 件。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CallbackParam, NodeParam, TreeController, TreeListenType, TreeListener, TreeListenerManager, TreeView } from '@kit.ArkUI';
```

## treeController

```TypeScript
treeController: TreeController
```

树视图组件的控制器，用于控制树的节点信息。

**类型：** [TreeController](arkts-arkui-arkui-advanced-treeview-treecontroller-c.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

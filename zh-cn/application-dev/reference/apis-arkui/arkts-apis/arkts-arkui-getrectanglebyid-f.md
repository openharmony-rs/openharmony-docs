# getRectangleById

## getRectangleById

```TypeScript
function getRectangleById(id: string): ComponentInfo
```

根据组件ID获取组件实例对象，通过组件实例对象将获取的坐标位置和大小同步返回给开发者。

> **说明：**
>
> - 从API version 10开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的
> [getComponentUtils](arkts-arkui-uicontext-c.md#getcomponentutils-1)方法获取当前UI上下
> 文关联的[ComponentUtils](arkts-arkui-componentutils-c.md)对象。在目标组件布局完成后，通过该接口能够获取组件坐标和尺寸信息。建议在
> [布局回调](arkts-arkui-inspector.md)中使用该接口。如果组件动态创建但未挂载组件树，则无法通过该接口获取正常的组件信息。因为组件在未挂载组件树的情况下，一般未经过UI框架正常
> 的测量与布局，此时请确保组件正常挂载组件树后再尝试获取组件信息。

**起始版本：** 10

**废弃版本：** 18

**替代接口：** getRectangleById

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 指定组件id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ComponentInfo | 组件大小、位置、平移缩放旋转及仿射矩阵属性信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | UI execution context not found. |

**示例：**

```TypeScript
import { componentUtils } from '@kit.ArkUI';
let modePosition:componentUtils.ComponentInfo = componentUtils.getRectangleById("onClick");

```


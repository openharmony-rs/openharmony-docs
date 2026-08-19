# DragPreview

拖拽背板的对象，在OnDrop和OnDragEnd回调中使用不生效。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-dragController-export class DragPreview--><!--Device-dragController-export class DragPreview-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## animate

```TypeScript
animate(options: AnimationOptions, handler: () => void): void
```

设置背板蒙版颜色变化动效，在OnDrop和OnDragEnd回调中使用不生效，仅支持通过 [getDragPreview()](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-dragcontroller-c.md#getdragpreview) 方法获取到的对象上使用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragPreview-animate(options: AnimationOptions, handler: () => void): void--><!--Device-DragPreview-animate(options: AnimationOptions, handler: () => void): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | AnimationOptions | 是 | 动效参数。 |
| handler | () =&gt; void | 是 | 用于修改背板蒙版颜色等属性的回调方法。 |

## setForegroundColor

```TypeScript
setForegroundColor(color: ResourceColor): void
```

设置背板蒙版颜色，在OnDrop和OnDragEnd回调中使用不生效，仅支持通过 [getDragPreview()](../../apis-na/arkts-apis/arkts-na-arkui-uicontext-dragcontroller-c.md#getdragpreview) 方法获取到的对象上使用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragPreview-setForegroundColor(color: ResourceColor): void--><!--Device-DragPreview-setForegroundColor(color: ResourceColor): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | ResourceColor | 是 | 背板蒙版颜色。 |


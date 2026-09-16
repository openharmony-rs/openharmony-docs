# DragPreview

拖拽背板的对象，在OnDrop和OnDragEnd回调中使用不生效。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## animate

```TypeScript
animate(options: AnimationOptions, handler: () =>void): void
```

设置背板蒙版颜色变化动效，在OnDrop和OnDragEnd回调中使用不生效，仅支持通过[getDragPreview()](arkts-arkui-arkui-uicontext-dragcontroller-c.md#getdragpreview)方法获取到的对象上使用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AnimationOptions](arkts-arkui-dragcontroller-animationoptions-i.md) | 是 | 动效参数。 |
| handler | () =&gt;void | 是 | 用于修改背板蒙版颜色等属性的回调方法。 |

**示例**

```TypeScript
> 说明：
> 
> 推荐通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[getDragController](arkts-arkui-arkui-uicontext-uicontext-c.md#getdragcontroller)方法获取当前UI上下文关联的DragController对象。

在EntryAbility.ets中获取UI上下文并保存至LocalStorage中。
```

```TypeScript
在Index.ets中通过this.getUIContext().getSharedLocalStorage()获取UI上下文，进而获取DragController对象实施后续操作。
```

## setForegroundColor

```TypeScript
setForegroundColor(color: ResourceColor): void
```

设置背板蒙版颜色，在OnDrop和OnDragEnd回调中使用不生效，仅支持通过[getDragPreview()](arkts-arkui-arkui-uicontext-dragcontroller-c.md#getdragpreview)方法获取到的对象上使用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [ResourceColor](arkts-arkui-resourcecolor-t.md) | 是 | 背板蒙版颜色。 |

**示例**

```TypeScript
请参考[animate](#animate)。
```

# Button

菜单中的菜单项按钮。

**起始版本：** 9

<!--Device-promptAction-interface Button--><!--Device-promptAction-interface Button-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## color

```TypeScript
color: string | Resource
```

按钮文本颜色。

**类型：** string \| Resource

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Button-color: string | Resource--><!--Device-Button-color: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primary

```TypeScript
primary?: boolean
```

在弹窗获焦且未进行tab键走焦时，按钮是否默认响应Enter键。多个Button时，只允许一个Button的该字段配置为true，否则所有Button均不响应。多重弹窗可自动获焦连续响应。值为true表示按钮默认响应Enter键，值为false时，按钮不默认响应Enter键。<br/>默认值：false

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Button-primary?: boolean--><!--Device-Button-primary?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: string | Resource
```

按钮文本内容。

**类型：** string \| Resource

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Button-text: string | Resource--><!--Device-Button-text: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full


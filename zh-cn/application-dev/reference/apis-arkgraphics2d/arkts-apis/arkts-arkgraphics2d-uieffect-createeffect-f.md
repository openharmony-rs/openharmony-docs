# createEffect

## createEffect

```TypeScript
function createEffect(): VisualEffect
```

创建VisualEffect实例用于给组件添加多种VisualEffect效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

<!--Device-uiEffect-function createEffect(): VisualEffect--><!--Device-uiEffect-function createEffect(): VisualEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| VisualEffect | 返回VisualEffect实例，支持添加多种VisualEffect效果。 |

## 示例

```TypeScript
let visualEffect : uiEffect.VisualEffect = uiEffect.createEffect()
```


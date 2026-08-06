# createEffect

## createEffect

```TypeScript
function createEffect(): VisualEffect
```

创建VisualEffect实例用于给组件添加多种effect效果。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

<!--Device-uiEffect-function createEffect(): VisualEffect--><!--Device-uiEffect-function createEffect(): VisualEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回VisualEffect的头节点。 |

**示例：**

```TypeScript
let visualEffect : uiEffect.VisualEffect = uiEffect.createEffect()
```


# CommonTransition

```TypeScript
declare class CommonTransition<T>
```

页面转场通用动效，通过[PageTransitionEnter](arkts-arkui-pagetransitionenter-comp.md#pagetransitionenter)和[PageTransitionExit](arkts-arkui-pagetransitionenter-comp-con.md#pagetransitionexit)继承使用，需在pageTransition()函数中配置，slide与translate均涉及位置移动：slide适用于需要沿预置方向（左/右/上/下/START/END）滑入滑出的场景，使用简单；translate适用于需要自定义平移距离的场景，灵活性更高。当slide和translate同时设置时，默认生效slide。scale、opacity分别设置缩放和透明度效果，可与上述效果组合使用。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

转场通用动效的构造函数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## opacity

```TypeScript
opacity(value: number): T
```

设置入场的起点透明度值或者退场的终点透明度值。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 设置入场的起点透明度值或者退场的终点透明度值。<br>取值范围：[0, 1] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件，用于链式调用。 |

## scale

```TypeScript
scale(value: ScaleOptions): T
```

设置页面转场时的缩放效果。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ScaleOptions](arkts-arkui-common-comp-scaleoptions-i.md) | 是 | 设置页面转场时的缩放效果，为入场时起点和退场时终点的值。<br>- x：横向放大倍数（或缩小比例）。<br>- y：纵向放大倍数（或缩小比例）。<br>- z：竖向放大倍数（或缩小比例）。<br>- centerX、centerY缩放中心点。centerX和centerY默认值是"50%"，即默认以页面的中心点为缩放中心点。<br>- 中心点为(0, 0)代表页面的左上角。<br>**适用版本：** 18 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件，用于链式调用。 |

## slide

```TypeScript
slide(value: SlideEffect): T
```

设置页面转场时的滑入滑出效果，和translate同时设置时默认生效slide。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SlideEffect](arkts-arkui-pagetransitionenter-comp-slideeffect-e.md) | 是 | 页面转场时的滑入滑出效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件，用于链式调用。 |

## translate

```TypeScript
translate(value: TranslateOptions): T
```

设置页面转场时的平移效果。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TranslateOptions](arkts-arkui-common-comp-translateoptions-i.md) | 是 | 设置页面转场时的平移效果，为入场时起点和退场时终点的值，和slide同时设置时默认生效slide。<br>- x：横向的平移距离。<br>- y：纵向的平移距离。<br>- z：竖向的平移距离。<br>**适用版本：** 18 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件，用于链式调用。 |

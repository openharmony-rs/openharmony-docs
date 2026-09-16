# GestureControl

定义手势竞争结果。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 枚举

| 名称 | 说明 |
| --- | --- |
| [GestureType](arkts-arkui-gesturecontrol-gesturetype-e.md) | 定义手势类型。 |

## 示例

```TypeScript
该示例通过LongPressGesture实现了长按手势的识别。从API version 22开始，支持通过[LongPressGestureHandlerOptions](./ts-gesturehandler.md#longpressgesturehandleroptions)的allowableMovement属性设置识别手势的最大移动距离。
```

```TypeScript
### 示例1（双击手势识别）

该示例通过TapGesture实现了双击手势的识别。


```

```TypeScript
### 示例2（获取单击手势坐标）

该示例通过TapGesture获取单击手势点击位置的坐标。


```

```TypeScript
### 示例3（获取组件实时位置）

该示例通过[getCurrentLocalPosition](#getcurrentlocalposition)方法获取点击位置相对于当前组件实时位置左上角的坐标。

从API版本26.0.0开始，新增支持getCurrentLocalPosition接口。
```

```TypeScript
该示例通过PanGesture实现了单指/双指滑动手势的识别。
```

```TypeScript
该示例展示了如何实现快滑手势的识别。
```

```TypeScript
该示例通过配置RotationGesture实现了双指旋转手势的识别。
```

```TypeScript
### 示例1（实现简单缩放）

该示例通过配置PinchGesture实现了三指捏合手势的识别功能。


```

```TypeScript
### 示例2（实现图片跟手缩放）

通过配置PinchGesture，该示例实现了图片的跟手缩放效果。
```

```TypeScript
该示例通过配置GestureGroup，实现了长按和拖动的组合手势顺序识别功能。
```

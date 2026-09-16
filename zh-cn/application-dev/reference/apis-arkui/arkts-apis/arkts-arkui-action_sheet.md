# action_sheet(ActionSheet)

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ActionSheet](arkts-arkui-actionsheet-c.md) |  |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ActionSheetButtonOptions](arkts-arkui-actionsheetbuttonoptions-i.md) | 弹窗中按钮的样式。 |
| [ActionSheetOffset](arkts-arkui-actionsheetoffset-i.md) | 弹窗相对alignment所在位置的偏移量。 |
| [ActionSheetOptions](arkts-arkui-actionsheetoptions-i.md) | 列表选择弹窗的样式。 |
| [DismissDialogAction](arkts-arkui-dismissdialogaction-i.md) | 弹窗关闭的信息。 |
| [SheetInfo](arkts-arkui-sheetinfo-i.md) | 弹窗中的选项内容，每一项支持设置文本、图标以及选中的回调。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ActionSheetOptions](arkts-arkui-actionsheetoptions-i-sys.md) | 列表选择弹窗的样式。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [ImmersiveMode](arkts-arkui-immersivemode-t.md) | 弹窗的蒙层效果。 |
| [LevelMode](arkts-arkui-levelmode-t.md) | 弹窗的显示层级。 |

## 示例

```TypeScript
### 示例1（弹出列表选择弹窗）

该示例通过点击按钮弹出列表选择弹窗。


```

```TypeScript
### 示例2（可在主窗外弹出的弹窗）

在2in1设备上设置showInSubWindow为true时，可以弹出在主窗外显示的弹窗。


```

```TypeScript
### 示例3（设置弹窗的动画）

该示例通过配置transition实现弹窗的显示和消失动画。


```

```TypeScript
### 示例4（设置弹窗的样式）

该示例定义了ActionSheet的样式，如宽度、高度、背景色、阴影等。


```

```TypeScript
### 示例5（悬停态弹窗）
```

```TypeScript
### 示例6（弹窗生命周期）

该示例为弹窗配置生命周期回调。

从API version 19开始，在ActionSheetOptions中新增了onDidAppear、onDidDisappear、onWillAppear和onWillDisappear属性。


```

```TypeScript
### 示例7（自定义背景模糊效果参数）

该示例通过配置backgroundBlurStyleOptions，实现自定义背景模糊效果。

从API version 19开始，在ActionSheetOptions中新增了backgroundBlurStyleOptions属性。


```

```TypeScript
### 示例8（自定义背景效果参数）

该示例通过配置backgroundEffect，实现自定义背景效果。

从API version 19开始，在ActionSheetOptions中新增了backgroundEffect属性。


```

```TypeScript
### 示例9（设置弹窗的沉浸光感效果）

该示例通过ActionSheetOptions中的systemMaterial属性设置组件的系统材质，实现沉浸光感效果。设置系统材质后，ActionSheet弹出过程中会有非线性形变和边缘流光。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，在ActionSheetOptions中新增了systemMaterial属性。
```

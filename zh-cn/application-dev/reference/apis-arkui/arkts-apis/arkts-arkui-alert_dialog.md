# alert_dialog(AlertDialog)

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AlertDialog](arkts-arkui-alertdialog-c.md) |  |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AlertDialogButtonBaseOptions](arkts-arkui-alertdialogbuttonbaseoptions-i.md) | 警告弹窗中按钮的样式。 |
| [AlertDialogButtonOptions](arkts-arkui-alertdialogbuttonoptions-i.md) | 继承自[AlertDialogButtonBaseOptions](arkts-arkui-alertdialogbuttonbaseoptions-i.md)。 |
| [AlertDialogParam](arkts-arkui-alertdialogparam-i.md) | 警告弹窗的样式。 |
| [AlertDialogParamWithButtons](arkts-arkui-alertdialogparamwithbuttons-i.md) | 继承自[AlertDialogParam](arkts-arkui-alertdialogparam-i.md)。 |
| [AlertDialogParamWithConfirm](arkts-arkui-alertdialogparamwithconfirm-i.md) | 继承自[AlertDialogParam](arkts-arkui-alertdialogparam-i.md)。 |
| [AlertDialogParamWithOptions](arkts-arkui-alertdialogparamwithoptions-i.md) | 继承自[AlertDialogParam](arkts-arkui-alertdialogparam-i.md)。 |
| [DismissDialogAction](arkts-arkui-dismissdialogaction-i.md) | Dialog关闭的信息。 |
| [TextStyle](arkts-arkui-textstyle-i.md) | 弹窗中message的文本样式，包含文本截断方式等。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AlertDialogParam](arkts-arkui-alertdialogparam-i-sys.md) | 警告弹窗的样式。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DialogAlignment](arkts-arkui-dialogalignment-e.md) | 警告弹窗的对齐方式。 |
| [DialogButtonDirection](arkts-arkui-dialogbuttondirection-e.md) | 警告弹窗中按钮的对齐方式。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [LevelOrder](arkts-arkui-levelorder-t.md) | 弹窗的显示顺序。 |

## 示例

```TypeScript
### 示例1（弹出多个按钮的弹窗）

该示例通过AlertDialogParamWithConfirm、AlertDialogParamWithButtons和AlertDialogParamWithOptions实现了分别弹出一、二、三个按钮的弹窗。


```

```TypeScript
### 示例2（可在主窗外弹出的弹窗）

在2in1设备上设置AlertDialogParam中showInSubWindow属性的值为true时，可以弹出在主窗外显示的弹窗。


```

```TypeScript
### 示例3（设置弹窗的动画）

该示例通过配置AlertDialogParam中的transition属性来实现弹窗的显示和消失动画。


```

```TypeScript
### 示例4（设置弹窗的样式）

本示例展示了如何设置AlertDialog的样式，包括宽度、高度、背景色、阴影等。


```

```TypeScript
### 示例5（悬停态弹窗）
```

```TypeScript
### 示例6（弹窗生命周期）

该示例展示了弹窗生命周期的相关接口的使用方法。


```

```TypeScript
### 示例7（自定义背景模糊效果参数）

该示例通过配置AlertDialogParam中的backgroundBlurStyleOptions属性，实现了自定义背景模糊效果。

从API version 19开始，在AlertDialogParam中新增了backgroundBlurStyleOptions属性。


```

```TypeScript
### 示例8（自定义背景效果参数）

该示例通过配置AlertDialogParam中的backgroundEffect属性，实现自定义背景效果。

从API version 19开始，在AlertDialogParam中新增了backgroundEffect属性。


```

```TypeScript
### 示例9（设置弹窗的沉浸光感效果）

该示例通过AlertDialogParam中的systemMaterial属性设置组件的系统材质，实现沉浸光感效果。设置系统材质后，AlertDialog弹出过程中会有非线性形变和边缘流光。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，在AlertDialogParam中新增了systemMaterial属性。
```

# custom_dialog_controller(CustomDialog)

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [CustomDialogController](arkts-arkui-customdialogcontroller-c.md) | 自定义弹窗的控制器。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CustomDialogControllerOptions](arkts-arkui-customdialogcontrolleroptions-i.md) | 自定义弹窗的样式。 |
| [DismissDialogAction](arkts-arkui-dismissdialogaction-i.md) | Dialog关闭的信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CustomDialogControllerOptions](arkts-arkui-customdialogcontrolleroptions-i-sys.md) | 自定义弹窗的样式。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [PromptActionCommonState](arkts-arkui-promptactioncommonstate-t.md) | 自定义弹窗的状态。 |

## 示例

```TypeScript
### 示例1（弹出嵌套弹窗）

该示例实现了在CustomDialog中打开另一个或另一些CustomDialog。


```

```TypeScript
### 示例2（可在主窗外弹出的弹窗）

在2in1设备上设置showInSubWindow为true时，可以弹出在主窗外显示的弹窗。

从API版本26.0.0开始，CustomDialogControllerOptions新增displayModeInSubWindow属性。


```

```TypeScript
### 示例3（设置弹窗的样式）

该示例展示了CustomDialog的样式，包括宽度、高度、背景色、阴影等。


```

```TypeScript
### 示例4（悬停态弹窗）
```

```TypeScript
### 示例5（获取弹窗的状态）

该示例实现了在[CustomDialogController](arkts-arkui-customdialogcontroller-c.md)中调用getState获取弹窗当前状态。

从API version 20开始，在CustomDialogController中新增了getState接口。
```

```TypeScript
### 示例6（使用@Link和@Consume监听数据变化）

该示例使用[@Link](../../../ui/state-management/arkts-link.md)和[@Consume](../../../ui/state-management/arkts-provide-and-consume.md)实现页面与弹窗内数据的双向绑定。


```

```TypeScript
### 示例7（自定义带loading的弹窗）

该示例使用maskColor，maskRect和[LoadingProgress](ts-basic-components-loadingprogress.md)，实现带loading的弹窗，并展示不在maskRect区域的事件透传效果。


```

```TypeScript
### 示例8（不使用keyboardAvoidDistance调整弹窗与软键盘的间距）

该示例通过监听键盘变化，调整布局[margin](ts-universal-attributes-size.md#margin)的属性，实现与使用keyboardAvoidDistance调整弹窗与软键盘的间距一样的效果。

从API version 15开始，在CustomDialogControllerOptions中新增了keyboardAvoidDistance属性。


```

```TypeScript
### 示例9（弹窗生命周期）

该示例为弹窗配置生命周期回调。

从API version 19开始，在CustomDialogControllerOptions中新增了onDidAppear、onDidDisappear、onWillAppear和onWillDisappear属性。


```

```TypeScript
### 示例10（不同customStyle下的弹窗示例）

该示例是在对齐方式为[DialogAlignment.Bottom](ts-methods-alert-dialog-box.md#dialogalignment枚举说明)时，展示customStyle不同值下，弹窗内容与安全区域的效果。


```

```TypeScript
### 示例11（自定义背景模糊效果参数）

该示例通过配置backgroundBlurStyleOptions，实现自定义背景模糊效果。

从API version 19开始，在CustomDialogControllerOptions中新增了backgroundBlurStyleOptions属性。


```

```TypeScript
### 示例12（自定义背景效果参数）

该示例通过配置backgroundEffect，实现自定义背景效果。

从API version 19开始，在CustomDialogControllerOptions中新增了backgroundEffect属性。


```

```TypeScript
### 示例13（自定义弹窗动态刷新宽度）

该示例通过状态变量同步自定义组件的宽度，实现自定义弹窗宽度动态切换。


```

```TypeScript
### 示例14（设置弹窗的沉浸光感效果）

该示例通过systemMaterial设置组件的系统材质，实现沉浸光感效果。设置系统材质后，CustomDialog弹出过程中会有非线性形变和边缘流光。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，在CustomDialogControllerOptions中新增了systemMaterial属性。
```

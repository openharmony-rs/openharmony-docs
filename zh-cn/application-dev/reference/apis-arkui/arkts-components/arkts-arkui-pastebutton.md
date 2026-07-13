# PasteButton

定义用于设置粘贴按钮的接口。


## PasteButton

```TypeScript
PasteButton()
```

默认创建带有图标、文本、背景的粘贴控件。控件创建完成后，用户点击时系统会执行授权校验；授权成功后，应用可读取当前剪贴板内容。
<br>**说明**</br>
<ul><li>为避免因控件样式不合法而导致授权失败，请开发者先了解安全控件样式
的[约束与限制](docroot://security/AccessToken/security-component-overview.md#约束与限制)。</li></ul>

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PasteButton

```TypeScript
PasteButton(options: PasteButtonOptions)
```

使用指定的图标、文本和按钮类型创建粘贴按钮。创建后，系统会触发一个
点击按钮时的授权检查。授权成功后，应用将获得临时权限
读取剪贴板。
<br>**说明**</br>
<ul><li>为避免因控件样式不合法而导致授权失败，请开发者先了解安全控件样式
的[约束与限制](docroot://security/AccessToken/security-component-overview.md#约束与限制)。</li>
</ul>

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | PasteButtonOptions | 是 | 粘贴控件的配置选项，用于指定图标、文本和按钮类型等元素属性。<br>建议至少显式设置icon或text中的一项，以便用户清楚识别控件用途。<br/>若icon和text都未传入，则options不生效，控件显示为默认样式：<br/>{<br/>icon: PasteIconStyle.LINES,<br/>text: PasteDescription.PASTE,<br/>buttonType: ButtonType.Capsule <br/>} |

## 汇总

- [PasteButtonOptions](arkts-arkui-pastebutton-pastebuttonoptions-i.md)
- [PasteButtonCallback](arkts-arkui-pastebutton-pastebuttoncallback-t.md)
- [PasteButtonOnClickResult](arkts-arkui-pastebutton-pastebuttononclickresult-e.md)
- [PasteDescription](arkts-arkui-pastebutton-pastedescription-e.md)
- [PasteIconStyle](arkts-arkui-pastebutton-pasteiconstyle-e.md)

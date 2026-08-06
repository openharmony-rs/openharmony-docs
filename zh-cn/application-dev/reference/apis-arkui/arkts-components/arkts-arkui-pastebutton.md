# PasteButton

安全控件的粘贴控件。用户点击粘贴控件，应用可以临时获取读取剪贴板权限。 <br>**说明**</br> <ul><li>

## 核心枚举类型</li> <li>**[PasteIconStyle]{@link PasteIconStyle}：** 粘贴控件图标风格枚举，用于指定控件展示的图标风格。</li> <li>**[PasteDescription]{@link PasteDescription}：** 粘贴控件文本描述枚举，用于指定控件展示的文本描述。</li> <li>**[PasteButtonOnClickResult]{@link PasteButtonOnClickResult}：** 粘贴控件点击结果枚举，用于表示点击后授权是否成功。</li> <li>###### 核心接口类型</li> <li>**[PasteButtonOptions]{@link PasteButtonOptions}：** 粘贴控件配置对象，用于指定图标、文字和按钮类型等元素属性。</li> <li>**[PasteButtonCallback]{@link PasteButtonCallback}：** 粘贴控件点击回调类型，用于返回点击事件、授权结果和错误信息。</li> <li>###### 子组件</li> <li>不支持</li></ul>

## PasteButton

```TypeScript
PasteButton()
```

默认创建带有图标、文本、背景的粘贴控件。控件创建完成后，用户点击时系统会执行授权校验；授权成功后，应用可读取当前剪贴板内容。 \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_**说明**\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_ \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_为避免因控件样式不合法而导致授权失败，请开发者先了解安全控件样式 的\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。\_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PasteButtonInterface-(): PasteButtonAttribute--><!--Device-PasteButtonInterface-(): PasteButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PasteButton

```TypeScript
PasteButton(options: PasteButtonOptions)
```

使用指定的图标、文本和按钮类型创建粘贴按钮。创建后，系统会触发一个 点击按钮时的授权检查。授权成功后，应用将获得临时权限 读取剪贴板。 \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_**说明**\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_ \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_为避免因控件样式不合法而导致授权失败，请开发者先了解安全控件样式 的\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。\_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_ \_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PasteButtonInterface-(options: PasteButtonOptions): PasteButtonAttribute--><!--Device-PasteButtonInterface-(options: PasteButtonOptions): PasteButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 粘贴控件的配置选项，用于指定图标、文本和按钮类型等元素属性。 \_\_\_HTML\_TAG\_USD\_0\_\_\_建议至少显式设置icon或text中的一项，以便用户清楚识别控件用途。\_\_\_HTML\_TAG\_USD\_1\_\_\_若icon和text都未传入，则options不生效，控件显示为默认样式：\_\_\_HTML\_TAG\_USD\_2\_\_\_{\_\_\_HTML\_TAG\_USD\_3\_\_\_icon: PasteIconStyle.LINES,\_\_\_HTML\_TAG\_USD\_4\_\_\_text: PasteDescription.PASTE,\_\_\_HTML\_TAG\_USD\_5\_\_\_buttonType: ButtonType.Capsule \_\_\_HTML\_TAG\_USD\_6\_\_\_}  |

## 汇总


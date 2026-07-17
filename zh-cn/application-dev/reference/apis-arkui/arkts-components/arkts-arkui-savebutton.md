# SaveButton

安全控件的保存控件系统接口，适用于应用需要临时获取媒体库访问权限以保存图片或视频的场景，例如图片保存到相册、媒体内容导出等。
应用集成保存控件后，用户首次使用该控件时，保存控件会展示弹窗供用户确认。用户点击允许后，应用获取访问媒体库接口的临时授权，相关接口请参见
[Interface (PhotoAccessHelper)]{@link @ohos.file.photoAccessHelper:photoAccessHelper.PhotoAccessHelper}；用户拒绝或关闭弹窗时，本次
* 不授权，应用不会获得媒体库接口访问权限。后续使用无需弹窗授权。
在API version 19及之前的版本中，授权持续时间为10秒；在API version 20及之后的版本中，授权持续时间为1分钟。
开发者应在授权有效期内调用媒体库接口获取文件句柄，并完成创建媒体资源等需要临时授权的操作。授权到期后，已通过授权获取的文件句柄仍可继续进行读写操作，不受授权时间限制。
<br>**说明**</br>
<ul><li>

## 核心枚举类型</li>

<li></li><li>**[SaveIconStyle]{@link SaveIconStyle}：** 保存控件图标风格枚举，用于指定控件展示的图标风格。</li><li>**[SaveDescription]{@link SaveDescription}：** 保存控件文本描述枚举，用于指定控件展示的文本描述。</li><li>**[SaveButtonOnClickResult]{@link SaveButtonOnClickResult}：** 保存控件点击结果枚举，用于表示点击后授权是否成功。</li><li></li><li>

## 核心接口类型</li>

<li></li><li>**[SaveButtonOptions]{@link SaveButtonOptions}：** 保存控件配置对象，用于指定图标、文字和按钮类型等元素属性。</li><li>**[SaveButtonCallback]{@link SaveButtonCallback}：** 保存控件点击回调类型，用于返回点击事件、授权结果和错误信息。</li><li></li><li>

## 子组件</li>

<li></li><li>不支持。</li></ul>

## SaveButton

```TypeScript
SaveButton()
```

默认创建带有图标、文本、背景的保存控件。用户首次使用保存控件时会展示弹窗，在点击允许后自动授权，应用会获取访问媒体库接口的临时授权。后续使用无需弹窗授权。<br>在API version 19及之前的版本中，授权持续时间为10秒。授权到期后，已通过授权获取的文件句柄仍可继续进行读写操作，不受授权时间限制。<br>在API version 20及之后的版本中，授权持续时间为1分钟。授权到期后，已通过授权获取的文件句柄仍可继续进行读写操作，不受授权时间限制。<br>**说明**</br><ul><li>为避免控件样式不合法导致授权失败，请开发者先了解安全控件样式的[约束与限制](docroot://security/AccessToken/security-component-overview.md#约束与限制)。</li></ul>

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SaveButtonInterface-(): SaveButtonAttribute--><!--Device-SaveButtonInterface-(): SaveButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SaveButton

```TypeScript
SaveButton(options: SaveButtonOptions)
```

创建包含指定图标、文本或按钮类型的保存控件。用户首次使用保存控件时会展示弹窗，在点击允许后自动授权，应用会获取访问媒体库接口的临时授权。后续使用无需弹窗授权。在API version 19及之前的版本中，授权持续时间为10秒。授权到期后，已通过授权获取的文件句柄仍可继续进行读写操作，不受授权时间限制。在API version 20及之后的版本中，授权持续时间为1分钟。授权到期后，已通过授权获取的文件句柄仍可继续进行读写操作，不受授权时间限制。<br>**说明**</br><ul><li>为避免控件样式不合法导致授权失败，请开发者先了解安全控件样式的[约束与限制](docroot://security/AccessToken/security-component-overview.md#约束与限制)。</li></ul>

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SaveButtonInterface-(options: SaveButtonOptions): SaveButtonAttribute--><!--Device-SaveButtonInterface-(options: SaveButtonOptions): SaveButtonAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | SaveButtonOptions | 是 | 保存控件的配置选项，用于指定图标、文本和按钮类型等元素属性。<br>建议至少显式设置 icon 或 text 中的一项，以确保用户能明确理解控件用途；若两者都不传，控件显示为默认样式。 |

## 汇总

- [SaveButtonOptions](arkts-arkui-savebutton-savebuttonoptions-i.md)
- [SaveButtonCallback](arkts-arkui-savebutton-savebuttoncallback-t.md)
- [SaveButtonOnClickResult](arkts-arkui-savebutton-savebuttononclickresult-e.md)
- [SaveDescription](arkts-arkui-savebutton-savedescription-e.md)
- [SaveIconStyle](arkts-arkui-savebutton-saveiconstyle-e.md)

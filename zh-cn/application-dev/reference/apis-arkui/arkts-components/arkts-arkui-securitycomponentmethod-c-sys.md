# SecurityComponentMethod

安全控件通用属性模块，提供安全控件的布局、尺寸、文字、图标、颜色、边框和交互等通用属性的统一配置能力。
- 为[PasteButton](./paste_button)、[SaveButton](./save_button)等安全控件统一设置布局、尺寸、文字、图标、颜色、边框和交互相关属性。
- 在满足安全控件规范的前提下，调整安全控件显示效果和交互体验。具体约束请参见[约束与限制](../../../../security/AccessToken/security-component-overview.md#约束与限制)。
- 通过链式调用方式复用安全控件通用属性能力。

###### 核心枚举类型
- **[SecurityComponentLayoutDirection](arkts-arkui-securitycomponentlayoutdirection-e.md)：** 安全控件图标和文字排列方向枚举，用于指定横向或纵向布局。
- **[ButtonType](@global:ButtonType)：** 安全控件按钮样式枚举，用于指定胶囊、圆形、圆角矩形或普通按钮样式。

###### 核心接口类型
- **[SecurityComponentMethod](arkts-arkui-securitycomponentmethod-c.md)：** 安全控件通用属性方法集合，用于为具体安全控件配置布局、尺寸、文字、图标、颜色、边框和交互属性。

###### 子组件
不支持

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key(value: string): T
```

设置组件的唯一标识，唯一性由开发者保证。调用成功后，组件将被赋予指定的唯一标识字符串，可在测试场景中精确定位该组件实例。与[id](arkts-arkui-securitycomponentmethod-c.md#id-1)
同时使用时，后设置的标识值会覆盖先设置的标识值，建议仅设置id。

此接口仅用于应用测试场景，验证安全控件的属性设置和交互行为。生产环境请使用公开接口[id](arkts-arkui-securitycomponentmethod-c.md#id-1)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 组件的唯一标识，唯一性由开发者保证。适用于测试场景中按标识精确定位安全控件实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 安全控件的属性。 |


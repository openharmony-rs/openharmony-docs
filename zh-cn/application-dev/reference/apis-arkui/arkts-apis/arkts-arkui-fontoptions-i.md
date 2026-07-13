# FontOptions

注册的自定义字体信息。

> **说明：**
>
> 直接使用font可能导致[UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的问题，推荐通过使用
> [UIContext](arkts-arkui-uicontext.md)中的
> [getFont](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont)方法获取当前UI上下文关联的
> [Font](arkts-arkui-uicontext.md)对象。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## familyName

```TypeScript
familyName: string | Resource
```

设置注册的字体名称。

**类型：** string | Resource

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## familySrc

```TypeScript
familySrc: string | Resource
```

设置注册字体文件的路径。

**说明：**

读取系统沙箱路径内的资源时，建议使用file://路径前缀的字符串，需要确保沙箱目录路径下的文件存在并且有可读权限。

**类型：** string | Resource

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full


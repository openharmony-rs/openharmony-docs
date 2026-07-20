# ImageSpan

[Text]{@link text}、[ContainerSpan]{@link container_span}组件的子组件，用于显示行内图片。

> **说明：**

> - 本模块接口仅可在Stage模型下使用。

## 子组件

无

## ImageSpan

```TypeScript
ImageSpan(value: ResourceStr | PixelMap)
```

定义ImageSpan组件构造函数。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ImageSpanInterface-(value: ResourceStr | PixelMap): ImageSpanAttribute--><!--Device-ImageSpanInterface-(value: ResourceStr | PixelMap): ImageSpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) \| PixelMap | 是 | 图片的数据源，支持本地图片和网络图片。<br/>当使用相对路径引用图片资源时，例如`ImageSpan("common/test.jpg")`，不 支持跨包/跨模块调用该ImageSpan组件，建议使用`$r`方式来管理需全局使用的图片资源。<br/>- 支持的图片格式包括png、jpg、bmp、svg、gif和heif。<br/>- 支持`Base64`字符串。格式 `data:image/[png\|jpeg\|bmp\|webp\|heif];base64,[base64 data]`，其中`[base64 data]`为`Base64`字符串数据。<br/>- 支持file://data /storage路径前缀的字符串，用于读取本应用安装目录下file文件夹下的图片资源。需要保证目录包路径下的文件有可读权限。  |

## 汇总

- [ImageLoadResult](arkts-arkui-imagespan-imageloadresult-i.md)
- [ImageCompleteCallback](arkts-arkui-imagespan-imagecompletecallback-t.md)

# ImageSpan

ImageSpan是Text、ContainerSpan组件的子组件，用于在文本中显示行内图片，支持设置图片对齐方式、缩放类型、加载占位图和颜色滤镜等，适用于需要在文本段落中嵌入图片实现图文混排的场景。

## 子组件

无

## ImageSpan

```TypeScript
ImageSpan(value: ResourceStr | PixelMap)
```

定义ImageSpan组件构造函数。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**测试接口：** 此接口仅在自动化测试脚本中使用。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [PixelMap](arkts-arkui-pixelmap-t.md) | 是 | 图片的数据源，支持本地图片和网络图片。<br>使用网络图片时，需要申请权限ohos.permission.INTERNET。具体申请方式请参考[声明权限](../../../security/AccessToken/declare-permissions.md)。<br>当使用相对路径引用图片资源时，例如`ImageSpan("common/test.jpg")`，不支持跨包/跨模块调用该ImageSpan组件，建议使用`&#36;r`方式来管理需全局使用的图片资源。<br>- 支持的图片格式包括png、jpg、bmp、svg、gif、webp和heif。<br>- 支持`Base64`字符串。格式`data:image/[png&#124;jpeg&#124;bmp&#124;webp&#124;heif];base64,[base64 data]`，其中`[base64 data]`为`Base64`字符串数据。<br>- 支持file://data/storage路径前缀的字符串，用于读取本应用安装目录下file文件夹下的图片资源。需要保证应用安装目录路径下的文件有可读权限。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ImageLoadResult](arkts-arkui-imageloadresult-i.md) | 图片数据加载成功和解码成功触发回调时返回的对象。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ImageCompleteCallback](arkts-arkui-imagecompletecallback-t.md) | 图片加载成功和解码成功时均触发的回调。 |

## 示例

```TypeScript
### 示例1（设置对齐方式）

从API version 10开始，该示例通过[verticalAlign](#verticalalign)、[objectFit](#objectfit)属性展示了ImageSpan组件的对齐方式以及缩放效果。


```

```TypeScript
### 示例2（设置背景样式）

从API version 11开始，该示例通过[textBackgroundStyle](ts-basic-components-span.md#textbackgroundstyle11)属性展示了文本设置背景样式的效果。


```

```TypeScript
### 示例3（为图片添加事件）

从API version 12开始，该示例通过[onComplete](#oncomplete12)、[onError](#onerror12)为图片添加加载成功和加载异常的事件。
```

```TypeScript
### 示例4（设置颜色滤镜）

从API version 14开始，该示例通过[colorFilter](#colorfilter14)属性展示了给ImageSpan图像设置颜色滤镜的效果。


```

```TypeScript
### 示例5（设置加载占位图）

从API version 12开始，该示例通过[alt](#alt12)属性展示了ImageSpan设置加载网络图片时占位图的效果。

使用网络图片时，需要申请权限ohos.permission.INTERNET。具体申请方式请参考[声明权限](../../../security/AccessToken/declare-permissions.md)。


```

```TypeScript
### 示例6（使用supportSvg2属性时，SVG图片的显示效果）

从API version 22开始，该示例通过设置[supportSvg2](#supportsvg222)属性，使[SVG标签解析能力增强功能](ts-image-svg2-capabilities.md)的[SVG易用性提升](ts-image-svg2-capabilities.md#svg易用性提升)能力生效。


```

```TypeScript
### 示例7（设置图片拉伸）

该示例通过[resizable](#resizable)属性的slice选项，对ImageSpan图片不同方向进行拉伸。

从API版本26.1.0开始，新增resizable属性。
```

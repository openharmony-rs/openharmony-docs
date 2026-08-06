# ImageSpan

ImageSpan是[Text]{@link ./text}、[ContainerSpan]{@link ./container_span}组件的子组件，用于在文本中显示行内图片，支持设置图片对齐方式、缩放类型、加载占位图和颜色滤镜 等，适用于需要在文本段落中嵌入图片实现图文混排的场景。

## 子组件 无

## ImageSpan

```TypeScript
ImageSpan(value: ResourceStr | PixelMap)
```

定义ImageSpan组件构造函数。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ImageSpanInterface-(value: ResourceStr | PixelMap): ImageSpanAttribute--><!--Device-ImageSpanInterface-(value: ResourceStr | PixelMap): ImageSpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| PixelMap | 是 | 图片的数据源，支持本地图片和网络图片。 \_\_\_HTML\_TAG\_USD\_7\_\_\_使用网络图片时，需要申请权限ohos.permission.INTERNET。具体申请方式请参考 \_\_\_MD\_LINK\_USD\_6\_\_\_。 \_\_\_HTML\_TAG\_USD\_8\_\_\_当使用相对路径引用图片资源时，例如\_\_\_INLINE\_CODE\_USD\_0\_\_\_，不支持跨包/跨模块调用该ImageSpan组件，建议使用\_\_\_INLINE\_CODE\_USD\_1\_\_\_方式来管理需全局使用的图片资源。 \_\_\_HTML\_TAG\_USD\_9\_\_\_- 支持的图片格式包括png、jpg、bmp、svg、gif、webp和heif。 \_\_\_HTML\_TAG\_USD\_10\_\_\_- 支持\_\_\_INLINE\_CODE\_USD\_2\_\_\_字符串。格式\_\_\_INLINE\_CODE\_USD\_3\_\_\_，其中\_\_\_INLINE\_CODE\_USD\_4\_\_\_为\_\_\_INLINE\_CODE\_USD\_5\_\_\_字符串数 据。 \_\_\_HTML\_TAG\_USD\_11\_\_\_- 支持file://data/storage路径前缀的字符串，用于读取本应用安装目录下file文件夹下的图片资源。需要保证应用安装目录路径下的文件有可读权限。  |

## 汇总


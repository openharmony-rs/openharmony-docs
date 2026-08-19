# OnNativeEmbedObjectParamChangeCallback

```TypeScript
export type OnNativeEmbedObjectParamChangeCallback = (event: NativeEmbedParamDataInfo) => void
```

The callback when the param element which is a child item of the object element has changed.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export type OnNativeEmbedObjectParamChangeCallback = (event: NativeEmbedParamDataInfo) => void--><!--Device-unnamed-export type OnNativeEmbedObjectParamChangeCallback = (event: NativeEmbedParamDataInfo) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [NativeEmbedParamDataInfo](arkts-na-web-nativeembedparamdatainfo-i.md) | 是 | callback information of param element. |


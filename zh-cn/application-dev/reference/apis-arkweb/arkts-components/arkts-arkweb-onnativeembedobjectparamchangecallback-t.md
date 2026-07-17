# OnNativeEmbedObjectParamChangeCallback

```TypeScript
type OnNativeEmbedObjectParamChangeCallback = (event: NativeEmbedParamDataInfo) => void
```

增加、修改或删除同层渲染object标签内嵌param元素时触发此回调。

**起始版本：** 21

<!--Device-unnamed-type OnNativeEmbedObjectParamChangeCallback = (event: NativeEmbedParamDataInfo) => void--><!--Device-unnamed-type OnNativeEmbedObjectParamChangeCallback = (event: NativeEmbedParamDataInfo) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | NativeEmbedParamDataInfo | 是 | object标签内嵌param元素的详细变化信息。 |


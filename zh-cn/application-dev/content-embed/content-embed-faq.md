# Content Embed Kit常见问题
<!--Kit: Content Embed Kit-->
<!--Subsystem: officeservice -->
<!--Owner: @weiguoning-->
<!--Designer: @zhuwei-->
<!--Tester: @zhaotianyu-->
<!--Adviser: @jinqiuheng-->

## 如何根据需求选择链接或嵌入模式来创建OE文档

客户端开发者在调用[OH_ContentEmbed_CreateDocumentByFile](../reference/apis-content-embed-kit/capi-content-embed-document-h.md#oh_contentembed_createdocumentbyfile)创建OE文档时，可根据是否需要同步源文件变更来设置isLinking参数。

- 当isLinking为true时，表示以链接方式创建OE文档。当服务端编辑OE文档时，源文件也会被修改。如果源文件被移动、删除或者重命名时，OE文档启动编辑会失败，如果用户在文件管理器中恢复原始源文件需要应用进行授权。同时链接方式不支持链接到客户端应用的沙箱目录。
- 当isLinking为false时，表示以嵌入方式创建OE文档。当客户端请求服务端编辑OE文档时，会先拷贝一份临时文件到客户端应用沙箱目录。服务端对OE文档修改时，不会修改源文件。当客户端正常退出时会清空创建的临时文件。

## 客户端基于文件创建OE文档时如何显示文档快照或应用图标

客户端基于[OH_ContentEmbed_CreateDocumentByFile](../reference/apis-content-embed-kit/capi-content-embed-document-h.md#oh_contentembed_createdocumentbyfile)创建文档时，客户端需要通过[OH_ContentEmbed_Proxy_GetCapability](../reference/apis-content-embed-kit/capi-content-embed-proxy-h.md#oh_contentembed_proxy_getcapability)查询OE Extension是否支持获取快照。

- 如果服务端不支持快照时，客户端可以通过<!--RP1-->[OH_NativeBundle_GetAbilityResourceInfo](../reference/apis-ability-kit/capi-native-interface-bundle-h.md#oh_nativebundle_getabilityresourceinfo)获取文件类型的组件资源信息列表。<!--RP1End-->
- 如果服务端支持获取快照时，客户端可以通过[OH_ContentEmbed_Proxy_GetSnapshot](../reference/apis-content-embed-kit/capi-content-embed-proxy-h.md#oh_contentembed_proxy_getsnapshot)获取快照信息。

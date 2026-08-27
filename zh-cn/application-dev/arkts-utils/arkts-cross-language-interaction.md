# ArkTS跨语言交互
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @xliu-huanwei; @shilei123; @huanghello-->
<!--Designer: @shilei123-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

除了支持使用ArkTS开发外，开发者还可以通过Node-API实现ArkTS与C/C++(Native)的跨语言交互能力。

OpenHarmony的Node-API是基于Node.js社区版本的扩展实现，但与原生Node-API并不完全兼容。

开发者可参考使用Node-API进行跨语言开发流程，基于Node-API支持的数据类型和Node-API接口进行Native能力的开发和封装，并通过在ArkTS侧导入Native模块的方式实现跨语言调用。

Node-API扩展能力接口提供了增强功能，支持更灵活的ArkTS交互和自定义对象创建。开发者可结合Node-API的扩展能力进行功能扩展，并参考Node-API开发规范和Node-API常见问题进行跨语言功能开发。

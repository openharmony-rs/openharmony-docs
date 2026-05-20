# Data Protection Kit（数据保护服务）
Data Protection Kit 提供数据防泄漏和敏感内容识别能力，帮助开发者保护应用中的敏感数据安全。 
**主要功能**： 
- 数据防泄漏：防止敏感数据被未授权访问和泄露 
- 敏感内容识别：自动识别文档中的敏感信息 
**适用场景**： 
- 企业办公应用中的文档保护
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @QRF-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

- ArkTS（方舟开发框架） API<!--data-protection-arkts-->
  - [@ohos.dlpPermission (数据防泄漏)](js-apis-dlppermission.md)
  - [@ohos.security.identifySensitiveContent (识别敏感内容)](js-apis-identifySensitiveContent.md)
  <!--Del-->
  - [@ohos.dlpPermission (数据防泄漏)(系统接口)](js-apis-dlppermission-sys.md)
  - [@ohos.dlpSetDlpFeature (设置数据防泄漏入口)(系统接口)](js-apis-dlpsetdlpfeature-sys.md)
  <!--DelEnd-->
- C API<!--data-protection-c-->
  - 模块<!--data-protection-module-->
    - [DlpPermissionApi](capi-dlppermissionapi.md)
  - 头文件<!--data-protection-headerfile-->
    - [dlp_permission_api.h](capi-dlp-permission-api-h.md)
- 错误码<!--data-protection-arkts-errcode-->
  - [DLP服务错误码](errorcode-dlp.md)

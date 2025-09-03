# 应用安装与更新一致性校验
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @Brilliantry_Rui-->

随着应用发展越来越复杂，应用也被拆成多个模块进行开发维护，不同的团队负责单个或者多个模块，应用在安装更新过程中会针对不同的字段进行一致性校验和验证，保证应用的安全合法性。本文介绍多模块安装或更新时，签名证书、配置文件的一致性校验规则。

>
> **说明**
>
> [app.json5配置文件](./app-configuration-file.md)中versionCode字段一致，表示安装或更新包同版本，否则为不同版本。
>
> 使用打包工具进行打包时，会进行合法性校验。详情请参考[打包工具](../../application-dev/tools/packing-tool.md)。

## 签名证书一致性校验

|字段名称|说明|安装一致性校验规则|更新一致性校验规则|
|--|--|--|--|
|appId|应用的appId，组成方式为bundleName_公钥的base64编码。|是|appId和appIdentifier任一相同即可。|
|appIdentifier|应用的唯一标识。<!--RP2-->来源于应用[Profile签名文件](../security/app-provision-structure.md)中的app-identifier。<!--RP2End-->|是|appId和appIdentifier任一相同即可。|
|appDistributionType|<!--RP1-->应用[Profile签名文件](../security/app-provision-structure.md)中的app-distribution-type，标识应用的分发类型。<!--RP1End-->|是|更新不同版本时无校验，同版本有校验。|
|appProvisionType|应用签名证书类型。<!--RP3-->来源于应用[Profile签名文件](../security/app-provision-structure.md)中的type。分为debug和release。debug用于本地调试使用，release用于应用发布场景。<!--RP3End-->|是|更新不同版本时无校验，同版本有校验。|
|apl|表示应用程序的[APL等级](../security/AccessToken/app-permission-mgmt-overview.md#权限机制中的基本概念)，系统定义的apl包括：normal、system_basic和system_core。|是|更新不同版本时无校验，同版本有校验。|


## 配置文件一致性校验

|字段名称|说明|安装一致性校验规则|更新一致性校验规则|
|--|--|--|--|
|bundleName|标识应用名称。该字段来源于[app.json5配置文件](./app-configuration-file.md)中的bundleName字段。|是|是|
|versionCode|标识应用版本号。该字段来源于[app.json5配置文件](./app-configuration-file.md)中的versionCode字段。从API version 18开始，HAP的版本号须大于等于HSP版本号。API version 17及之前版本，HSP的版本号必须与HAP版本号一致。|是|是|
|apiReleaseType|标识应用运行需要的API目标版本的类型。设备中未安装该应用，该应用包含多个模块包，模块一个一个安装时，不检验一致性。该字段来源于[app.json5配置文件](./app-configuration-file.md)中的apiReleaseType字段。|否|是|
|<!--DelRow--> singleton|标识应用是否安装在0用户下。|否|是|
|<!--DelRow--> appType|标识应用是三方应用或系统应用。|是|是|
|<!--DelRow--> isStage|标识应用是否为Stage模型。|是，FA模型和Stage模型在同版本中不允许变更。|否|
|targetBundleName|标识当前包所指定的目标应用，配置该字段的应用为具有overlay特征的应用。该字段来源[app.json5配置文件](./app-configuration-file.md)中targetBundleName字段。|是|是|
|targetPriority|标识当前应用的优先级。该字段来源于[app.json5配置文件](./app-configuration-file.md)中的targetPriority字段。|是|是|
|bundleType|标识应用的类型。该字段来源于[app.json5配置文件](./app-configuration-file.md)中的bundleType字段。|是|是|
|installationFree|标识是否支持免安装。该字段来源于[module.json5配置文件](./module-configuration-file.md)中的installationFree字段。|是|是|
|debug|标识应用是否可调试。该字段来源于[app.json5配置文件](./app-configuration-file.md)中的debug字段。|是|否|
|moduleType|标识模块的类型。该字段来源于[module.json5配置文件](./module-configuration-file.md)中的type字段。|是，同版本entry类型的moduleName不能修改|是|


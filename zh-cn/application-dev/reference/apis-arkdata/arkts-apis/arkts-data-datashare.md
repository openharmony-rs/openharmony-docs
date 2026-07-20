# @ohos.data.dataShare

**DataShare**用于应用管理其自身数据，同时支持同个设备上不同应用间的数据共享。

**起始版本：** 20

<!--Device-unnamed-declare namespace dataShare--><!--Device-unnamed-declare namespace dataShare-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createDataProxyHandle](arkts-arkdata-datashare-createdataproxyhandle-f.md#createdataproxyhandle) | 创建DataProxyHandle实例。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createDataShareHelper](arkts-arkdata-datashare-createdatasharehelper-f-sys.md#createdatasharehelper) | 创建DataShareHelper实例。使用callback异步回调。 |
| [createDataShareHelper](arkts-arkdata-datashare-createdatasharehelper-f-sys.md#createdatasharehelper-1) | 创建DataShareHelper实例，通过DataShareHelperOptions指定是否通过代理访问。使用callback异步回调。 |
| [createDataShareHelper](arkts-arkdata-datashare-createdatasharehelper-f-sys.md#createdatasharehelper-2) | 创建DataShareHelper实例，通过DataShareHelperOptions指定是否通过代理访问。使用Promise异步回调。 |
| [disableSilentProxy](arkts-arkdata-datashare-disablesilentproxy-f-sys.md#disablesilentproxy) | 关闭静默访问。使用Promise异步回调。  使用规则：  - 数据提供方调用此接口，来关闭静默访问功能。  - 此接口设置的关闭结果在校验的时候是搭配data_share_config.json文件中isSilentProxyEnable字段进行工作的。支持的配置可参考[data_share_config.json配置](docroot://database/share-data-by-datashareextensionability-sys.md)。  - 此接口生效在调用datashareHelper相关接口过程中，如果此接口有关闭过相关uri，那么会按照此接口的配置来关闭静默访问。如果此接口未调用过，则会读取data_share_config.json中的配置来校验Datashare的关闭状态。 |
| [enableSilentProxy](arkts-arkdata-datashare-enablesilentproxy-f-sys.md#enablesilentproxy) | 开启静默访问。使用Promise异步回调。  使用规则：  - 数据提供方调用此接口，来开启静默访问功能。  - 此接口设置的开启结果在校验的时候是搭配data_share_config.json文件中isSilentProxyEnable字段进行工作的。支持的配置可参考[data_share_config.json配置](docroot://database/share-data-by-datashareextensionability-sys.md)。  - 此接口生效在调用datashareHelper相关接口过程中，如果此接口有开启过相关uri，那么会按照此接口的配置来开启静默访问。如果此接口未调用过，则会读取data_share_config.json中的配置来校验Datashare的开启状态。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [DataProxyChangeInfo](arkts-arkdata-datashare-dataproxychangeinfo-i.md) | 通知订阅者共享配置变更的数据结构。包括数据变更类型、变化的URI、变更的数据内容。 |
| [DataProxyConfig](arkts-arkdata-datashare-dataproxyconfig-i.md) | 数据代理操作配置的数据结构。 |
| [DataProxyGetResult](arkts-arkdata-datashare-dataproxygetresult-i.md) | 配置共享批量获取操作结果的数据结构。 |
| [DataProxyHandle](arkts-arkdata-datashare-dataproxyhandle-i.md) | 数据代理操作句柄的实例，可使用此实例访问或管理共享配置信息。在调用DataProxyHandle提供的方法前，需要先通过[createDataProxyHandle](arkts-arkdata-datashare-createdataproxyhandle-f.md#createdataproxyhandle-1)构建一个实例。 |
| [DataProxyResult](arkts-arkdata-datashare-dataproxyresult-i.md) | 配置共享批量操作结果的数据结构。 |
| [ProxyData](arkts-arkdata-datashare-proxydata-i.md) | 共享配置的数据结构。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ChangeInfo](arkts-arkdata-datashare-changeinfo-i-sys.md) | 数据变更时通知用户具体变更的内容，包括数据变更类型、变化的uri、变更的数据内容。 |
| [DataShareHelper](arkts-arkdata-datashare-datasharehelper-i-sys.md) | DataShare管理工具实例，可使用此实例访问或管理服务端的数据。在调用DataShareHelper提供的方法前，需要先通过[createDataShareHelper](arkts-arkdata-datashare-createdatasharehelper-f-sys.md#createdatasharehelper-1)构建一个实例。 |
| [DataShareHelperOptions](arkts-arkdata-datashare-datasharehelperoptions-i-sys.md) | 指定[DataShareHelper](arkts-arkdata-datashare-datasharehelperoptions-i-sys.md)的可选参数，包含是否在代理模式下，以及非静默访问的拉起等待时间。 |
| [OperationResult](arkts-arkdata-datashare-operationresult-i-sys.md) | 订阅/取消订阅数据变更和发布数据的操作结果。 |
| [PublishedDataChangeNode](arkts-arkdata-datashare-publisheddatachangenode-i-sys.md) | 订阅/取消订阅已发布数据变更的结果。 |
| [PublishedItem](arkts-arkdata-datashare-publisheditem-i-sys.md) | 指定发布的数据类型。 |
| [RdbDataChangeNode](arkts-arkdata-datashare-rdbdatachangenode-i-sys.md) | 订阅/取消订阅RDB数据变更的结果，回调支持传输不大于10M的数据。 |
| [Template](arkts-arkdata-datashare-template-i-sys.md) | 指定订阅中的模板结构。 |
| [TemplateId](arkts-arkdata-datashare-templateid-i-sys.md) | 标记模板的数据结构，TemplateId是在[addTemplate](arkts-arkdata-datashare-datasharehelper-i-sys.md#addtemplate-1)中自动生成的，在[addTemplate](arkts-arkdata-datashare-datasharehelper-i-sys.md#addtemplate-1)后，可以使用模板id来标记模板。 |
| [UpdateOperation](arkts-arkdata-datashare-updateoperation-i-sys.md) | 批量更新操作的参数结构。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DataProxyErrorCode](arkts-arkdata-datashare-dataproxyerrorcode-e.md) | 配置共享批量操作返回值的状态码枚举。 |
| [DataProxyMaxValueLength](arkts-arkdata-datashare-dataproxymaxvaluelength-e.md) | [共享配置](arkts-arkdata-datashare-proxydata-i.md)的值允许的最大长度的枚举值。 |
| [DataProxyType](arkts-arkdata-datashare-dataproxytype-e.md) | 数据代理类型的枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ChangeType](arkts-arkdata-datashare-changetype-e-sys.md) | 数据变更类型枚举。 |
| [SubscriptionType](arkts-arkdata-datashare-subscriptiontype-e-sys.md) | 数据订阅类型枚举。 |
<!--DelEnd-->


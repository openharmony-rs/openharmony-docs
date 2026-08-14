# @ohos.app.ability.insightIntentDriver

本模块提供执行意图调用的能力，系统根据用户交互等信息执行意图调用。 > **说明：** > > 本模块从API version 20开始支持通过 > @InsightIntentLink > 装饰器定义的意图来实现应用跳转。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace insightIntentDriver--><!--Device-unnamed-declare namespace insightIntentDriver-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [execute](arkts-ability-insightintentdriver-execute-f-sys.md#execute) | 执行意图调用的接口。使用callback异步回调。 当调用方在后台时，需要申请`ohos.permission.START_ABILITIES_FROM_BACKGROUND`权限。 当意图调用执行模式[ExecuteMode](arkts-ability-insightintent-executemode-e.md#ExecuteMode)取值为UI_ABILITY_BACKGROUND时，需要 申请`ohos.permission.ABILITY_BACKGROUND_COMMUNICATION`权限。 |
| [execute](arkts-ability-insightintentdriver-execute-f-sys.md#execute（系统接口）) | 执行意图调用的接口。使用Promise异步回调。 当调用方在后台时，需要申请`ohos.permission.START_ABILITIES_FROM_BACKGROUND`权限。 当意图调用执行模式[ExecuteMode](arkts-ability-insightintent-executemode-e.md#ExecuteMode)取值为UI_ABILITY_BACKGROUND时，需要 申请`ohos.permission.ABILITY_BACKGROUND_COMMUNICATION`权限。 |
| [getAllInsightIntentInfo](arkts-ability-insightintentdriver-getallinsightintentinfo-f-sys.md#getAllInsightIntentInfo) | 查询当前设备上的所有意图信息。使用Promise异步回调。 |
| [getInsightIntentInfoByBundleName](arkts-ability-insightintentdriver-getinsightintentinfobybundlename-f-sys.md#getInsightIntentInfoByBundleName) | 根据包名查询当前设备上的意图信息。使用Promise异步回调。 |
| [getInsightIntentInfoByFilter](arkts-ability-insightintentdriver-getinsightintentinfobyfilter-f-sys.md#getInsightIntentInfoByFilter) | Obtains the intent information on the current device based on the given intent filter. This API uses a promise to return the result.&lt;br&gt;If the user ID of the calling application is different from the user ID of the intent, the |
| [getInsightIntentInfoByIntentName](arkts-ability-insightintentdriver-getinsightintentinfobyintentname-f-sys.md#getInsightIntentInfoByIntentName) | 根据包名、模块名和意图名查询当前设备上的意图信息。使用Promise异步回调。 |
| [queryEntityInfo](arkts-ability-insightintentdriver-queryentityinfo-f-sys.md#queryEntityInfo) | 查询意图实体信息。 |
| [queryEntityInfo](arkts-ability-insightintentdriver-queryentityinfo-f-sys.md#queryEntityInfo（系统接口）) | 查询意图实体信息。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [FunctionIntentInfo](arkts-ability-insightintentdriver-functionintentinfo-i.md) | @InsightIntentFunctionMethod 装饰器的参数类型，当前全部属性均继承自[IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md#IntentDecoratorInfo)。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [EntityInfo](arkts-ability-insightintentdriver-entityinfo-i-sys.md) | EntityInfo继承自[IntentEntityDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intententitydecoratorinfo-i.md#IntentEntityDecoratorInfo)， 用于描述 @InsightIntentEntity 装饰器定义的意图实体的信息。 |
| [EntryIntentInfo](arkts-ability-insightintentdriver-entryintentinfo-i-sys.md) | FormIntentInfo用于描述 @InsightIntentForm 装饰器支持的参数，例如卡片名称。同时，该接口也可用于描述[使用配置文件开发的意图](../../../application-models/insight-intent-config-development.md)所绑定的卡片信 息。 |
| [ExecuteParam](arkts-ability-insightintentdriver-executeparam-i-sys.md) | 执行意图调用的参数。 |
| [FormIntentInfo](arkts-ability-insightintentdriver-formintentinfo-i-sys.md) | FormIntentInfo用于描述 @InsightIntentForm 装饰器支持的参数，例如卡片名称。同时，该接口也可用于描述[使用配置文件开发的意图](../../../application-models/insight-intent-config-development.md)所绑定的卡片信 息。 |
| [InsightIntentInfo](arkts-ability-insightintentdriver-insightintentinfo-i-sys.md) | 意图信息，表示设备中意图的具体参数配置。 |
| [InsightIntentInfoFilter](arkts-ability-insightintentdriver-insightintentinfofilter-i-sys.md) | 意图筛选器，描述目标意图的筛选条件，用于筛选设备上符合条件的意图。 |
| [LinkIntentInfo](arkts-ability-insightintentdriver-linkintentinfo-i-sys.md) | LinkIntentInfo用于描述 @InsightIntentLink 装饰器支持的参数，例如应用间跳转需要的uri信息。 |
| [PageIntentInfo](arkts-ability-insightintentdriver-pageintentinfo-i-sys.md) | PageIntentInfo用于描述 @InsightIntentPage 装饰器支持的参数，例如目标页面的 [NavDestination](../../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navdestination10)名称。 |
| [QueryParam](arkts-ability-insightintentdriver-queryparam-i-sys.md) | 查询洞察意图实体时的Param。 |
| [ServiceExtensionIntentInfo](arkts-ability-insightintentdriver-serviceextensionintentinfo-i-sys.md) | 用于描述[使用配置文件开发的意图](../../../application-models/insight-intent-config-development.md)所绑定的ServiceExtensionAbility组件信息 。 |
| [SubIntentInfoForConfiguration](arkts-ability-insightintentdriver-subintentinfoforconfiguration-i-sys.md) | 用于描述[使用配置文件开发的意图](../../../application-models/insight-intent-config-development.md)的特有信息。 |
| [UIAbilityIntentInfo](arkts-ability-insightintentdriver-uiabilityintentinfo-i-sys.md) | 用于描述[使用配置文件开发的意图](../../../application-models/insight-intent-config-development.md)所绑定的UIAbility组件信息。 |
| [UIExtensionIntentInfo](arkts-ability-insightintentdriver-uiextensionintentinfo-i-sys.md) | 用于描述[使用配置文件开发的意图](../../../application-models/insight-intent-config-development.md)所绑定的UIExtensionAbility组件信息。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DevelopType](arkts-ability-insightintentdriver-developtype-e-sys.md) | 用于描述意图的开发方式。 |
| [ExecuteModeForConfiguration](arkts-ability-insightintentdriver-executemodeforconfiguration-e-sys.md) | [使用配置文件开发的意图](../../../application-models/insight-intent-config-development.md)支持的意图执行模式。例如，将 [insight_intent.json配置文件](../../../application-models/insight-intent-config-development.md#insight_intentjson配置文件说明) 中的executeMode设置为"foreground"，表示支持与UIAbility组件绑定的意图在前台运行。 |
| [GetInsightIntentFlag](arkts-ability-insightintentdriver-getinsightintentflag-e-sys.md) | 意图信息（[InsightIntentInfo](arkts-ability-insightintentdriver-insightintentinfo-i-sys.md#InsightIntentInfo（系统接口）)）的标识，用于 [getAllInsightIntentInfo](arkts-ability-insightintentdriver-getinsightintentinfobybundlename-f-sys.md#getInsightIntentInfoByBundleName（系统接口）)、 [getInsightIntentInfoByBundleName](arkts-ability-insightintentdriver-getinsightintentinfobybundlename-f-sys.md#getInsightIntentInfoByBundleName（系统接口）)和 [getInsightIntentInfoByIntentName](arkts-ability-insightintentdriver-getinsightintentinfobyintentname-f-sys.md#getInsightIntentInfoByIntentName（系统接口）)接口查询意图信息。 |
| [InsightIntentType](arkts-ability-insightintentdriver-insightintenttype-e-sys.md) | 表示通过意图装饰器定义的意图类型，可通过[getAllInsightIntentInfo](arkts-ability-insightintentdriver-getallinsightintentinfo-f-sys.md#getAllInsightIntentInfo（系统接口）)等方法返回的 [LinkIntentInfo](arkts-ability-insightintentdriver-linkintentinfo-i-sys.md#LinkIntentInfo（系统接口）)获取。 |
<!--DelEnd-->


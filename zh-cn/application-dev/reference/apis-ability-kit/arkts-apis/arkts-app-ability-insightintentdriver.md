# @ohos.app.ability.insightIntentDriver

本模块提供执行意图调用的能力，系统根据用户交互等信息执行意图调用。

> **说明：**
>
> 本模块从API version 20开始支持通过
> [@InsightIntentLink](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink)
> 装饰器定义的意图来实现应用跳转。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[execute](arkts-ability-insightintentdriver-execute-f-sys.md#execute-1) | 执行意图调用的接口。使用callback异步回调。<br/>当调用方在后台时，需要申请`ohos.permission.START_ABILITIES_FROM_BACKGROUND`权限。<br/>当意图调用执行模式[ExecuteMode](arkts-ability-insightintent-executemode-e.md#ExecuteMode)取值为UI_ABILITY_BACKGROUND时，需要<br/>申请`ohos.permission.ABILITY_BACKGROUND_COMMUNICATION`权限。<br/> |
| <!--DelRow-->[execute](arkts-ability-insightintentdriver-execute-f-sys.md#execute-2) | 执行意图调用的接口。使用Promise异步回调。<br/>当调用方在后台时，需要申请`ohos.permission.START_ABILITIES_FROM_BACKGROUND`权限。<br/>当意图调用执行模式[ExecuteMode](arkts-ability-insightintent-executemode-e.md#ExecuteMode)取值为UI_ABILITY_BACKGROUND时，需要<br/>申请`ohos.permission.ABILITY_BACKGROUND_COMMUNICATION`权限。<br/> |
| <!--DelRow-->[getAllInsightIntentInfo](arkts-ability-insightintentdriver-getallinsightintentinfo-f-sys.md#getAllInsightIntentInfo-1) | 查询当前设备上的所有意图信息。使用Promise异步回调。<br/> |
| <!--DelRow-->[getInsightIntentInfoByBundleName](arkts-ability-insightintentdriver-getinsightintentinfobybundlename-f-sys.md#getInsightIntentInfoByBundleName-1) | 根据包名查询当前设备上的意图信息。使用Promise异步回调。<br/> |
| <!--DelRow-->[getInsightIntentInfoByFilter](arkts-ability-insightintentdriver-getinsightintentinfobyfilter-f-sys.md#getInsightIntentInfoByFilter-1) | Obtains the intent information on the current device based on the given intent filter. This API uses a promise to<br/>return the result.&lt;br&gt;If the user ID of the calling application is different from the user ID of the intent, the<br/> |
| <!--DelRow-->[getInsightIntentInfoByIntentName](arkts-ability-insightintentdriver-getinsightintentinfobyintentname-f-sys.md#getInsightIntentInfoByIntentName-1) | 根据包名、模块名和意图名查询当前设备上的意图信息。使用Promise异步回调。<br/> |
| <!--DelRow-->[queryEntityInfo](arkts-ability-insightintentdriver-queryentityinfo-f-sys.md#queryEntityInfo-1) | 查询意图实体信息。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[EntityInfo](arkts-ability-insightintentdriver-entityinfo-i-sys.md) | EntityInfo继承自[IntentEntityDecoratorInfo](arkts-ability-intententitydecoratorinfo-i.md#IntentEntityDecoratorInfo)，<br/>用于描述<br/>[@InsightIntentEntity](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententity)<br/>装饰器定义的意图实体的信息。<br/> |
| <!--DelRow-->[EntryIntentInfo](arkts-ability-insightintentdriver-entryintentinfo-i-sys.md) | FormIntentInfo用于描述<br/>[@InsightIntentForm](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentform)<br/>装饰器支持的参数，例如卡片名称。同时，该接口也可用于描述[使用配置文件开发的意图](../../../../application-models/insight-intent-config-development.md)所绑定的卡片信<br/>息。<br/> |
| <!--DelRow-->[ExecuteParam](arkts-ability-insightintentdriver-executeparam-i-sys.md) | 执行意图调用的参数。<br/> |
| <!--DelRow-->[FormIntentInfo](arkts-ability-insightintentdriver-formintentinfo-i-sys.md) | FormIntentInfo用于描述<br/>[@InsightIntentForm](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentform)<br/>装饰器支持的参数，例如卡片名称。同时，该接口也可用于描述[使用配置文件开发的意图](../../../../application-models/insight-intent-config-development.md)所绑定的卡片信<br/>息。<br/> |
| [FunctionIntentInfo](arkts-ability-insightintentdriver-functionintentinfo-i.md) | [@InsightIntentFunctionMethod](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentfunctionmethod)<br/>装饰器的参数类型，当前全部属性均继承自[IntentDecoratorInfo](arkts-ability-intentdecoratorinfo-i.md#IntentDecoratorInfo)。<br/> |
| <!--DelRow-->[InsightIntentInfo](arkts-ability-insightintentdriver-insightintentinfo-i-sys.md) | 意图信息，表示设备中意图的具体参数配置。<br/> |
| <!--DelRow-->[InsightIntentInfoFilter](arkts-ability-insightintentdriver-insightintentinfofilter-i-sys.md) | 意图筛选器，描述目标意图的筛选条件，用于筛选设备上符合条件的意图。<br/> |
| <!--DelRow-->[LinkIntentInfo](arkts-ability-insightintentdriver-linkintentinfo-i-sys.md) | LinkIntentInfo用于描述<br/>[@InsightIntentLink](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink)<br/>装饰器支持的参数，例如应用间跳转需要的uri信息。<br/> |
| <!--DelRow-->[PageIntentInfo](arkts-ability-insightintentdriver-pageintentinfo-i-sys.md) | PageIntentInfo用于描述<br/>[@InsightIntentPage](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentpage)<br/>装饰器支持的参数，例如目标页面的<br/>[NavDestination](../../../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navdestination10)名称。<br/> |
| <!--DelRow-->[QueryParam](arkts-ability-insightintentdriver-queryparam-i-sys.md) | 查询洞察意图实体时的Param。<br/> |
| <!--DelRow-->[ServiceExtensionIntentInfo](arkts-ability-insightintentdriver-serviceextensionintentinfo-i-sys.md) | 用于描述[使用配置文件开发的意图](../../../../application-models/insight-intent-config-development.md)所绑定的ServiceExtensionAbility组件信息<br/>。<br/> |
| <!--DelRow-->[SubIntentInfoForConfiguration](arkts-ability-insightintentdriver-subintentinfoforconfiguration-i-sys.md) | 用于描述[使用配置文件开发的意图](../../../../application-models/insight-intent-config-development.md)的特有信息。<br/> |
| <!--DelRow-->[UIAbilityIntentInfo](arkts-ability-insightintentdriver-uiabilityintentinfo-i-sys.md) | 用于描述[使用配置文件开发的意图](../../../../application-models/insight-intent-config-development.md)所绑定的UIAbility组件信息。<br/> |
| <!--DelRow-->[UIExtensionIntentInfo](arkts-ability-insightintentdriver-uiextensionintentinfo-i-sys.md) | 用于描述[使用配置文件开发的意图](../../../../application-models/insight-intent-config-development.md)所绑定的UIExtensionAbility组件信息。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[DevelopType](arkts-ability-insightintentdriver-developtype-e-sys.md) | 用于描述意图的开发方式。<br/> |
| <!--DelRow-->[ExecuteModeForConfiguration](arkts-ability-insightintentdriver-executemodeforconfiguration-e-sys.md) | [使用配置文件开发的意图](../../../../application-models/insight-intent-config-development.md)支持的意图执行模式。例如，将<br/>[insight_intent.json配置文件](../../../../application-models/insight-intent-config-development.md#insight_intentjson配置文件说明)<br/>中的executeMode设置为"foreground"，表示支持与UIAbility组件绑定的意图在前台运行。<br/> |
| <!--DelRow-->[GetInsightIntentFlag](arkts-ability-insightintentdriver-getinsightintentflag-e-sys.md) | 意图信息（[InsightIntentInfo](arkts-ability-insightintentdriver-insightintentinfo-i-sys.md#InsightIntentInfo)）的标识，用于<br/>[getAllInsightIntentInfo](arkts-ability-insightintentdriver-getinsightintentinfobybundlename-f-sys.md#getInsightIntentInfoByBundleName-1)、<br/>[getInsightIntentInfoByBundleName](arkts-ability-insightintentdriver-getinsightintentinfobybundlename-f-sys.md#getInsightIntentInfoByBundleName-1)和<br/>[getInsightIntentInfoByIntentName](arkts-ability-insightintentdriver-getinsightintentinfobyintentname-f-sys.md#getInsightIntentInfoByIntentName-1)接口查询意图信息。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - 对于使用配置文件开发的意图，通过上述接口查询的全量信息和简要信息完全一致。<br/>&gt;<br/>&gt; - 对于使用装饰器开发的意图，通过上述接口查询的全量信息和简要信息存在差别，详见下表。<br/>&gt;<br/>&gt; 表1 全量意图信息与简要意图信息差别<br/>&gt;<br/>&gt; \| 属性 \| 全量意图信息是否包含 \| 简要意图信息是否包含 \|<br/>&gt; \| -------- \| -------- \| -------- \|<br/>&gt; \| bundleName \| 是 \| 是 \| <br/>&gt; \| moduleName \| 是 \| 是 \|<br/>&gt; \| intentName \| 是 \| 是 \|<br/>&gt; \| domain \| 是 \| 否 \|<br/>&gt; \| intentVersion \| 是 \| 否 \|<br/>&gt; \| displayName \| 是 \| 是 \|<br/>&gt; \| displayDescription \| 是 \| 否 \|<br/>&gt; \| schema \| 是 \| 否 \|<br/>&gt; \| icon \| 是 \| 否 \|<br/>&gt; \| llmDescription \| 是 \| 否 \|<br/>&gt; \| keywords \| 是 \| 否 \|<br/>&gt; \| intentType \| 是 \| 是 \|<br/>&gt; \| subIntentInfo \| 是 \| 是 \|<br/>&gt; \| parameters \| 是 \| 是 \|<br/>&gt; \| entities \| 否 \| 否 \|<br/>&gt; \| developType&lt;sup&gt;23+&lt;/sup&gt; \| 是 \| 是 \|<br/>&gt; \| subIntentInfoForConfiguration&lt;sup&gt;23+&lt;/sup&gt; \| 否 \| 否 \|<br/> |
| <!--DelRow-->[InsightIntentType](arkts-ability-insightintentdriver-insightintenttype-e-sys.md) | 表示通过意图装饰器定义的意图类型，可通过[getAllInsightIntentInfo](arkts-ability-insightintentdriver-getallinsightintentinfo-f-sys.md#getAllInsightIntentInfo-1)等方法返回的<br/>[LinkIntentInfo](arkts-ability-insightintentdriver-linkintentinfo-i-sys.md#LinkIntentInfo)获取。<br/> |


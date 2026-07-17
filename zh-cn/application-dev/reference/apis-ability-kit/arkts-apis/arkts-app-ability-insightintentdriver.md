# @ohos.app.ability.insightIntentDriver

本模块提供执行意图调用的能力，系统根据用户交互等信息执行意图调用。

> **说明：**  
>  
> 本模块从API version 20开始支持通过  
> [@InsightIntentLink](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink)  
> 装饰器定义的意图来实现应用跳转。

**起始版本：** 11

<!--Device-unnamed-declare namespace insightIntentDriver--><!--Device-unnamed-declare namespace insightIntentDriver-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { insightIntentDriver } from '@kit.AbilityKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [execute](arkts-ability-insightintentdriver-execute-f-sys.md#execute-1) | 执行意图调用的接口。使用callback异步回调。当调用方在后台时，需要申请`ohos.permission.START_ABILITIES_FROM_BACKGROUND`权限。当意图调用执行模式[ExecuteMode](arkts-ability-insightintent-executemode-e.md)取值为UI_ABILITY_BACKGROUND时，需要申请`ohos.permission.ABILITY_BACKGROUND_COMMUNICATION`权限。 |
| [execute](arkts-ability-insightintentdriver-execute-f-sys.md#execute-2) | 执行意图调用的接口。使用Promise异步回调。当调用方在后台时，需要申请`ohos.permission.START_ABILITIES_FROM_BACKGROUND`权限。当意图调用执行模式[ExecuteMode](arkts-ability-insightintent-executemode-e.md)取值为UI_ABILITY_BACKGROUND时，需要申请`ohos.permission.ABILITY_BACKGROUND_COMMUNICATION`权限。 |
| [getAllInsightIntentInfo](arkts-ability-insightintentdriver-getallinsightintentinfo-f-sys.md#getallinsightintentinfo-1) | 查询当前设备上的所有意图信息。使用Promise异步回调。 |
| [getInsightIntentInfoByBundleName](arkts-ability-insightintentdriver-getinsightintentinfobybundlename-f-sys.md#getinsightintentinfobybundlename-1) | 根据包名查询当前设备上的意图信息。使用Promise异步回调。 |
| [getInsightIntentInfoByFilter](arkts-ability-insightintentdriver-getinsightintentinfobyfilter-f-sys.md#getinsightintentinfobyfilter-1) | Obtains the intent information on the current device based on the given intent filter. This API uses a promise to return the result.<br>If the user ID of the calling application is different from the user ID of the intent, the |
| [getInsightIntentInfoByIntentName](arkts-ability-insightintentdriver-getinsightintentinfobyintentname-f-sys.md#getinsightintentinfobyintentname-1) | 根据包名、模块名和意图名查询当前设备上的意图信息。使用Promise异步回调。 |
| [queryEntityInfo](arkts-ability-insightintentdriver-queryentityinfo-f-sys.md#queryentityinfo-1) | 查询意图实体信息。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [FunctionIntentInfo](arkts-ability-insightintentdriver-functionintentinfo-i.md) | [@InsightIntentFunctionMethod](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentfunctionmethod)装饰器的参数类型，当前全部属性均继承自[IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md)。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [EntityInfo](arkts-ability-insightintentdriver-entityinfo-i-sys.md) | EntityInfo继承自[IntentEntityDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intententitydecoratorinfo-i.md)，用于描述[@InsightIntentEntity](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententity)装饰器定义的意图实体的信息。 |
| [EntryIntentInfo](arkts-ability-insightintentdriver-entryintentinfo-i-sys.md) | FormIntentInfo用于描述[@InsightIntentForm](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentform)装饰器支持的参数，例如卡片名称。同时，该接口也可用于描述[使用配置文件开发的意图](../../../../application-models/insight-intent-config-development.md)所绑定的卡片信息。 |
| [ExecuteParam](arkts-ability-insightintentdriver-executeparam-i-sys.md) | 执行意图调用的参数。 |
| [FormIntentInfo](arkts-ability-insightintentdriver-formintentinfo-i-sys.md) | FormIntentInfo用于描述[@InsightIntentForm](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentform)装饰器支持的参数，例如卡片名称。同时，该接口也可用于描述[使用配置文件开发的意图](../../../../application-models/insight-intent-config-development.md)所绑定的卡片信息。 |
| [InsightIntentInfo](arkts-ability-insightintentdriver-insightintentinfo-i-sys.md) | 意图信息，表示设备中意图的具体参数配置。 |
| [InsightIntentInfoFilter](arkts-ability-insightintentdriver-insightintentinfofilter-i-sys.md) | 意图筛选器，描述目标意图的筛选条件，用于筛选设备上符合条件的意图。 |
| [LinkIntentInfo](arkts-ability-insightintentdriver-linkintentinfo-i-sys.md) | LinkIntentInfo用于描述[@InsightIntentLink](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink)装饰器支持的参数，例如应用间跳转需要的uri信息。 |
| [PageIntentInfo](arkts-ability-insightintentdriver-pageintentinfo-i-sys.md) | PageIntentInfo用于描述[@InsightIntentPage](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentpage)装饰器支持的参数，例如目标页面的[NavDestination](../../../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navdestination10)名称。 |
| [QueryParam](arkts-ability-insightintentdriver-queryparam-i-sys.md) | 查询洞察意图实体时的Param。 |
| [ServiceExtensionIntentInfo](arkts-ability-insightintentdriver-serviceextensionintentinfo-i-sys.md) | 用于描述[使用配置文件开发的意图](../../../../application-models/insight-intent-config-development.md)所绑定的ServiceExtensionAbility组件信息。 |
| [SubIntentInfoForConfiguration](arkts-ability-insightintentdriver-subintentinfoforconfiguration-i-sys.md) | 用于描述[使用配置文件开发的意图](../../../../application-models/insight-intent-config-development.md)的特有信息。 |
| [UIAbilityIntentInfo](arkts-ability-insightintentdriver-uiabilityintentinfo-i-sys.md) | 用于描述[使用配置文件开发的意图](../../../../application-models/insight-intent-config-development.md)所绑定的UIAbility组件信息。 |
| [UIExtensionIntentInfo](arkts-ability-insightintentdriver-uiextensionintentinfo-i-sys.md) | 用于描述[使用配置文件开发的意图](../../../../application-models/insight-intent-config-development.md)所绑定的UIExtensionAbility组件信息。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DevelopType](arkts-ability-insightintentdriver-developtype-e-sys.md) | 用于描述意图的开发方式。 |
| [ExecuteModeForConfiguration](arkts-ability-insightintentdriver-executemodeforconfiguration-e-sys.md) | [使用配置文件开发的意图](../../../../application-models/insight-intent-config-development.md)支持的意图执行模式。例如，将[insight_intent.json配置文件](../../../../application-models/insight-intent-config-development.md#insight_intentjson配置文件说明)中的executeMode设置为"foreground"，表示支持与UIAbility组件绑定的意图在前台运行。 |
| [GetInsightIntentFlag](arkts-ability-insightintentdriver-getinsightintentflag-e-sys.md) | 意图信息（[InsightIntentInfo](arkts-ability-insightintentdriver-insightintentinfo-i-sys.md)）的标识，用于[getAllInsightIntentInfo](arkts-ability-insightintentdriver-getinsightintentinfobybundlename-f-sys.md#getinsightintentinfobybundlename-1)、[getInsightIntentInfoByBundleName](arkts-ability-insightintentdriver-getinsightintentinfobybundlename-f-sys.md#getinsightintentinfobybundlename-1)和[getInsightIntentInfoByIntentName](arkts-ability-insightintentdriver-getinsightintentinfobyintentname-f-sys.md#getinsightintentinfobyintentname-1)接口查询意图信息。 |
| [InsightIntentType](arkts-ability-insightintentdriver-insightintenttype-e-sys.md) | 表示通过意图装饰器定义的意图类型，可通过[getAllInsightIntentInfo](arkts-ability-insightintentdriver-getallinsightintentinfo-f-sys.md#getallinsightintentinfo-1)等方法返回的[LinkIntentInfo](arkts-ability-insightintentdriver-linkintentinfo-i-sys.md)获取。 |
<!--DelEnd-->


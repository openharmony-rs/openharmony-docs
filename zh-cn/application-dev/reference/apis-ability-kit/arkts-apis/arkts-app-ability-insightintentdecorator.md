# @ohos.app.ability.InsightIntentDecorator

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [EntryIntentDecoratorInfo](arkts-ability-entryintentdecoratorinfo-i.md) | EntryIntentDecoratorInfo继承自[IntentDecoratorInfo](arkts-ability-intentdecoratorinfo-i.md#IntentDecoratorInfo)，用于描述<br/>[@InsightIntentEntry](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententry)<br/>装饰器支持的参数。<br/> |
| [FormIntentDecoratorInfo](arkts-ability-formintentdecoratorinfo-i.md) | FormIntentDecoratorInfo继承自[IntentDecoratorInfo](arkts-ability-intentdecoratorinfo-i.md#IntentDecoratorInfo)，用于描述<br/>[@InsightIntentForm](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentform)<br/>装饰器支持的参数。<br/> |
| [FunctionIntentDecoratorInfo](arkts-ability-functionintentdecoratorinfo-i.md) | [@InsightIntentFunctionMethod](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentfunctionmethod)<br/>装饰器的参数类型，当前全部属性均继承自[IntentDecoratorInfo](arkts-ability-intentdecoratorinfo-i.md#IntentDecoratorInfo)。<br/> |
| [IntentDecoratorInfo](arkts-ability-intentdecoratorinfo-i.md) | 意图装饰器的通用属性，用于定义意图的基本信息（包括意图名称、意图版本号）。适用于本模块的所有装饰器。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 如果根据schema与intentVersion字段，在标准意图列表存在匹配的标准意图，系统会将intentName、domain、llmDescription、keywords、parameters、result字段均设置为标准<br/>&gt; 意图的相应字段值。<br/> |
| [IntentEntityDecoratorInfo](arkts-ability-intententitydecoratorinfo-i.md) | 用于描述<br/>[@InsightIntentEntity](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententity)<br/>装饰器支持的参数。<br/> |
| [LinkIntentDecoratorInfo](arkts-ability-linkintentdecoratorinfo-i.md) | LinkIntentDecoratorInfo继承自[IntentDecoratorInfo](arkts-ability-intentdecoratorinfo-i.md#IntentDecoratorInfo)，用于描述<br/>[@InsightIntentLink](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink)<br/>装饰器支持的参数，例如应用间跳转需要的uri信息。<br/> |
| [LinkIntentParamMapping](arkts-ability-linkintentparammapping-i.md) | LinkIntentParamMapping是<br/>[@InsightIntentLink](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink)<br/>装饰器的意图参数和uri信息的映射。<br/> |
| [PageIntentDecoratorInfo](arkts-ability-pageintentdecoratorinfo-i.md) | PageIntentDecoratorInfo继承自[IntentDecoratorInfo](arkts-ability-intentdecoratorinfo-i.md#IntentDecoratorInfo)，用于描述<br/>[@InsightIntentPage](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentpage)<br/>装饰器支持的参数，例如目标页面的<br/>[NavDestination](../../../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navdestination10)名称。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [LinkParamCategory](arkts-ability-linkparamcategory-e.md) | [@InsightIntentLink](../../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink)<br/>装饰器的意图参数类别，用于定义意图参数的传递形式。<br/> |


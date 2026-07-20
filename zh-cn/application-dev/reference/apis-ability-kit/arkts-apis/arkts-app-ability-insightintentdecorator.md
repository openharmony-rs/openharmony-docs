# @ohos.app.ability.InsightIntentDecorator

## 导入模块

```TypeScript
import { InsightIntentFunction, InsightIntentForm, InsightIntentLink, InsightIntentEntity, LinkParamCategory, InsightIntentPage, InsightIntentEntry, InsightIntentFunctionMethod } from '@kit.AbilityKit';
```

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [EntryIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-entryintentdecoratorinfo-i.md) | EntryIntentDecoratorInfo继承自[IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md)，用于描述[@InsightIntentEntry](docroot://reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententry)装饰器支持的参数。 |
| [FormIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-formintentdecoratorinfo-i.md) | FormIntentDecoratorInfo继承自[IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md)，用于描述[@InsightIntentForm](docroot://reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentform)装饰器支持的参数。 |
| [FunctionIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-functionintentdecoratorinfo-i.md) | [@InsightIntentFunctionMethod](docroot://reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentfunctionmethod)装饰器的参数类型，当前全部属性均继承自[IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md)。 |
| [IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md) | 意图装饰器的通用属性，用于定义意图的基本信息（包括意图名称、意图版本号）。适用于本模块的所有装饰器。 |
| [IntentEntityDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intententitydecoratorinfo-i.md) | 用于描述[@InsightIntentEntity](docroot://reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententity)装饰器支持的参数。 |
| [LinkIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-linkintentdecoratorinfo-i.md) | LinkIntentDecoratorInfo继承自[IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md)，用于描述[@InsightIntentLink](docroot://reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink)装饰器支持的参数，例如应用间跳转需要的uri信息。 |
| [LinkIntentParamMapping](arkts-ability-app-ability-insightintentdecorator-linkintentparammapping-i.md) | LinkIntentParamMapping是[@InsightIntentLink](docroot://reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink)装饰器的意图参数和uri信息的映射。 |
| [PageIntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-pageintentdecoratorinfo-i.md) | PageIntentDecoratorInfo继承自[IntentDecoratorInfo](arkts-ability-app-ability-insightintentdecorator-intentdecoratorinfo-i.md)，用于描述[@InsightIntentPage](docroot://reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentpage)装饰器支持的参数，例如目标页面的[NavDestination](docroot://reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navdestination10)名称。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [LinkParamCategory](arkts-ability-app-ability-insightintentdecorator-linkparamcategory-e.md) | [@InsightIntentLink](docroot://reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintentlink)装饰器的意图参数类别，用于定义意图参数的传递形式。 |


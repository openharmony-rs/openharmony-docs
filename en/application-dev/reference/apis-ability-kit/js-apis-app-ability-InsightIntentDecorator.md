# @ohos.app.ability.InsightIntentDecorator (Intent Decorator)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b3bc27a342923ac4fafa55153b55c4f3b627330f translatedAt=2026-09-03T10:21:21.065Z pushedAt=2026-09-05T11:51:38.607Z -->

The InsightIntentDecorator module provides several types of intent decorators for decorating classes or methods. You can [use decorators to develop intents](../../application-models/insight-intent-decorator-development.md) to define the functions of an application as intents and integrate them into AI entries such as intelligent Q&A, intelligent search, and intelligent recommendation.

- [@InsightIntentLink](#insightintentlink): decorates a URI in the current application as an intent, enabling AI entries to quickly jump to the current application. For details on the parameters supported by this decorator, see [LinkIntentDecoratorInfo](#linkintentdecoratorinfo).
- [@InsightIntentPage](#insightintentpage): decorates a page in your application as an intent, enabling AI systems to swiftly navigate to that page. For details on the parameters supported by this decorator, see [PageIntentDecoratorInfo](#pageintentdecoratorinfo).
- [@InsightIntentFunction](#insightintentfunction) and [@InsightIntentFunctionMethod](#insightintentfunctionmethod): these two decorators must be used together. Use [@InsightIntentFunction](#insightintentfunction) to decorate a class and [@InsightIntentFunctionMethod](#insightintentfunctionmethod) to decorate a static function in the class, so that the static function is defined as an intent, enabling AI entries to quickly execute the function.
- [@InsightIntentEntry](#insightintententry): decorates a class that inherits from [InsightIntentEntryExecutor](./js-apis-app-ability-InsightIntentEntryExecutor.md) to implement intent operations and configure the ability on which the intent depends. This helps the AI entry point to easily invoke the associated ability and perform the intended action. For details on the parameters supported by this decorator, see [EntryIntentDecoratorInfo](#entryintentdecoratorinfo).
- [@InsightIntentForm](#insightintentform): decorates a [FormExtensionAbility](../apis-form-kit/js-apis-app-form-formExtensionAbility.md) to specify the name of the widget bound to the FormExtensionAbility. This enables the AI entry point to add the widget via intent calls. For details on the parameters supported by this decorator, see [FormIntentDecoratorInfo](#formintentdecoratorinfo).
- [@InsightIntentEntity](#insightintententity): decorates a class that inherits from [IntentEntity](./js-apis-app-ability-insightIntent.md#intententity20) to define the class as an intent entity, which can pass parameters required for intent calls. For details on the parameters supported by this decorator, see [IntentEntityDecoratorInfo](#intententitydecoratorinfo).

> **NOTE**
>
> The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Basic Concepts

Intents are divided into two types: standard intents and custom intents.

The system queries the standard intent list for a matching intent based on the **schema** and **intentVersion** fields in [IntentDecoratorInfo](#intentdecoratorinfo).

- If a match is found, the intent is identified as a standard intent.
- If no match is found, the intent is identified as a custom intent.

## Modules to Import

```ts
import { InsightIntentLink, InsightIntentPage, InsightIntentFunctionMethod, InsightIntentFunction, InsightIntentEntry } from '@kit.AbilityKit';
```

## @InsightIntentLink

Decorates a URI link in the current application as an intent, enabling AI entries to quickly jump to the current application via the defined intent. For details on the parameters supported by this decorator, see [LinkIntentDecoratorInfo](#linkintentdecoratorinfo).

> **NOTE**
>
> The URI format must comply with the requirements described in [Application Link Description](../../application-models/app-uri-config.md).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 20.

**Example**

Custom intent: The parameters of a custom intent must be passed in as a standard JSON schema data structure.

```ts
import { InsightIntentLink, LinkParamCategory } from '@kit.AbilityKit';

@InsightIntentLink({
  intentName: 'PlayMusic',
  domain: 'MusicDomain',
  intentVersion: '1.0.1',
  displayName: 'Play Music',
  displayDescription: 'Intent to play music',
  icon: $r('app.media.app_icon'), // $r indicates a local icon, which must be defined in the resource catalog.
  llmDescription: 'Supports passing song names to play music',
  keywords: ['music playback', 'play music', 'PlayMusic'],
  uri: 'https://www.example.com/music/',
  paramMappings: [{
    paramName: 'songName',
    paramMappingName: 'music',
    paramCategory: LinkParamCategory.LINK
  }],
  parameters: {
    '$schema': 'http://json-schema.org/draft-07/schema#',
    'type': 'object',
    'title': 'Song Schema',
    'description': 'A schema for describing songs and their artists',
    'properties': {
      'songName': {
        'type': 'string',
        'description': 'The name of the song',
        'minLength': 1
      }
    },
    'required': ['songName'],
    'additionalProperties': false
  },
  result: {
    'type': 'object',
    'propertyNames': {
      'enum': [
        'code',
        'result'
      ]
    },
    'required': [
      'code',
      'result'
    ],
    'properties': {
      'code': {
        'description': 'Result code for job execution',
        'type': 'number'
      },
      'result': {}
    }
  }
})
export class ClassForLink {
  private _playback: string = 'intention_test';

  public set playback(value: string) {
    this._playback = value;
  }

  public get playback(): string {
    return this._playback;
  }

  constructor(playback: string) {
    this._playback = playback;
  }

  static updatePlaybackStatus(playbackProgress: number, playback?: number): void {
    console.info(`Function1, playbackProgress: ${playbackProgress}.`);
  }
}
```

## IntentDecoratorInfo

Common properties for intent decorators, used to define basic information about an intent (including the intent name and version number). It applies to all decorators provided by this module.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 20.

**Properties**

> **NOTE**
>
> If a matching intent is found in the standard intent list based on the **schema** and **intentVersion** fields, the system automatically populates the **intentName**, **domain**, **llmDescription**, **keywords**, **parameters**, and **result** fields with the values from the matching standard intent.

| Name              | Type           | Read-Only        | Optional| Description                                                        |
| ------------------ | ----------------| ---------- | ---- | ------------------------------------------------------------ |
| intentName         | string          | No      | No  | Intent name, which is the unique identifier of an intent.|
| domain             | string          | No      | No  | Vertical domain of the intent. It is used to categorize intents by vertical fields (for example, video, music, and games). For details about the value range, see the vertical domain fields in [smart distribution features in different vertical domains](https://developer.huawei.com/consumer/en/doc/service/intents-ai-distribution-characteristic-0000001901922213#section2656133582215).   |
| intentVersion      | string          | No      | No  | Version number of the intent. It is used to distinguish and manage intents when their capabilities evolve.                       |
| displayName        | string          | No      | No  | Name of the intent displayed to users.                                      |
| displayDescription | string         | No       | Yes  | Description of the intent displayed to users.                                      |
| schema             | string         | No       | Yes  | Name of a standard intent schema. This field is required when you [access a standard intent](../../application-models/insight-intent-definition.md#accessing-standard-intents). It is not required when you [create a custom intent](../../application-models/insight-intent-definition.md#creating-custom-intents). For details about the standard intent list, see [Appendix: Standard Intent Access Specifications](../../application-models/insight-intent-access-specifications.md).|
| icon               | ResourceStr | No   | Yes   | Indicates the intent icon, which is displayed at the AI entry.<br>- When the value is of the string type, the icon is read from a network resource.<br>- When the value is of the [Resource](../../reference/apis-localization-kit/js-apis-resource-manager.md) type, the icon is read from a local resource. |
| llmDescription     | string      | No           | Yes   | Indicates the functional description of the intent, which is used by a large language model to understand the intent.                  |
| keywords           | string[]     | No         | Yes  | Search keywords for the intent.                                      |
| parameters         | Record\<string, Object\>| No | Yes   | Indicates the data format declaration of the intent parameters, which is used to define the data format of the input parameters during intent invocation. For details about the values, see Intent Schema for Each Vertical Domain. |
| result           | Record\<string, Object\>     | No          | Yes   | Indicates the data format declaration of the result returned by intent invocation, which is used to define the data format of the result returned by intent invocation.                                       |

## LinkIntentDecoratorInfo

LinkIntentDecoratorInfo inherits from [IntentDecoratorInfo](#intentdecoratorinfo) and is used to describe the parameters supported by the [@InsightIntentLink](#insightintentlink) decorator, such as the URI information required for inter-application jumps.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 20.

**Properties**

| Name       | Type             | Read-Only| Optional| Description                                                        |
| ----------- | -----------------| ------ | ---- | ------------------------------------------------------------ |
| uri                | string          | No          | No   | URI address of the intent.                                 |
| paramMappings      | [LinkIntentParamMapping](#linkintentparammapping)[] | No | Yes   | Mapping between intent parameters and URI information.    |

## LinkIntentParamMapping

LinkIntentParamMapping is the mapping between the intent parameters of the [@InsightIntentLink](#insightintentlink) decorator and the URI information.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 20.

**Properties**

| Name            | Type  | Read-Only| Optional| Description                                  |
| ---------------- | ------ | ----| ---- | -------------------------------------- |
| paramName        | string | No| No  | Name of the intent parameter.                      |
| paramMappingName | string | No| Yes  | Mapping name of the intent parameter.                    |
| paramCategory    | [LinkParamCategory](#linkparamcategory) | No | Yes   | Intent parameter category. If the value is [LINK](#linkparamcategory), the system obtains the mapping name corresponding to paramName and appends it to the end of the URI in key-value pair form. If the value is [WANT](#linkparamcategory), the system obtains the mapping name corresponding to paramName and its value, and passes them through the parameters field of [Want](./js-apis-app-ability-want.md).  |

## LinkParamCategory

Enumerates the intent parameter categories available for the [@InsightIntentLink](#insightintentlink) decorator. The enum is used to define how intent parameters should be passed.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 20.

| Name| Value| Description|
| -------- | -------- | -------- |
| LINK  | 'link' | Indicates that the intent parameter category is 'link'. The system obtains the intent parameter mapping name corresponding to the paramName field and appends the intent parameter mapping name to the end of the URI link. |
| WANT  | 'want' | Indicates that the intent parameter category is 'want'. The system obtains the intent parameter mapping name corresponding to the paramName field and passes the intent parameter mapping name and its value through the parameters field of [Want](./js-apis-app-ability-want.md). |

## @InsightIntentPage

Decorates a page in the application as an intent, enabling AI systems to swiftly navigate to that page. For details on the parameters supported by this decorator, see [PageIntentDecoratorInfo](#pageintentdecoratorinfo).

> **NOTE**
>
> This decorator is only applicable to struct pages.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 20.

**Example**

```ts
import { InsightIntentPage } from '@kit.AbilityKit';

@Entry
@Component
@InsightIntentPage({
  intentName: 'SearchMusic',
  domain: 'MusicDomain',
  intentVersion: '1.0.1',
  displayName: 'Search Music',
  displayDescription: 'Intent to search music',
  schema: 'SearchMusic',
  uiAbility: 'Entry',
  pagePath: './ets/pages/Index',
  navigationId: '1',
  navDestinationName: 'PageOne',
})
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## PageIntentDecoratorInfo

PageIntentDecoratorInfo inherits from [IntentDecoratorInfo](#intentdecoratorinfo) and is used to describe the parameters supported by the [@InsightIntentPage](#insightintentpage) decorator, such as the [navDestination](../apis-arkui/arkui-ts/ts-basic-components-navigation.md#navdestination10) name of the target page.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 20.

**Properties**

| Name              | Type        | Read-Only      | Optional| Description                                                        |
| ------------------ | -------------| --------- | ---- | ------------------------------------------------------------ |
| uiAbility          | string       | No          | Yes  | Name of the UIAbility bound to the intent.                                 |
| pagePath           | string        | No         | No  | Path of the page bound to the intent. The page must be a file that actually exists.|
| navigationId       | string        | No        | Yes   | ID attribute of the [Navigation](../apis-arkui/arkui-ts/ts-basic-components-navigation.md) component bound to the intent. |
| navDestinationName | string         | No       | Yes   | Name of the [navDestination](../apis-arkui/arkui-ts/ts-basic-components-navigation.md#navdestination10) component bound to the intent. |

## @InsightIntentFunction

This decorator must be used together with the [@InsightIntentFunctionMethod](#insightintentfunctionmethod) decorator.

This decorator is used to decorate a class, and [@InsightIntentFunctionMethod](#insightintentfunctionmethod) is used to decorate a static function in that class. This setup defines the static function as an intent, enabling AI systems to execute it rapidly.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 20.

## @InsightIntentFunctionMethod

This decorator must be used together with the [@InsightIntentFunction](#insightintentfunction) decorator.

[@InsightIntentFunction](#insightintentfunction) is used to decorate a class, and this decorator is used to decorate a static function in that class. This setup defines the static function as an intent, enabling AI systems to execute it rapidly.

> **NOTE**
>
> The class containing static methods must be exported using **export**.
>
> Parameter names and types of a function must align with those specified in the intent definition.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 20.

**Example**

```ts
import { InsightIntentFunction, InsightIntentFunctionMethod } from '@kit.AbilityKit';

@InsightIntentFunction()
export class ClassForFuncDemo {
  @InsightIntentFunctionMethod({
  intentName: 'GetWeather',
  domain: 'LifeDomain',
  intentVersion: '1.0.1',
  displayName: 'Query weather',
  displayDescription: 'Display weather information',
  icon: $r('app.media.app_icon'), // $r indicates a local icon, which must be defined in the resource catalog.
  llmDescription: 'Get weather of a location',
  parameters: {
    '$schema': 'http://json-schema.org/draft-07/schema#',
    'type': 'object',
    'title': 'Weather Schema',
    'description': 'A schema for getting weather of a location',
    'properties': {
      'location': {
        'type': 'string',
        'description': 'The city and state, e.g. Hangzhou',
        'minLength': 1
      }
    },
    'required': ['location'],
    'additionalProperties': false
  }
})
  static getWeather(location: string): string {
    console.info(`location: ${location}`);
    return 'The current temperature in Hangzhou is 24℃';
  }
}
```

## FunctionIntentDecoratorInfo

Parameter type of the [@InsightIntentFunctionMethod](#insightintentfunctionmethod) decorator. All properties inherit from [IntentDecoratorInfo](#intentdecoratorinfo).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 20.

## @InsightIntentEntry

Decorates a class that inherits from [InsightIntentEntryExecutor](./js-apis-app-ability-InsightIntentEntryExecutor.md) to implement intent operations and configure the ability on which the intent depends. This helps the AI entry point to easily invoke the associated ability and perform the intended action. For details on the parameters supported by this decorator, see [EntryIntentDecoratorInfo](#entryintentdecoratorinfo).

> **NOTE**
>
> - If this decorator is used to integrate a standard intent, all mandatory parameters defined in the standard intent JSON Schema must be implemented and their types must match.
> - If a custom intent is created, all mandatory parameters defined in the parameters field must be implemented and their types must match.
> - The decorated class must be exported using export default. The attributes of the class support only basic types or intent entities, and the return value supports only intent entities.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 20.

**Example**

```ts
import { insightIntent, InsightIntentEntry, InsightIntentEntryExecutor } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const LOG_TAG: string = 'testTag-EntryIntent';

// Use the @InsightIntentEntry decorator to define an intent.
@InsightIntentEntry({
  intentName: 'PlayMusic',
  domain: 'MusicDomain',
  intentVersion: '1.0.1',
  displayName: 'Play Music',
  displayDescription: 'Intent to play music',
  icon: $r('app.media.app_icon'), // $r indicates a local icon, which must be defined in the resource catalog.
  llmDescription: 'Supports passing song names to play music',
  keywords: ['music playback', 'play music', 'PlayMusic'],
  abilityName: 'EntryAbility',
  executeMode: [insightIntent.ExecuteMode.UI_ABILITY_FOREGROUND],
  parameters: {
    '$schema': 'http://json-schema.org/draft-07/schema#',
    'type': 'object',
    'title': 'Song Schema',
    'description': 'A schema for describing songs and their artists',
    'properties': {
      'songName': {
        'type': 'string',
        'description': 'The name of the song',
        'minLength': 1
      }
    },
    'required': ['songName']
  }
})
export default class PlayMusicDemo extends InsightIntentEntryExecutor<string> {
  songName: string = '';

  onExecute(): Promise<insightIntent.IntentResult<string>> {
    hilog.info(0x0000, LOG_TAG, 'PlayMusicDemo executeMode %{public}s', JSON.stringify(this.executeMode));
    hilog.info(0x0000, LOG_TAG, '%{public}s', JSON.stringify(this));
    // Create a LocalStorage instance to pass parameters between pages.
    let storage = new LocalStorage();
    // Save the song name to LocalStorage for the target page to read.
    storage.setOrCreate('songName', this.songName);
    // Start the PlayMusicPage page based on the executeMode parameter.
    if (this.executeMode == insightIntent.ExecuteMode.UI_ABILITY_FOREGROUND) {
      this.windowStage?.loadContent('pages/PlayMusicPage', storage);
    } else if (this.executeMode == insightIntent.ExecuteMode.UI_EXTENSION_ABILITY) {
      this.uiExtensionSession?.loadContent('pages/PlayMusicPage', storage);
    }
    // Define the intent execution result.
    let result: insightIntent.IntentResult<string> = {
      code: 123,
      result: 'result'
    }
    hilog.error(0x0000, LOG_TAG, `Failed to execute PlayMusicDemo. Code: ${result.code}, message: ${result.result}`);
    // Return the intent execution failure result by using Promise.reject.
    return Promise.reject(result);
  }
}
```

## EntryIntentDecoratorInfo

Inherits from [IntentDecoratorInfo](#intentdecoratorinfo) and is used to describe the parameters supported by the [@InsightIntentEntry](#insightintententry) decorator.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 20.

**Properties**

| Name              | Type        | Read-Only      | Optional| Description                                                        |
| ------------------ | -------------| --------- | ---- | ------------------------------------------------------------ |
| abilityName        | string       | No       | No  | Name of the ability bound to the intent.                                 |
| executeMode        | [insightIntent.ExecuteMode](./js-apis-app-ability-insightIntent.md#executemode)[]| No       | No  | Execution mode of the intent call, that is, execution mode supported when the bound ability is started.|

## @InsightIntentForm

Decorates a [FormExtensionAbility](../apis-form-kit/js-apis-app-form-formExtensionAbility.md) to specify the name of the widget bound to the FormExtensionAbility. This enables the AI entry point to add the widget via intent calls. For details on the parameters supported by this decorator, see [FormIntentDecoratorInfo](#formintentdecoratorinfo).

> **NOTE**
>
> For details about the requirements for defining widget names, see [Widget Configuration](../../form/arkts-ui-widget-configuration.md#widget-configuration).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 20.

**Example**

```ts
import { formBindingData, FormExtensionAbility } from '@kit.FormKit';
import { Want, InsightIntentForm } from '@kit.AbilityKit';

// Use the @InsightIntentForm decorator to define a widget of the FormExtensionAbility as an intent.
@InsightIntentForm({
  intentName: 'PlayMusic',
  domain: 'MusicDomain',
  intentVersion: '1.0.1',
  displayName: 'Play Music',
  displayDescription: 'Intent to play music',
  icon: $r('app.media.app_icon'), // $r indicates a local icon, which must be defined in the resource catalog.
  llmDescription: 'Supports passing song names to play music',
  keywords: ['music playback', 'play music', 'PlayMusic'],
  parameters: {
    '$schema': 'http://json-schema.org/draft-07/schema#',
    'type': 'object',
    'title': 'Song Schema',
    'description': 'A schema for describing songs and their artists',
    'properties': {
      'songName': {
        'type': 'string',
        'description': 'The name of the song',
        'minLength': 1
      },
      'artist': {
        'type': 'object',
        'description': 'Information about the artist',
        'properties': {
          'country': {
            'type': 'string',
            'description': 'The artist\'s country of origin',
            'default': 'zh'
          },
          'city': {
            'type': 'object',
            'description': 'The artist\'s city of origin'
          },
          'name': {
            'type': 'string',
            'description': 'The name of the artist',
            'minLength': 1
          }
        },
        'required': ['name']
      }
    },
    'required': ['songName']
  },
  formName: 'widget'
})
export default class EntryFormAbility extends FormExtensionAbility {
  songName: string = '';

  onAddForm(want: Want) {
    // This API is called to return the FormBindingData object.
    let formData = '';
    return formBindingData.createFormBindingData(formData);
  }
}
```

## FormIntentDecoratorInfo

Inherits from [IntentDecoratorInfo](#intentdecoratorinfo) and is used to describe the parameters supported by the [@InsightIntentForm](#insightintentform) decorator.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 20.

**Properties**

| Name              | Type        | Read-Only      | Optional| Description                                                        |
| ------------------ | -------------| --------- | ---- | ------------------------------------------------------------ |
| formName        | string       | No       | No  | Name of the widget bound to the FormExtensionAbility.                                 |

## @InsightIntentEntity

Decorates a class that inherits from [IntentEntity](./js-apis-app-ability-insightIntent.md#intententity20) to define the class as an intent entity, which can pass parameters required for intent calls. For details on the parameters supported by this decorator, see [IntentEntityDecoratorInfo](#intententitydecoratorinfo).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 20.

**Example**

```ts
import { insightIntent, InsightIntentEntity } from '@kit.AbilityKit';

@InsightIntentEntity({
  entityCategory: 'artist entity category',
  parameters: {
    '$id': '/schemas/ArtistClassDef',
    'type': 'object',
    'description': 'Information about the artist',
    'properties': {
      'country': {
        'type': 'string',
        'description': 'The artist\'s country of origin',
        'default': 'zh'
      },
      'city': {
        'type': 'string',
        'description': 'The artist\'s city of origin'
      },
      'name': {
        'type': 'string',
        'description': 'The name of the artist',
        'minLength': 1
      }
    },
    'required': ['name']
  }
})
export class ArtistClassDef implements insightIntent.IntentEntity {
  entityId: string = 'id';
  name: string = '';
}
```

## IntentEntityDecoratorInfo

Describes the parameters supported by the [@InsightIntentEntity](#insightintententity) decorator.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 20.

**Properties**

| Name              | Type        | Read-Only      | Optional| Description                                                        |
| ------------------ | -------------| --------- | ---- | ------------------------------------------------------------ |
| entityCategory        | string       | No        | No   | Category of the intent entity, used to classify intent entities.                   |
| parameters        | Record<string, Object> | No       | Yes  | Data format of the intent entity.  |
| supportedQueryProperties        | string[] | No        | Yes   | List of attributes supported for querying the intent entity. The attribute names in the list must be defined in parameters.<br>**Since:** 26.0.0<br>**Atomic service API**: Since API version 26.0.0, this API is supported in atomic services. |

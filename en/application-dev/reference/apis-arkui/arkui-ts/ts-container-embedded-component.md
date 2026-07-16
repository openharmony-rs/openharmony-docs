# EmbeddedComponent

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=fd10fbb9e5b5e2e1e561a46b9ca4925a29d1a0a3 translatedAt=2026-06-30T12:25:56.216Z pushedAt=2026-07-02T09:00:23.895Z -->

The **EmbeddedComponent** is a component used to embed into the current page the UI provided by another [EmbeddedUIExtensionAbility](../../apis-ability-kit/js-apis-app-ability-embeddedUIExtensionAbility.md) in the same application. The EmbeddedUIExtensionAbility runs in an independent process for UI layout and rendering.

It is usually used in modular development scenarios where process isolation is required.

> **NOTE**
>
>- This component is supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.
>
>- The APIs of this module can be used only in the stage model.
>
>- Before API version 26.0.0, when the **EmbeddedComponent** gained focus, the focus within the launched **EmbeddedUIExtensionAbility** process was directly dispatched to the first focusable child node. Since API version 26.0.0,
> if focus moves to the **EmbeddedUIExtensionAbility** from outside, the focus is normally dispatched to the first focusable child node.
> If focus is transferred to **EmbeddedUIExtensionAbility** due to a hierarchical page transition, it follows the same rules as **UIAbility**. When a hierarchical page is launched and the page has neither set [defaultFocus](ts-universal-attributes-focus.md#defaultfocus9) nor [actively requested focus](../../../ui/arkts-common-events-focus-event.md#active-focus-acquisitionloss), the focus stays on the root container and is not dispatched to child nodes.

## Constraints

The **EmbeddedComponent** is supported only on devices configured with multi-process permissions.

**EmbeddedComponent** can only be used in a **UIAbility**, and the launched **EmbeddedUIExtensionAbility** must belong to the same application as the **UIAbility**. Since API version 26.0.0, if the application to which the **EmbeddedComponent** belongs has applied for the **ohos.permission.SUPPORT_CROSS_APP_EMBED_FOR_OA** permission (available only to normal enterprise applications), and the application's [appIdentifier](../../../quick-start/common-problem-of-application.md#what-is-appidentifier) is in the allowed application list of the **EmbeddedUIExtensionAbility** (specified by the **appIdentifierAllowList** attribute of the [extensionAbilities tag](../../../quick-start/module-configuration-file.md#extensionabilities)), cross-application launching of the EmbeddedUIExtensionAbility by the **EmbeddedComponent** is allowed.

## Child Components

Not supported

## APIs

EmbeddedComponent(loader: import('../api/@ohos.app.ability.Want').default, type: EmbeddedType, options?: EmbeddedOptions)

Creates a cross-process embedded component to display the UI of the EmbeddedUIExtensionAbility with the same bundle name.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name               | Type                         | Mandatory|Description  |
| --------------------- | ---------------------------------------------------------- | ---- | ------------------------------------ |
| loader                | import('../api/@ohos.app.ability.[Want](../../apis-ability-kit/js-apis-app-ability-want.md)').default | Yes   | **EmbeddedUIExtensionAbility** to be loaded. |
| type                  | [EmbeddedType](ts-appendix-enums.md#embeddedtype12)                              | Yes  | Type of the provider.                      |
| options| [EmbeddedOptions](#embeddedoptions) | No   | Construction parameters to be passed.<br>**Since:** 26.0.0                     |

## Attributes

The [universal attributes](ts-component-general-attributes.md) are supported.

> **NOTE**
>
> The default and minimum width and height of the **EmbeddedComponent** are both 10 vp. The following width- and height-related attributes are not supported: **constraintSize**, **aspectRatio**, **layoutWeight**, **flexBasis**, **flexGrow**, and **flexShrink**.

## Events

Event information related to screen coordinates is converted based on the position, width, and height of the **EmbeddedComponent**, before being transferred to the EmbeddedUIExtensionAbility for processing.

Universal events, such as the [click event](ts-universal-events-click.md), are not supported. Only the following events are supported.

### onTerminated

onTerminated(callback: import('../api/@ohos.base').Callback&lt;TerminationInfo&gt;)

Triggered when the launched EmbeddedUIExtensionAbility exits normally by calling [terminateSelfWithResult](../../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession.md#terminateselfwithresult) or [terminateSelf](../../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession.md#terminateself).

> **NOTE**
>
> This API cannot be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description    |
| -------  | ------ | ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| callback | import('../api/@ohos.base').[Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<[TerminationInfo](#terminationinfo)> | Mandatory | Callback used to receive the return result of **EmbeddedUIExtensionAbility**. The input parameter type is [TerminationInfo](#terminationinfo). |

> **NOTE**
>
> - If the EmbeddedUIExtensionAbility is terminated by calling **terminateSelfWithResult**, the carried information is passed as arguments into the callback function.
> - If the EmbeddedUIExtensionAbility is terminated by calling **terminateSelf**, the input parameters **code** and **want** in the callback function are at their default values: **0** and **undefined**, respectively.

### onError

onError(callback: import('../api/@ohos.base').ErrorCallback)

Called when an error occurs during the running of the started EmbeddedUIExtensionAbility. Through the **code**, **name**, and **message** in the callback parameters, error information can be obtained and handled. For details about the error codes, see [UIExtension Error Codes](../errorcode-uiextension.md).

> **NOTE**
>
> This API cannot be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                                        | Mandatory                                                                      | Description     |
| ------ | ---------------------------------------------------------------------------- | --------- | --------- |
| callback    | import('../api/@ohos.base').[ErrorCallback](../../apis-basic-services-kit/js-apis-base.md#errorcallback) | Mandatory | Callback used to receive error information. The input parameter type is [BusinessError](../../apis-basic-services-kit/js-apis-base.md#businesserror). You can obtain error information through **code**, **name**, and **message** in the parameter and handle it accordingly. |

> **NOTE**
>
> This callback is called to notify the provider of the following:
> - The EmbeddedUIExtensionAbility fails to be started.
> - The EmbeddedUIExtensionAbility fails to be switched to the background.
> - The EmbeddedUIExtensionAbility fails to be destroyed.
> - The EmbeddedUIExtensionAbility exits abnormally.
> - An **EmbeddedComponent** is nested in the EmbeddedUIExtensionAbility.

### onDrawReady

onDrawReady(callback: Callback\<void>)

Triggered when the launched [EmbeddedUIExtensionAbility](../../apis-ability-kit/js-apis-app-ability-embeddedUIExtensionAbility.md#embeddeduiextensionability) draws its first frame.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                               | Mandatory | Description                                    |
| ------ | ---------------------------------- | ---- | --------------------------------------- |
| callback   | [Callback](../../apis-basic-services-kit/js-apis-base.md#callback)\<void> | Yes   | Callback triggered when the **EmbeddedUIExtensionAbility** draws its first frame. |

## EmbeddedOptions

Defines optional construction parameters passed in during the construction of **EmbeddedComponent**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Name                               | Type                                                         | Read-Only | Optional | Description                                                         |
| ---------------------------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| placeholder                        | [ComponentContent](../js-apis-arkui-ComponentContent.md)     | No   | Yes   | Placeholder displayed before the connection between the **EmbeddedComponent** and the **EmbeddedUIExtensionAbility** is established. |
| areaChangePlaceholder              | Record\<string, [ComponentContent](../js-apis-arkui-ComponentContent.md)> | No   | Yes   | Area change placeholder displayed when the size of the **EmbeddedComponent** changes and internal rendering is not yet complete. |
| dpiFollowStrategy                  | [EmbeddedDpiFollowStrategy](#embeddeddpifollowstrategy)    | No   | Yes   | DPI follow strategy, indicating whether to follow the host or the **EmbeddedUIExtensionAbility**.<br/> Default value: **FOLLOW_UI_EXTENSION_ABILITY_DPI**, indicating to follow the **EmbeddedUIExtensionAbility**. |
| windowModeFollowStrategy | [EmbeddedWindowModeFollowStrategy](#embeddedwindowmodefollowstrategy) | No   | Yes   | Window mode follow strategy, indicating whether to follow the host or the **EmbeddedUIExtensionAbility**.<br/> Default value: **FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE**<br/>**Since:** 26.0.0 |

## EmbeddedDpiFollowStrategy

Defines the DPI follow strategy, which is used to set the DPI to follow the host or the **EmbeddedUIExtensionAbility**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Name                            | Value | Description                               |
| ------------------------------- | -- | ---------------------------------- |
| FOLLOW_HOST_DPI                 | 0  | The DPI follows the host.                  |
| FOLLOW_UI_EXTENSION_ABILITY_DPI | 1  | The DPI follows the **EmbeddedUIExtensionAbility**. |

## EmbeddedWindowModeFollowStrategy

Defines the window mode follow strategy, which is used to set the window mode to follow the host or the **EmbeddedUIExtensionAbility**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Name                                    | Value | Description                                        |
| --------------------------------------- | -- | ------------------------------------------- |
| FOLLOW_HOST_WINDOW_MODE                 | 0  | The window mode follows the host.                      |
| FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE | 1  | The window mode follows the **EmbeddedUIExtensionAbility**. |

## TerminationInfo

Provides the result returned by the started **EmbeddedUIExtensionAbility**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type                     | Read-Only| Optional| Description                                                |
| ---- | -------------------------| ---- | ---- | ---------------------------------------------------- |
| code | number                                                     | No| No| Result code returned when the **EmbeddedUIExtensionAbility** exits. The result code is determined by the data passed when **terminateSelfWithResult** or **terminateSelf** is called.|
| want | import('../api/@ohos.app.ability.[Want](../../apis-ability-kit/js-apis-app-ability-want.md)').default | No | Yes | Data returned when the launched **EmbeddedUIExtensionAbility** exits. |

## Example: Loading an EmbeddedComponent Component

This example shows the basic usage of the **EmbeddedComponent** component and **EmbeddedUIExtensionAbility**. The bundle name of the sample application is **com.example.embeddedComponent**, and the launched **EmbeddedUIExtensionAbility** within the same application is **ExampleEmbeddedAbility**. This example is supported only on devices configured with multi-process permissions, such as PCs and 2-in-1 devices.

Since API version 26.0.0, the [onDrawReady](#ondrawready) API is added.

- The EntryAbility (UIAbility) of the sample application loads the **ets/pages/Index.ets** file, whose content is as follows:

  ```ts
  import { Want } from '@kit.AbilityKit';
  import { ComponentContent } from '@kit.ArkUI';

  class Params {
  }
  @Builder
  function LoadingBuilder(params: Params) {
    Column() {
      LoadingProgress()
        .color(Color.Blue)
    }
  }
  @Builder
  function AreaChangePlaceholderBuilder(params: Params) {
    Column() {
    }
    .width('100%')
    .height('100%')
    .backgroundColor(Color.Orange)
  }
  @Entry
  @Component
  struct Index {
    @State message: string = 'Message: ';
    private want: Want = {
      bundleName: "com.example.embeddedComponent",
      abilityName: "ExampleEmbeddedAbility",
    };
    @State dpiFollowStrategy: EmbeddedDpiFollowStrategy = EmbeddedDpiFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_DPI;
    @State windowStrategy: EmbeddedWindowModeFollowStrategy =
    EmbeddedWindowModeFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE;
    private initPlaceholder = new ComponentContent(this.getUIContext(), wrapBuilder(LoadingBuilder), new Params);
    private areaChangePlaceholder = new ComponentContent(this.getUIContext(), wrapBuilder(AreaChangePlaceholderBuilder), new Params);

    build() {
      Row() {
        Column() {
          Text(this.message)
            .fontSize(20)
            .fontWeight(FontWeight.Bold)
          EmbeddedComponent(this.want, EmbeddedType.EMBEDDED_UI_EXTENSION,
            {
              placeholder: this.initPlaceholder,
              areaChangePlaceholder: {
                "FOLD_TO_EXPAND" : this.areaChangePlaceholder,
              },
              windowModeFollowStrategy: this.windowStrategy,
              dpiFollowStrategy: this.dpiFollowStrategy
            })
            .width('100%')
            .height('90%')
            .onTerminated((info) => {
              // Triggered when the terminateSelfWithResult button is clicked in the extension page.
              this.message = 'Termination: code = ' + info.code + ', want = ' + JSON.stringify(info.want);
            })
            .onError((error) => {
              // Triggered on failure or exception.
              this.message = 'Error: code = ' + error.code;
            })
            .onDrawReady(() => {
              // Since API version 26.0.0, support is added for triggering the onDrawReady callback when the launched EmbeddedUIExtensionAbility draws the first frame, and the text box displays the following information:
              this.message = `onDrawReady`;
            })
        }
        .width('100%')
      }
      .height('100%')
    }
  }
  ```

- The EmbeddedUIExtensionAbility (**ExampleEmbeddedAbility**) to start by the **EmbeddedComponent** is implemented in the **ets/extensionAbility/ExampleEmbeddedAbility.ets** file. The file content is as follows:

  ```ts
  import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';

  const TAG: string = '[ExampleEmbeddedAbility]';

  export default class ExampleEmbeddedAbility extends EmbeddedUIExtensionAbility {
    onCreate() {
      console.info(TAG, `onCreate`);
    }

    onForeground() {
      console.info(TAG, `onForeground`);
    }

    onBackground() {
      console.info(TAG, `onBackground`);
    }

    onDestroy() {
      console.info(TAG, `onDestroy`);
    }

    onSessionCreate(want: Want, session: UIExtensionContentSession) {
      console.info(TAG, `onSessionCreate, want: ${JSON.stringify(want)}`);
      let param: Record<string, UIExtensionContentSession> = {
        'session': session
      };
      let storage: LocalStorage = new LocalStorage(param);
      // Load the pages/extension.ets content.
      session.loadContent('pages/extension', storage);
    }

    onSessionDestroy(session: UIExtensionContentSession) {
      console.info(TAG, `onSessionDestroy`);
    }
  }
  ```

- The entry page file **ets/pages/extension.ets** for **ExampleEmbeddedAbility** (EmbeddedUIExtensionAbility) is as follows. The path to this page must also be configured in the **resources/base/profile/main_pages.json** file.

  ```ts
  import { UIExtensionContentSession } from '@kit.AbilityKit';

  @Entry
  @Component
  struct Extension {
    @State message: string = 'EmbeddedUIExtensionAbility Index';
    private storage: LocalStorage | undefined = this.getUIContext()?.getSharedLocalStorage();
    private session: UIExtensionContentSession | undefined = this.storage?.get<UIExtensionContentSession>('session');

    build() {
      Column() {
        Text(this.message)
          .fontSize(20)
          .fontWeight(FontWeight.Bold)
        Button("terminateSelfWithResult").fontSize(20).onClick(() => {
          // Call terminateSelfWithResult to exit when the button is clicked.
          this.session?.terminateSelfWithResult({
            resultCode: 1,
            want: {
              bundleName: "com.example.embeddedComponent",
              abilityName: "ExampleEmbeddedAbility",
            }
          });
        })
      }.width('100%').height('100%')
    }
  }
  ```

- Add the configuration for **ExampleEmbeddedAbility** under the **extensionAbilities** tag in the **module.json5** file. The type is set to **embeddedUI**, as shown below:

  ```json
  {
    "name": "ExampleEmbeddedAbility",
    "srcEntry": "./ets/extensionAbility/ExampleEmbeddedAbility.ets",
    "type": "embeddedUI"
  }
  ```

- The file directory structure is as follows:

  ```shell
  .
  └── main
      ├── ets
      │   ├── extensionAbility
      │   │   └── ExampleEmbeddedAbility.ets
      │   └── pages
      |       ├── extension.ets
      │       └── Index.ets  
      ├── resources
      |   └── base
      |       └── profile
      |           └── main_pages.json
      └── module.json5
  ```

- The following is an example:

  ![EmbeddedComponent](figures/embeddedComponent.png)
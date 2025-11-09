# In-Application Embedded Component (EmbeddedComponent)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @lmleon-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

The **EmbeddedComponent** allows the current page to embed UI content provided by other EmbeddedUIExtensionAbilities within the same application. These UIs run in independent processes, offering enhanced security and stability.

The **EmbeddedComponent** is primarily used for cross-module, cross-process embedded UI integration. Its core objective is to improve application flexibility and user experience through modular design.

Be aware of the component's usage constraints and lifecycle management to maximize its benefits in application architecture.

## Basic Concepts

- [EmbeddedComponent](../reference/apis-arkui/arkui-ts/ts-container-embedded-component.md)

  The **EmbeddedComponent** enables embedding UI content from another EmbeddedUIExtensionAbility within the same application. It supports modular development scenarios requiring process isolation, allowing flexible UI design by integrating specific functionalities or interfaces into another page.

- [EmbeddedUIExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-embeddedUIExtensionAbility.md)

  Defined and used in the provider application, the EmbeddedUIExtensionAbility enables cross-process UI embedding. It can only be launched by a UIAbility within the same application and requires multi-process permissions.

## Constraints

- Device Requirements

  The **EmbeddedComponent** is supported only on devices that support [EmbeddedUIExtensionAbility](../reference/apis-ability-kit/js-apis-app-ability-embeddedUIExtensionAbility.md).

- Applicable Scope

  The **EmbeddedComponent** can be used only in the UIAbility, and the EmbeddedUIExtensionAbility to start must belong to the same application as the UIAbility.

- Attribute Restrictions

  The **EmbeddedComponent** supports [universal attributes](../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md), with default and minimum width and height values set to 10 vp.
  
  The following width- and height-related attributes are not supported:
  **constraintSize**, **aspectRatio**, **layoutWeight**, **flexBasis**, **flexGrow**, and **flexShrink**.

- Event handling

  Event information related to screen coordinates is converted based on the position, width, and height of the **EmbeddedComponent**, before being passed to the EmbeddedUIExtensionAbility for processing.

  The **EmbeddedComponent** does not support universal events, including the [click event](../reference/apis-arkui/arkui-ts/ts-universal-events-click.md). It only supports the [onTerminated](../reference/apis-arkui/arkui-ts/ts-container-embedded-component.md#onterminated) and [onError](../reference/apis-arkui/arkui-ts/ts-container-embedded-component.md#onerror) events.

## Scenario Example

This example demonstrates the basic usage of the **EmbeddedComponent** and EmbeddedUIExtensionAbility.

**Host Page**

The host page is the parent page of the **EmbeddedComponent**, embedding and displaying the UI from the EmbeddedUIExtensionAbility. Below is a complete implementation:

```ts
import { Want } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  @State message: string = 'Message: '
  private want: Want = {
    bundleName: "com.example.embeddeddemo",
    abilityName: "ExampleEmbeddedAbility",
  }

  build() {
    Row() {
      Column() {
        Text(this.message).fontSize(30)
        EmbeddedComponent(this.want, EmbeddedType.EMBEDDED_UI_EXTENSION)
          .width('100%')
          .height('90%')
          .onTerminated((info) => {
            // Triggered when the terminateSelfWithResult button is clicked on the extension page.
            this.message = 'Termination: code = ' + info.code + ', want = ' + JSON.stringify(info.want);
          })
          .onError((error) => {
            // Triggered on failure or exception.
            this.message = 'Error: code = ' + error.code;
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

In an ArkTS project, the implementation code for EmbeddedUIExtensionAbility is typically located in the **ets/extensionAbility** directory of the project. For example, the **ExampleEmbeddedAbility.ets** file is located in the **./ets/extensionAbility/** directory.

Key considerations for implementing the host page:

- Multi-process model check

  Check whether the device has multi-process mode enabled during application startup. Provide clear error messages or guidance if it is disabled.

- Exception handling

  Use the [onError](../reference/apis-arkui/arkui-ts/ts-container-embedded-component.md#onerror) event to handle errors during embedded ability loading or execution.

- Lifecycle management

  Manage the lifecycle of the **EmbeddedComponent** to ensure proper resource cleanup.

- Style configuration

  Properly configure the size and position of the **EmbeddedComponent** to display embedded UIs as expected.

**Provider Application Lifecycle Implementation**

The provider application implements embedded UI extension abilities. Below is an example lifecycle implementation:

```ts
import { EmbeddedUIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';

const TAG: string = '[ExampleEmbeddedAbility]'

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

Key implementation details:

- Lifecycle stages

  **onCreate** -> **onForeground**: from initialization to the visible state.

  **onBackground** -> **onForeground**: state transition during foreground-background switching.

  **onDestroy**: resource cleanup when the component is actively destroyed by the host.

- Session management

  **onSessionCreate**: creates an independent storage context and loads the UI.

  **onSessionDestroy**: handles cleanup when the session ends.

- Context passing

  Use LocalStorage to pass the **UIExtensionContentSession** across components.

  Bind ArkTS pages to extension ability contexts through **loadContent**.

**Entry Page**

The following is an implementation of the entry component of the provider application, which demonstrates how to use **UIExtensionContentSession** and how to exit the embedded page and return the result through a button click event. This code file needs to be declared in the **main_pages.json** configuration file.

```ts
import { UIExtensionContentSession } from '@kit.AbilityKit';

@Entry
@Component
struct Extension {
  @State message: string = 'EmbeddedUIExtensionAbility Index';
  private localStorage: LocalStorage|undefined = this.getUIContext().getSharedLocalStorage();
  private session: UIExtensionContentSession | undefined = this.localStorage?.get<UIExtensionContentSession>('session');

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
            bundleName: "com.example.embeddeddemo",
            abilityName: "ExampleEmbeddedAbility",
          }
        });
      })
    }.width('100%').height('100%')
  }
}
```

Key considerations for implementing the entry page:

1. Session management

   Properly obtain and use the **UIExtensionContentSession** instances to ensure communication with the host application.

2. Result return

   When returning results to the host through **terminateSelfWithResult**, specify:

   - **resultCode**: result code.

   - **want**: recipient of the result.

3. Page lifecycle

   Manage the lifecycle of the entry page to ensure proper resource cleanup.

4. Style configuration

   Properly configure page element styles to display the page as expected.

**Configuration**

  To enable embedded UI extension abilities, configure the application's configuration file.

  Add the ExampleEmbeddedAbility configuration under the **extensionAbilities** tag in the **module.json5** file:

```json
{
  "name": "ExampleEmbeddedAbility",
  "srcEntry": "./ets/extensionAbility/ExampleEmbeddedAbility.ets",
  "type": "embeddedUI"
}
```

**Expected Results**

1. Start the application on the device that supports **EmbeddedUIExtensionAbility**.

   ![en-us_image_0000001502261065](figures/en-us_image_0000001502261065.jpg)

2. Clicking the **terminateSelfWithResult** button hides the provider content and displays **onTerminated** information on the host page.

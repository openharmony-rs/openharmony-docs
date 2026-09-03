# Class (TextMenuController)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=2eb91adacc6fee38616b0c2fc5e06efd616c5471 translatedAt=2026-08-05T03:00:33.346Z pushedAt=2026-08-06T03:42:37.278Z -->

The TextMenuController class is used to control the behavior of the text selection menu. It supports setting menu display options (such as displaying in a separate window with priority), disabling system service menu items or specific menu items. It is applicable to app scenarios where the text selection menu display mode needs to be customized or specific menu functions need to be restricted, such as disabling translation, search, and other functions in specific business scenarios.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 16.
>
> - **setMenuOptions** is a non-static API. You need to first use the [getTextMenuController()](arkts-apis-uicontext-uicontext.md#gettextmenucontroller16) method in UIContext to obtain a TextMenuController instance, and then call the corresponding method through this instance. **disableSystemServiceMenuItems** and **disableMenuItems** are static methods and can be called directly through the TextMenuController class.

## setMenuOptions<sup>16+</sup>

setMenuOptions(options: TextMenuOptions): void

Sets menu options. For example, when the text selection menu needs to be displayed in a separate window with priority under a specific UIContext, the menu display mode can be set through this API. If not set through this API, the text selection menu is displayed in the current window by default (showMode is TextMenuShowMode.DEFAULT).

**Atomic service API**: This API can be used in atomic services since API version 16.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type        | Mandatory  | Description  |
| -------- | ---------- | ---- | ---- |
| options | [TextMenuOptions](../apis-arkui/arkui-ts/ts-text-common.md#textmenuoptions16-object-description)| Yes    | Menu options for controlling the display mode of the text selection menu. |

**Example**

```ts
// xxx.ets
@Entry
@Component
struct Index {
  aboutToAppear(): void {
    // Set the UIContext to preferentially display the context menu on selection in a separate window.
    this.getUIContext()
      .getTextMenuController()
      .setMenuOptions(
        {
          showMode: TextMenuShowMode.PREFER_WINDOW
        }
      );
  }

  build() {
    Row() {
      Column() {
        TextInput({ text: 'This is a TextInput. Long press to display the text selection menu.' })
          .height(60)
          .fontStyle(FontStyle.Italic)
          .fontWeight(FontWeight.Bold)
          .textAlign(TextAlign.Center)
          .caretStyle({ width: '4vp' })

        Text('This is a Text. Long press to display the text selection menu.')
          .height(60)
          .copyOption(CopyOptions.InApp)
          .fontStyle(FontStyle.Italic)
          .fontWeight(FontWeight.Bold)
          .textAlign(TextAlign.Center)
      }.width('100%')
    }
    .height('100%')
  }
}
```

## disableSystemServiceMenuItems<sup>20+</sup>

static disableSystemServiceMenuItems(disable: boolean): void

Disables all system service menu items in the text selection menu. This is applicable to scenarios where the text selection menu needs to be fully customized, for example, in enterprise security apps where only basic functions such as copy, cut, select all, and paste are retained, and service menus such as search, translation, and share that may involve outgoing data transmission are disabled. If not set through this API, system service menu items are not disabled by default.

> **NOTE**
> 
> - This API takes effect globally for the entire app process after being called.
>
> - This API can be used in [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md).
>
> - After this API is called, it affects the text component's API [editMenuOptions](./arkui-ts/ts-basic-components-text.md#editmenuoptions12), and the input parameter list of its callback method [onCreateMenu](./arkui-ts/ts-text-common.md#oncreatemenu12) does not include the disabled menu options.
>
> - Components involving the text selection menu include [Text](./arkui-ts/ts-basic-components-text.md), [TextArea](./arkui-ts/ts-basic-components-textarea.md), [TextInput](./arkui-ts/ts-basic-components-textinput.md), [Search](./arkui-ts/ts-basic-components-search.md), [RichEditor](./arkui-ts/ts-basic-components-richeditor.md), and [Web](../apis-arkweb/arkts-basic-components-web.md).
>
> - System service menu items refer to menu items other than copy, cut, select all, and paste in [TextMenuItemId](./arkui-ts/ts-text-common.md#textmenuitemid12).
>
> - When both disableSystemServiceMenuItems and disableMenuItems are set, the method called first takes precedence. For example, if disableSystemServiceMenuItems(true) is called first and then disableMenuItems([...]) is called, the setting of disableSystemServiceMenuItems prevails. Conversely, if disableMenuItems([...]) is called first, the setting of disableMenuItems prevails. It is recommended to use only one of the two methods based on the actual disabling scope requirements and avoid calling both.
>
> - When this API is used, it takes effect globally, and if called multiple times, the last call prevails.
>
> - The disabled menu can be restored in the following three ways:
>
>   - If only disableSystemServiceMenuItems(true) is used to disable the menu, set it to false to restore the menu.
>   - If only disableMenuItems is used to disable the menu, set it to an empty array to restore the menu.
>   - If both disableSystemServiceMenuItems and disableMenuItems are used, set the former to false and the latter to an empty array to restore the menu.

**Atomic service API**: This API can be used in atomic services since API version 20.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type        | Mandatory  | Description  |
| -------- | ---------- | ---- | ---- |
| disable | boolean | Yes | Whether to disable the system service menu item. The value **true** indicates yes, and **false** indicates no. |

**Example**

```ts
import { TextMenuController } from '@kit.ArkUI';

// xxx.ets
@Entry
@Component
struct Index {
  aboutToAppear(): void {
    // Disable all system service menu items.
    TextMenuController.disableSystemServiceMenuItems(true);
  }

  aboutToDisappear(): void {
    // Restore system service menu items when the page disappears.
    TextMenuController.disableSystemServiceMenuItems(false);
  }

  build() {
    Row() {
      Column() {
        TextInput({ text: 'This is a TextInput. Long press to show the text selection menu.' })
          .height(60)
          .fontStyle(FontStyle.Italic)
          .fontWeight(FontWeight.Bold)
          .textAlign(TextAlign.Center)
          .caretStyle({ width: '4vp' })
          .editMenuOptions({
            onCreateMenu: (menuItems: Array<TextMenuItem>) => {
                // menuItems does not contain the disabled system menu items.
                return menuItems;
            },
            onMenuItemClick: (menuItem: TextMenuItem, textRange: TextRange) => {
                // The onMenuItemClick callback returns a boolean value.
                return false;
            }
          })
      }.width('100%')
    }
    .height('100%')
  }
}
```

## disableMenuItems<sup>20+</sup>

static disableMenuItems(items: Array\<TextMenuItemId>): void

Disables specified system service menu items in the text selection menu. This is applicable to scenarios where specific menu functions need to be disabled on demand, for example, disabling the search and translation menus to simplify the user interface or restrict access to external services. If not set through this API, no menu items are disabled by default.

> **NOTE**
> 
> - This API takes effect globally for the entire app process after being called.
>
> - This API can be used in [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md).
>
> - After this API is called, it affects the text component's API [editMenuOptions](./arkui-ts/ts-basic-components-text.md#editmenuoptions12), and the input parameter list of its callback method [onCreateMenu](./arkui-ts/ts-text-common.md#oncreatemenu12) does not include the disabled menu options.
>
> - Components involving the text selection menu include [Text](./arkui-ts/ts-basic-components-text.md), [TextArea](./arkui-ts/ts-basic-components-textarea.md), [TextInput](./arkui-ts/ts-basic-components-textinput.md), [Search](./arkui-ts/ts-basic-components-search.md), [RichEditor](./arkui-ts/ts-basic-components-richeditor.md), and [Web](../apis-arkweb/arkts-basic-components-web.md).
>
> - System service menu items refer to menu items other than copy, cut, select all, and paste in [TextMenuItemId](./arkui-ts/ts-text-common.md#textmenuitemid12).
>
> - When both disableSystemServiceMenuItems and disableMenuItems are set, the setting result of disableSystemServiceMenuItems that is set first prevails.
>
> - When this API is used, it takes effect globally, and if called multiple times, the last call prevails.
>
> - Disabling a first-level menu item also disables all its second-level menu items. For example, disabling the first-level menu item autoFill (parent menu item) in [TextMenuItemId](./arkui-ts/ts-text-common.md#textmenuitemid12) also disables the second-level menu item passwordVault (child menu item).
>
> - Disabling second-level menu items is not supported. If needed, this can be achieved by disabling the corresponding first-level menu item.
>
> - The disabled menu can be restored in the following three ways:
>
>   - If only disableSystemServiceMenuItems(true) is used to disable the menu, set it to false to restore the menu.
>   - If only disableMenuItems is used to disable the menu, set it to an empty array to restore the menu.
>   - If both disableSystemServiceMenuItems and disableMenuItems are used, set the former to false and the latter to an empty array to restore the menu.

**Atomic service API**: This API can be used in atomic services since API version 20.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type        | Mandatory  | Description  |
| -------- | ---------- | ---- | ---- |
| items | Array<[TextMenuItemId](./arkui-ts/ts-text-common.md#textmenuitemid12)> | Yes    | List of disabled menu items. Only system service menu items (excluding copy, cut, select all, and paste) can be disabled. Disabling a first-level menu item also disables all its second-level menu items. Second-level menu items cannot be disabled directly. |

**Example**

```ts
import { TextMenuController } from '@kit.ArkUI';

// xxx.ets
@Entry
@Component
struct Index {
  aboutToAppear(): void {
    // Disable search and translate menu items.
    TextMenuController.disableMenuItems([TextMenuItemId.SEARCH, TextMenuItemId.TRANSLATE]);
  }

  aboutToDisappear(): void {
    // Restore system service menu items.
    TextMenuController.disableMenuItems([]);
  }

  build() {
    Row() {
      Column() {
        TextInput({ text: 'This is a TextInput. Long press to show the text selection menu.' })
          .height(60)
          .fontStyle(FontStyle.Italic)
          .fontWeight(FontWeight.Bold)
          .textAlign(TextAlign.Center)
          .caretStyle({ width: '4vp' })
          .editMenuOptions({
            onCreateMenu: (menuItems: Array<TextMenuItem>) => {
              // The menuItems array does not include search and translate.
              return menuItems;
            },
            onMenuItemClick: (menuItem: TextMenuItem, textRange: TextRange) => {
              // The onMenuItemClick callback returns a boolean value.
              return false;
            }
          })
      }.width('100%')
    }
    .height('100%')
  }
}
```
<!--no_check-->
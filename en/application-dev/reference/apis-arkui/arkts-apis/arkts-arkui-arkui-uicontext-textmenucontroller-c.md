# TextMenuController

```TypeScript
export class TextMenuController
```

Provides the capability to control text menus.

> **NOTE:** 
> 
> - In the following non-static API examples, you must first use [getTextMenuController()](arkts-arkui-arkui-uicontext-uicontext-c.md#gettextmenucontroller) in **UIContext** to obtain a
> **TextMenuController** instance, and then call the APIs using the obtained instance.

**Since:** 16

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## disableMenuItems

```TypeScript
static disableMenuItems(items: Array<TextMenuItemId>): void
```

Disables specified system service menu items in the text selection menu.

> **NOTE:** 
> 
> - This API takes effect globally for the entire application process after being called.
> 
> - This API can be used in [UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md).
> 
> - After this API is called, the [editMenuOptions](../arkts-components/arkts-arkui-text-comp-attribute.md#editmenuoptions) API of text components will be affected. The parameter list of its [onCreateMenu](arkts-arkui-editmenuoptions-i.md#oncreatemenu) callback will not include the disabled menu options.
> 
> - Components involving text selection menus include the following: [Text](../arkts-components/arkts-arkui-text-comp.md#text),[TextArea](../arkts-components/arkts-arkui-textarea-comp.md#text_area), [TextInput](../arkts-components/arkts-arkui-textinput-comp.md#text_input),[Search](../arkts-components/arkts-arkui-search-comp.md#search), [RichEditor](../arkts-components/arkts-arkui-richeditor-comp.md#rich_editor), and [Web](../../apis-arkweb/arkts-components/arkts-arkweb-web-comp.md#web).
> 
> - System service menu items refer to menu items other than copy, cut, select all, and paste in [TextMenuItemId](arkts-arkui-textmenuitemid-c.md).
> 
> - When both **disableSystemServiceMenuItems** and **disableMenuItems** are set, the earlier-set
> **disableSystemServiceMenuItems** takes precedence.
> 
> - This API takes effect globally, and multiple calls are subject to the last call.
> 
> - Disabling a first-level menu item will also disable all its second-level menu items. For example, disabling the first-level menu item **autoFill** (parent item) in [TextMenuItemId](arkts-arkui-textmenuitemid-c.md) will simultaneously disable the second-level menu item **passwordVault** (child item) in **TextMenuItemId**.
> 
> - Disabling individual second-level menu items is not supported. If required, this can be achieved by disabling the corresponding first-level menu item.
> 
> - Disabled menus can be restored in the following ways:
> 
> - If only **disableSystemServiceMenuItems(true)** is used to disable menus, set it to **false** to restore.
> 
> - If only **disableMenuItems** is used to disable menus, set it to an empty array to restore.
> 
> - If both **disableSystemServiceMenuItems** and **disableMenuItems** are used, set the former to **false** and the latter to an empty array to restore.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| items | Array&lt;[TextMenuItemId](arkts-arkui-textmenuitemid-c.md)&gt; | Yes | List of menu items to disable. |

**Examples**

```TypeScript
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

## disableSystemServiceMenuItems

```TypeScript
static disableSystemServiceMenuItems(disable: boolean): void
```

Disables all system service menu items in the text selection menu.

> **NOTE:** 
> 
> - This API takes effect globally for the entire application process after being called.
> 
> - This API can be used in [UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md).
> 
> - After this API is called, the [editMenuOptions](../arkts-components/arkts-arkui-text-comp-attribute.md#editmenuoptions) API of text components will be affected. The parameter list of its [onCreateMenu](arkts-arkui-editmenuoptions-i.md#oncreatemenu) callback will not include the disabled menu options.
> 
> - Components involving text selection menus include the following: [Text](../arkts-components/arkts-arkui-text-comp.md#text),[TextArea](../arkts-components/arkts-arkui-textarea-comp.md#text_area), [TextInput](../arkts-components/arkts-arkui-textinput-comp.md#text_input),[Search](../arkts-components/arkts-arkui-search-comp.md#search), [RichEditor](../arkts-components/arkts-arkui-richeditor-comp.md#rich_editor), and [Web](../../apis-arkweb/arkts-components/arkts-arkweb-web-comp.md#web).
> 
> - System service menu items refer to menu items other than copy, cut, select all, and paste in [TextMenuItemId](arkts-arkui-textmenuitemid-c.md).
> 
> - When both **disableSystemServiceMenuItems** and **disableMenuItems** are set, the earlier-set
> **disableSystemServiceMenuItems** takes precedence.
> 
> - This API takes effect globally, and multiple calls are subject to the last call.
> 
> - Disabled menus can be restored in the following ways:
> 
> - If only **disableSystemServiceMenuItems(true)** is used to disable menus, set it to **false** to restore.
> 
> - If only **disableMenuItems** is used to disable menus, set it to an empty array to restore.
> 
> - If both **disableSystemServiceMenuItems** and **disableMenuItems** are used, set the former to **false** and the latter to an empty array to restore.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| disable | boolean | Yes | Whether to disable system service menu items. The value **true** means to disable system service menu items, and **false** means the opposite. |

**Examples**

```TypeScript
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

## setMenuOptions

```TypeScript
setMenuOptions(options: TextMenuOptions): void
```

Sets menu options.

**Since:** 16

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 16.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TextMenuOptions](arkts-arkui-textmenuoptions-i.md) | Yes | Menu options.<br>Default value: {showMode: TextMenuShowMode.DEFAULT}. |

**Examples**

```TypeScript
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

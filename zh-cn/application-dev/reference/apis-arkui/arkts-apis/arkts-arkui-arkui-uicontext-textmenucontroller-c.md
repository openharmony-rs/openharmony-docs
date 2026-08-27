# TextMenuController

TextMenuController用于控制文本选择菜单的行为，支持设置菜单显示选项（如优先使用独立窗口显示）、屏蔽系统服务菜单项或指定菜单项，适用于需要自定义文本选择菜单显示方式或限制特定菜单功能的应用场景，如在特定业务场景下禁用翻译、搜索等功能。

> **说明：**
> - setMenuOptions接口为非静态API，需先使用UIContext中的[getTextMenuController()](arkts-arkui-arkui-uicontext-uicontext-c.md#gettextmenucontroller)方法获取TextMenuController实例，再通过此实例调用对应方法。disableSystemServiceMenuItems和disableMenuItems为静态方法，可直接通过TextMenuController类调用。

**起始版本：** 16

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

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

屏蔽文本选择菜单内指定的系统服务菜单项。适用于需要按需禁用特定菜单功能的场景，例如禁用搜索和翻译菜单以简化用户界面或限制对外部服务的访问。未通过该接口设置时，默认不禁用任何菜单。

> **说明：**
> 
> 
> - 此接口调用后整个应用进程都会生效。
> 
> 
> - 此接口可在[UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md)使用。
> 
> 
> - 此接口调用后将影响文本组件的接口editMenuOptions，其回调方法
> onCreateMenu的入参列表中不包含被屏蔽的菜单选项。
> 
> 
> - 涉及文本选择菜单的组件有 Text、TextArea
> 、TextInput、Search、
> RichEditor、Web。
> 
> 
> - 系统服务菜单项指除[TextMenuItemId](arkts-arkui-textmenuitemid-c.md)中的复制、剪切、全选、粘贴以外的菜单项。
> 
> 
> - 当disableSystemServiceMenuItems与disableMenuItems同时设置时，以先设置的disableSystemServiceMenuItems的设置结果为准。。
> 
> 
> - 使用该接口时，全局生效，多次调用以最后一次为准。
> 
> 
> - 可以通过以下三种方式恢复禁用菜单：
> 
> 
> - 仅设置disableSystemServiceMenuItems(true)禁用菜单时，设置false即可恢复菜单；
> 
> 
> - 仅设置disableMenuItems禁用菜单时，设置为空数组即可恢复菜单；
> 
> 
> - 当disableSystemServiceMenuItems与disableMenuItems同时使用时，则前者设置为false，后者设置为空数组，即可恢复菜单。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | Array&lt;[TextMenuItemId](arkts-arkui-textmenuitemid-c.md)&gt; | 是 | 禁用菜单项的列表。仅支持禁用系统服务菜单项（复制、剪切、全选、粘贴除外），禁用一级菜单项会同时禁用其所有二级菜单项，不支持直接禁用二级菜单项。 。 |

**示例**

```TypeScript
import { TextMenuController } from '@kit.ArkUI';

// xxx.ets
@Entry
@Component
struct Index {
  aboutToAppear(): void {
    // 禁用搜索和翻译菜单。
    TextMenuController.disableMenuItems([TextMenuItemId.SEARCH, TextMenuItemId.TRANSLATE]);
  }

  aboutToDisappear(): void {
    // 恢复系统服务菜单。
    TextMenuController.disableMenuItems([]);
  }

  build() {
    Row() {
      Column() {
        TextInput({ text: '这是一个TextInput，长按弹出文本选择菜单' })
          .height(60)
          .fontStyle(FontStyle.Italic)
          .fontWeight(FontWeight.Bold)
          .textAlign(TextAlign.Center)
          .caretStyle({ width: '4vp' })
          .editMenuOptions({
            onCreateMenu: (menuItems: Array<TextMenuItem>) => {
              // menuItems不包含搜索和翻译。
              return menuItems;
            },
            onMenuItemClick: (menuItem: TextMenuItem, textRange: TextRange) => {
              // onMenuItemClick回调函数返回boolean类型
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

屏蔽文本选择菜单内所有系统服务菜单项。适用于需要完全自定义文本选择菜单的场景，例如企业安全应用中仅保留复制、剪切、全选、粘贴等基础功能，禁用搜索、翻译、分享等可能涉及数据外发的服务菜单。未通过该接口设置时，默认不禁用系统服务菜单项。

> **说明：**
> 
> 
> - 此接口调用后整个应用进程都会生效。
> 
> 
> - 此接口可在[UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md)使用。
> 
> 
> - 此接口调用后将影响文本组件的接口editMenuOptions，其回调方法onCreateMenu的入参列表中不包含被屏蔽的菜单选项。
> 
> 
> - 涉及文本选择菜单的组件有 Text、TextArea、TextInput、Search、RichEditor、Web。
> 
> 
> - 系统服务菜单项指除[TextMenuItemId](arkts-arkui-textmenuitemid-c.md)中的复制、剪切、全选、粘贴以外的菜单项。
> 
> 
> - 当disableSystemServiceMenuItems与disableMenuItems同时设置时，以先调用的方法为准。例如：先调用disableSystemServiceMenuItems(true)，再调用disableMenuItems([...])时，以disableSystemServiceMenuItems的设置为准；反之，先调用disableMenuItems([...])时，则以disableMenuItems的设置为准。建议根据实际禁用范围需求选择使用其中一个方法，避免同时调用。
> 
> 
> - 使用该接口时，全局生效，多次调用以最后一次为准。
> 
> 
> - 可以通过以下三种方式恢复禁用菜单：
> 
> 
> - 仅设置disableSystemServiceMenuItems(true)禁用菜单时，设置false即可恢复菜单；
> 
> 
> - 仅设置disableMenuItems禁用菜单时，设置为空数组即可恢复菜单；
> 
> 
> - 当disableSystemServiceMenuItems与disableMenuItems同时使用时，则前者设置为false，后者设置为空数组，即可恢复菜单。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| disable | boolean | 是 | 是否禁用系统服务菜单项。true表示禁用，false表示不禁用。 |

**示例**

```TypeScript
import { TextMenuController } from '@kit.ArkUI';

// xxx.ets
@Entry
@Component
struct Index {
  aboutToAppear(): void {
    // 禁用所有系统服务菜单。
    TextMenuController.disableSystemServiceMenuItems(true);
  }

  aboutToDisappear(): void {
    // 页面消失恢复系统服务菜单。
    TextMenuController.disableSystemServiceMenuItems(false);
  }

  build() {
    Row() {
      Column() {
        TextInput({ text: '这是一个TextInput，长按弹出文本选择菜单' })
          .height(60)
          .fontStyle(FontStyle.Italic)
          .fontWeight(FontWeight.Bold)
          .textAlign(TextAlign.Center)
          .caretStyle({ width: '4vp' })
          .editMenuOptions({
            onCreateMenu: (menuItems: Array<TextMenuItem>) => {
                // menuItems不包含被屏蔽的系统菜单项。
                return menuItems;
            },
            onMenuItemClick: (menuItem: TextMenuItem, textRange: TextRange) => {
                // onMenuItemClick回调函数返回boolean类型。
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

设置菜单选项。例如，需要在特定UIContext下优先使用独立窗口显示文本选择菜单时，可通过此接口设置菜单的显示模式。未通过该接口设置时，文本选择菜单默认在当前窗口显示（showMode为TextMenuShowMode.DEFAULT）。

**起始版本：** 16

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本16开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TextMenuOptions](arkts-arkui-textmenuoptions-i.md) | 是 | 设置菜单选项，用于控制文本选择菜单的显示模式。 默认值：{showMode: TextMenuShowMode.DEFAULT}。 |

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  aboutToAppear(): void {
    // 设置在对应的UIContext下优先使用独立窗口显示文本选择菜单
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
        TextInput({ text: '这是一个TextInput，长按弹出文本选择菜单' })
          .height(60)
          .fontStyle(FontStyle.Italic)
          .fontWeight(FontWeight.Bold)
          .textAlign(TextAlign.Center)
          .caretStyle({ width: '4vp' })

        Text('这是一个Text，长按弹出文本选择菜单')
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

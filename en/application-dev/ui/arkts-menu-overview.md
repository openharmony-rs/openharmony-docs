# Menu Overview
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Armstrong15-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

A menu is a pop-up window that allows users to perform specific actions. It typically appears when users right-click, long-press, or touch an item.

## When to Use

| API|Use Case |
| ----------| ----------------------------------- |
| [Menu control (Menu)](arkts-popup-and-menu-components-menu.md)| Used to bind actions to specified components, such as displaying operation options when an icon is long-pressed.|
| [Global menu independent of UI components (openMenu)](arkts-popup-and-menu-components-uicontext-menu.md)| Used to provide operation options in scenarios where UI components cannot be directly accessed, for example, in event callbacks.|

## Constraints

* When [bindMenu](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md#bindmenu11) is triggered via the **isShow** parameter or [bindContextMenu](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md#bindcontextmenu12) is triggered via the **isShown** parameter, the menu requires complete page construction before display. Therefore, avoid setting **isShow** or **isShown** to **true** during the page build phase, as this may cause incorrect menu positioning and rendering.
* When using **openMenu**, you must provide valid [TargetInfo](../reference/apis-arkui/arkts-apis-uicontext-i.md#targetinfo18). Otherwise, the menu won't display correctly.
* For details about other specifications, see [Menu Control](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md) and [openMenu](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#openmenu18).


## Lifecycle

The normal sequence is **aboutToAppear** > **onWillAppear** > **onAppear** > **onDidAppear** > **aboutToDisappear** > **onWillDisappear** > **onDisappear** > **onDidDisappear**.

| Name| Type| Description|
| --- | --- | --- |
| aboutToAppear  | () =>  void | Callback invoked when the menu is about to appear.|
| onAppear | () =>  void | Callback invoked after the menu appears.|
| aboutToDisappear | () =>  void | Callback invoked when the menu is about to disappear.|
| onDisappear  | () =>  void | Callback invoked after the menu disappears.|
| onWillAppear | [Callback&lt;void&gt;](../reference/apis-arkui/arkui-ts/ts-types.md#callback12) | Callback invoked before the menu appearance animation.<br>Note: **aboutToAppear** is invoked during initialization; **onWillAppear** is invoked before the animation starts; **onWillAppear** is invoked after **aboutToAppear**.|
| onDidAppear | [Callback&lt;void&gt;](../reference/apis-arkui/arkui-ts/ts-types.md#callback12) |  Callback invoked after the menu appears.<br>**NOTE**<br>1. If you quickly tap the button, the menu will be quickly displayed and then disappear. In this case, **onWillDisappear** may take effect before **onDidAppear**.<br>2. If the menu is closed before the menu entrance animation is complete, this callback is not triggered.<br>3. **onAppear** and **onDidAppear** are invoked at the same time. **onDidAppear** takes effect after **onAppear**.|
| onWillDisappear | [Callback&lt;void&gt;](../reference/apis-arkui/arkui-ts/ts-types.md#callback12) | Callback invoked before the menu disappearance animation.<br>**NOTE**<br>1. If you quickly tap the button, the menu will be quickly displayed and then disappear. In this case, **onWillDisappear** may take effect before **onDidAppear**.<br>2. **aboutToDisappear** and **onWillDisappear** are invoked at the same time. **onWillDisappear** takes effect after **aboutToDisappear**.|
| onDidDisappear | [Callback&lt;void&gt;](../reference/apis-arkui/arkui-ts/ts-types.md#callback12) | Callback invoked after the menu disappears.<br>Note: **onDisappear** and **onDidDisappear** are triggered at the same time. **onDidDisappear** takes effect after **onDisappear**.|

# Menu Overview
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Armstrong15-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @HelloCrease-->

A menu is a pop-up window that allows users to perform specific actions. It typically appears when users right-click, long-press, or touch an item.

## When to Use

| API|Use Case |
| ----------| ----------------------------------- |
| [Menu control (Menu)](arkts-popup-and-menu-components-menu.md)| Used to bind actions to specified components, such as displaying operation options when an icon is long-pressed.|
| [Global menu independent of UI components (openMenu)](arkts-popup-and-menu-components-uicontext-menu.md)| Used to show options in scenarios where UI components cannot be directly accessed, for example, in event callbacks.|

## Constraints

* When [bindMenu](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md#bindmenu11) is triggered via the **isShow** parameter or [bindContextMenu](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md#bindcontextmenu12) is triggered via the **isShown** parameter, the menu requires complete page construction before display. Therefore, avoid setting **isShow** or **isShown** to **true** during the page build phase, as this may cause incorrect menu positioning and rendering.
* When using **openMenu**, you must provide valid [TargetInfo](../reference/apis-arkui/arkts-apis-uicontext-i.md#targetinfo18). Otherwise, the menu won't display correctly.
* For details about other specifications, see [Menu Control](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md) and [openMenu](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#openmenu18).

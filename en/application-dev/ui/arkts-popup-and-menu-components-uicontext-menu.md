# Global Menu Independent of UI Components (openMenu)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Armstrong15-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

The [Menu](arkts-popup-and-menu-components-menu.md) component is a great option for creating menus, but it relies on a bound UI component to work. Since API version 18, however, the global API [openMenu](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#openmenu18) offers a more flexible solution. This API can be used directly or encapsulated in scenarios where no bound UI components are available, making it ideal for use cases such as event callbacks or when integrating with external systems.

## Displaying a Menu

To display a menu, call the [openMenu](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#openmenu18). The following is a basic example:

 <!-- @[open_menu](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/Menu/globalmenusindependentofuicomponents/GlobalOpenMenu.ets) -->

 ``` TypeScript
 this.getUIContext().getPromptAction()
   .openMenu(this.contentNode, { id: targetId }, {
     enableArrow: true
   })
   .then(() => {
     hilog.info(0xFF00, 'globalOpenMenu', 'openMenu success');
   })
   .catch((err: BusinessError) => {
     hilog.error(0xFF00, 'globalOpenMenu', 'openMenu error: ' + err.code + ' ' + err.message);
   });
 ```

 ![openMenu](figures/openMenu.gif)

### Creating a ComponentContent Instance

When using **openMenu**, you need to provide a [ComponentContent](../reference/apis-arkui/js-apis-arkui-ComponentContent.md) instance to define the menu content. **wrapBuilder(buildText)** encapsulates the custom component, and **new Params(this.message)** is the input parameter for the custom component. This parameter is optional and can be a basic data type.

  <!-- @[content_node](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/Menu/globalmenusindependentofuicomponents/GlobalOpenMenu.ets) -->

  ``` TypeScript
  private contentNode: ComponentContent<Object> =
    new ComponentContent(this.getUIContext(), wrapBuilder(buildText), this.message);
  ```

If your **wrapBuilder** includes other components (such as [Popup](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-Popup.md) or [Chip](../reference/apis-arkui/arkui-ts/ohos-arkui-advanced-Chip.md)), the [ComponentContent](../reference/apis-arkui/js-apis-arkui-ComponentContent.md#componentcontent-1) constructor must include four parameters, and the **options** parameter must be **{ nestingBuilderSupported: true }**.

 <!-- @[build_text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/Menu/globalmenusindependentofuicomponents/GlobalOpenMenu.ets) -->

 ``` TypeScript
 @Builder
 export function buildText(params: Params) {
   Popup({
     // Set the icon for the menu.
     icon: {
       // Replace $r('app.media.app_icon') with the actual resource file.
       image: $r('app.media.app_icon'),
       width: 32,
       height: 32,
       fillColor: Color.White,
       borderRadius: 10
     } as PopupIconOptions,
     // Set the text content.
     title: {
       text: `This is a Popup title 1`,
       fontSize: 20,
       fontColor: Color.Black,
       fontWeight: FontWeight.Normal
     } as PopupTextOptions,
     // Set the text content.
     message: {
       text: `This is a Popup message 1`,
       fontSize: 15,
       fontColor: Color.Black
     } as PopupTextOptions,
     // Set the buttons.
     buttons: [{
       text: 'confirm',
       action: () => {
         hilog.info(0xFF00, 'globalOpenMenu', 'confirm button click');
       },
       fontSize: 15,
       fontColor: Color.Black,
     },
       {
         text: 'cancel',
         action: () => {
           hilog.info(0xFF00, 'globalOpenMenu', 'cancel button click');
         },
         fontSize: 15,
         fontColor: Color.Black
       },] as [PopupButtonOptions?, PopupButtonOptions?]
   })
 }
 
 let contentNode: ComponentContent<Object> =
   new ComponentContent(uiContext, wrapBuilder(buildText), message, { nestingBuilderSupported: true });
 ```

 


### Providing Bound Component Information

When calling **openMenu**, you must provide the [TargetInfo](../reference/apis-arkui/arkts-apis-uicontext-i.md#targetinfo18) of the bound component. Without a valid target, the menu won't display.

 <!-- @[frame_node](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/Menu/globalmenusindependentofuicomponents/GlobalOpenMenu.ets) -->

 ``` TypeScript
 let frameNode: FrameNode | null = this.getUIContext().getFrameNodeByUniqueId(this.getUniqueId());
 let targetId = frameNode?.getChild(0)?.getUniqueId();
 ```


### Customizing the Menu Style

When calling **openMenu**, you can customize the menu style using [MenuOptions](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md#menuoptions10). Note that the **title** property is not effective, and the **preview** parameter supports only the [MenuPreviewMode](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md#menupreviewmode11) type.

  <!-- @[menu_options](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/Menu/globalmenusindependentofuicomponents/GlobalOpenMenu.ets) -->

  ``` TypeScript
  private options: MenuOptions = { enableArrow: true, placement: Placement.Bottom };
  ```

## Updating the Menu Style

To update the menu style, use the [updateMenu](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#updatemenu18) API, supported since API version 18. You can update the style fully or incrementally. However, the following properties cannot be updated: **showInSubWindow** in [MenuOptions](../reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md#menuoptions10), **preview**, **previewAnimationOptions**, **transition**, **onAppear**, **aboutToAppear**, **onDisappear**, **aboutToDisappear**, **onWillAppear**, **onDidAppear**, **onWillDisappear**, and **onDidDisappear**.

<!-- @[update_menu](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/Menu/globalmenusindependentofuicomponents/GlobalOpenMenu.ets) -->

``` TypeScript
this.getUIContext().getPromptAction()
  .updateMenu(this.contentNode, {
    enableArrow: false
  }, true)
  .then(() => {
    hilog.info(0xFF00, 'globalOpenMenu', 'updateMenu success');
  })
  .catch((err: BusinessError) => {
    hilog.error(0xFF00, 'globalOpenMenu', 'updateMenu error: ' + err.code + ' ' + err.message);
  });
```

   ![openMenu](figures/openMenu.gif)

## Closing the Menu

To close the menu, use the [closeMenu](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#closemenu18) API, supported since API version 18.

<!-- @[close_menu](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/DialogProject/entry/src/main/ets/pages/Menu/globalmenusindependentofuicomponents/GlobalOpenMenu.ets) --> 

``` TypeScript
this.getUIContext().getPromptAction()
  .closeMenu(this.contentNode)
  .then(() => {
    hilog.info(0xFF00, 'globalOpenMenu', 'closeMenu success');
  })
  .catch((err: BusinessError) => {
    hilog.error(0xFF00, 'globalOpenMenu', 'closeMenu error: ' + err.code + ' ' + err.message);
  });
```

![openMenu](figures/openMenu.gif)

> **NOTE**
>
> The [updateMenu](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#updatemenu18) and [closeMenu](../reference/apis-arkui/arkts-apis-uicontext-promptaction.md#closemenu18) APIs rely on the content to identify the menu. Therefore, you must maintain the content instance throughout the menu's lifecycle.

## Using the Global Menu in HAR Packages

You can encapsulate a menu using the [HAR](../quick-start/har-package.md) package to provide display, update, and close capabilities.

For details about how to invoke these capabilities, see [Using the Global Popup in HAR Packages](./arkts-popup-and-menu-components-uicontext-popup.md#using-the-global-popup-in-har-packages).

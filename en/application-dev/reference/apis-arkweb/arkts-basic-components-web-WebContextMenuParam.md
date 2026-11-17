# Class (WebContextMenuParam)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @zhufenghao-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

Implements a **WebContextMenuParam** object, which is displayed after the user clicks the right mouse button or long presses a specific element, such as an image or a link. For details about the sample code, see [onContextMenuShow](./arkts-basic-components-web-events.md#oncontextmenushow9).

The [@ohos.transfer](../apis-arkts/js-apis-transfer.md) system object conversion tool can be used to convert dynamic and static classes.

> **NOTE**
>
> - This module supports both ArkTS-Dyn and ArkTS-Sta.
>
> - The initial APIs of this component are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 9.
>
> - The sample effect is subject to the actual device.

## constructor<sup>9+</sup>

constructor()

Constructs a **WebContextMenuParam** object.

**System capability**: SystemCapability.Web.Webview.Core

**ArkTS-Dyn start version**: 9

**ArkTS-Sta start version**: 23

## x<sup>9+</sup>

ArkTS-Dyn: x(): number

ArkTS-Sta: x(): int

Obtains the X coordinate of the context menu.

**System capability**: SystemCapability.Web.Webview.Core

**ArkTS-Dyn start version**: 9

**ArkTS-Sta start version**: 23

**Return value**

| Type    | Description                |
| ------ | ------------------ |
| ArkTS-Dyn: number<br>ArkTS-Sta: int | If the display is normal, a non-negative integer is returned. Otherwise, **-1** is returned.<br>Unit: px (physical pixel)|

## y<sup>9+</sup>

ArkTS-Dyn: y(): number

ArkTS-Sta: y(): int

Obtains the Y coordinate of the context menu.

**System capability**: SystemCapability.Web.Webview.Core

**ArkTS-Dyn start version**: 9

**ArkTS-Sta start version**: 23

**Return value**

| Type    | Description                |
| ------ | ------------------ |
| ArkTS-Dyn: number<br>ArkTS-Sta: int | If the display is normal, a non-negative integer is returned. Otherwise, **-1** is returned.<br>Unit: px (physical pixel)|

## getLinkUrl<sup>9+</sup>

getLinkUrl(): string

Obtains the URL that has passed the security check.

**System capability**: SystemCapability.Web.Webview.Core

**ArkTS-Dyn start version**: 9

**ArkTS-Sta start version**: 23

**Return value**

| Type    | Description                       |
| ------ | ------------------------- |
| string | If it is a link that is being long pressed, the URL that has passed the security check is returned.|

## getUnfilteredLinkUrl<sup>9+</sup>

getUnfilteredLinkUrl(): string

Obtains the original URL.

**System capability**: SystemCapability.Web.Webview.Core

**ArkTS-Dyn start version**: 9

**ArkTS-Sta start version**: 23

**Return value**

| Type    | Description                   |
| ------ | --------------------- |
| string | If it is a link that is being long pressed, the original URL is returned.|

## getSourceUrl<sup>9+</sup>

getSourceUrl(): string

Obtains the source URL.

**System capability**: SystemCapability.Web.Webview.Core

**ArkTS-Dyn start version**: 9

**ArkTS-Sta start version**: 23

**Return value**

| Type    | Description                      |
| ------ | ------------------------ |
| string | If the selected element has the **src** attribute, the URL in the **src** is returned. The maximum size of the returned URL is 2 MB. If the size exceeds the upper limit, an empty string is returned.|

## existsImageContents<sup>9+</sup>

existsImageContents(): boolean

Checks whether image content exists.

**System capability**: SystemCapability.Web.Webview.Core

**ArkTS-Dyn start version**: 9

**ArkTS-Sta start version**: 23

**Return value**

| Type     | Description                       |
| ------- | ------------------------- |
| boolean | The value **true** means that there is image content in the element being long pressed, and **false** means the opposite.|

## getMediaType<sup>9+</sup>

getMediaType(): ContextMenuMediaType

Obtains the media type of this web page element.

**System capability**: SystemCapability.Web.Webview.Core

**ArkTS-Dyn start version**: 9

**ArkTS-Sta start version**: 23

**Return value**

| Type                                      | Description       |
| ---------------------------------------- | --------- |
| [ContextMenuMediaType](./arkts-basic-components-web-e.md#contextmenumediatype9) | Media type of the web page element.|

## getSelectionText<sup>9+</sup>

getSelectionText(): string

Obtains the selected text.

**System capability**: SystemCapability.Web.Webview.Core

**ArkTS-Dyn start version**: 9

**ArkTS-Sta start version**: 23

**Return value**

| Type    | Description                  |
| ------ | -------------------- |
| string | Selected text for the context menu. If no text is selected, null is returned.|

## getSourceType<sup>9+</sup>

getSourceType(): ContextMenuSourceType

Obtains the event source of the context menu.

**System capability**: SystemCapability.Web.Webview.Core

**ArkTS-Dyn start version**: 9

**ArkTS-Sta start version**: 23

**Return value**

| Type                                      | Description     |
| ---------------------------------------- | ------- |
| [ContextMenuSourceType](./arkts-basic-components-web-e.md#contextmenusourcetype9) | Event source of the context menu.|

## getInputFieldType<sup>9+</sup>

getInputFieldType(): ContextMenuInputFieldType

Obtains the input field type of this web page element.

**System capability**: SystemCapability.Web.Webview.Core

**ArkTS-Dyn start version**: 9

**ArkTS-Sta start version**: 23

**Return value**

| Type                                      | Description    |
| ---------------------------------------- | ------ |
| [ContextMenuInputFieldType](./arkts-basic-components-web-e.md#contextmenuinputfieldtype9) | Input field type.|

## isEditable<sup>9+</sup>

isEditable(): boolean

Checks whether a web page element is editable.

**System capability**: SystemCapability.Web.Webview.Core

**ArkTS-Dyn start version**: 9

**ArkTS-Sta start version**: 23

**Return value**

| Type     | Description                        |
| ------- | -------------------------- |
| boolean | **true** is returned if the web page element is editable; otherwise, **false** is returned.|

## getEditStateFlags<sup>9+</sup>

ArkTS-Dyn: getEditStateFlags(): number

ArkTS-Sta: getEditStateFlags(): int

Obtains the edit state flag of this web page element.

**System capability**: SystemCapability.Web.Webview.Core

**ArkTS-Dyn start version**: 9

**ArkTS-Sta start version**: 23

**Return value**

| Type    | Description                                      |
| ------ | ---------------------------------------- |
| ArkTS-Dyn: number<br>ArkTS-Sta: int | Edit state flag of the web page element. For details, see [ContextMenuEditStateFlags](./arkts-basic-components-web-e.md#contextmenueditstateflags9).|

## getPreviewWidth<sup>13+</sup>

ArkTS-Dyn: getPreviewWidth(): number

ArkTS-Sta: getPreviewWidth(): int

Obtains the width of a preview image.

**System capability**: SystemCapability.Web.Webview.Core

**ArkTS-Dyn start version**: 13

**ArkTS-Sta start version**: 23

**Return value**

| Type    | Description      |
| ------ | ----------- |
| ArkTS-Dyn: number<br>ArkTS-Sta: int | Width of a preview image.<br>Unit: px (physical pixel)|

## getPreviewHeight<sup>13+</sup>

ArkTS-Dyn: getPreviewHeight(): number

ArkTS-Sta: getPreviewHeight(): int

Obtains the height of a preview image.

**System capability**: SystemCapability.Web.Webview.Core

**ArkTS-Dyn start version**: 13

**ArkTS-Sta start version**: 23

**Return value**

| Type    | Description      |
| ------ | ----------  |
| ArkTS-Dyn: number<br>ArkTS-Sta: int | Height of a preview image.<br>Unit: px (physical pixel)|

## getContextMenuMediaType<sup>22+</sup>

getContextMenuMediaType(): ContextMenuDataMediaType

Obtains the type of the web page element that the user taps when the context menu event is reported.

**System capability**: SystemCapability.Web.Webview.Core

**ArkTS-Dyn start version**: 22

**ArkTS-Sta start version**: 23

**Return value**

| Type    | Description      |
| ------ | ----------  |
| [ContextMenuDataMediaType](./arkts-basic-components-web-e.md#contextmenudatamediatype22) | Media type of the web page element.|

## Type Conversion of WebContextMenuParam Using @ohos.transfer

Use the WebContextMenuParam object of ArkTS-Sta in ArkTS-Dyn.

- In the ArkTS-Sta module, convert the ArkTS-Sta WebContextMenuParam into the ArkTS-Dyn WebContextMenuParam and pass it to the ArkTS-Dyn submodule `library`.

  ArkTS-Sta example:

  ```TypeScript
  'use static'
  import { Entry, Column, Component, Web, OnContextMenuShowEvent, $rawfile } from '@kit.ArkUI';
  import { webview } from '@kit.ArkWeb';
  import { transfer } from '@kit.ArkTS';
  import { handleWebContextMenuParamDynamic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController(undefined);

    build() {
      Column() {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .onContextMenuShow((event: OnContextMenuShowEvent): boolean => {
            console.info('onContextMenuShow invoked');
            try {
                let webContextMenuParamDynamic = transfer.transferDynamic(event.param, "ArkWeb.WebContextMenuParam") as Object;
                handleWebContextMenuParamDynamic(webContextMenuParamDynamic);
            } catch (e: Error) {
                console.error('transferDynamic catch error: -----------' + e.message);
            }
            return false;
          })
      }
    }
  }
  ```
  HTML file to be loaded:
  ```html
  <!-- index.html -->
  <!DOCTYPE html>
  <html lang="en">
  <body>
    <h1>onContextMenuShow</h1>
    <a href="http://www.example.com" style="font-size:27px">URL www.example.com</a>
    // Place any image in the rawfile directory and name it example.png.
    <div><img src="example.png"></div>
    <p>Right-click text to display the context menu</p>
  </body>
  </html>
  ```

- Create an ArkTS-Dyn submodule `library` and provide a method for receiving ArkTS-Dyn WebContextMenuParam in the `library/src/main/ets/components` directory.

  ArkTS-Dyn example:

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  export function handleWebContextMenuParamDynamic(param_: any) {
    let param: WebContextMenuParam = param_ as WebContextMenuParam;
    console.info('x: ' + param.x());
    console.info('y: ' + param.y());
    console.info('LinkUrl: ' + param.getLinkUrl());
    console.info('SourceUrl: ' + param.getSourceUrl());
  }
  ```

Use the WebContextMenuParam object of ArkTS-Dyn in ArkTS-Sta.

- Create the ArkTS-Dyn WebContextMenuParam object in the ArkTS-Dyn module and pass it to the ArkTS-Sta submodule `library`.

  ArkTS-Dyn example:

  ```TypeScript
  import { webview } from '@kit.ArkWeb';
  import { handleWebContextMenuParamStatic } from 'library';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .onContextMenuShow((event: OnContextMenuShowEvent): boolean => {
            console.info('onContextMenuShow invoked');
            handleWebContextMenuParamStatic(event.param);
            return false;
          })
      }
    }
  }
  ```
  HTML file to be loaded:
  ```html
  <!-- index.html -->
  <!DOCTYPE html>
  <html lang="en">
  <body>
    <h1>onContextMenuShow</h1>
    <a href="http://www.example.com" style="font-size:27px">URL www.example.com</a>
    // Place any image in the rawfile directory and name it example.png.
    <div><img src="example.png"></div>
    <p>Right-click text to display the context menu</p>
  </body>
  </html>
  ```

- Create an ArkTS-Sta submodule `library` and provide a method for receiving ArkTS-Dyn WebContextMenuParam in the `library/src/main/ets/components` directory.

  ArkTS-Sta example:

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  'use static'
  import { WebContextMenuParam } from '@kit.ArkUI';
  import { transfer } from '@kit.ArkTS';

  export function handleWebContextMenuParamStatic(dynObject: Object) {
    try {
        let param: WebContextMenuParam = transfer.transferStatic(dynObject, "ArkWeb.WebContextMenuParam") as WebContextMenuParam;
        console.info('x: ' + param.x());
        console.info('y: ' + param.y());
        console.info('LinkUrl: ' + param.getLinkUrl());
        console.info('SourceUrl: ' + param.getSourceUrl());
    } catch (e: Error) {
        console.error('transferStatic catch error: -----------' + e.message);
    }
  }
  ```
<!--no_check-->
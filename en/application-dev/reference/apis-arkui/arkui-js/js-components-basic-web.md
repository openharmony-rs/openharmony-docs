# web

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zourongchun-->
<!--Designer: @kurli1-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=9fc8de61c9856085ad7066dda1e30828589acb6a translatedAt=2026-06-09T03:13:50.217Z pushedAt=2026-06-09T07:45:57.971Z -->

The **\<web>** component displays web page content.
>**NOTE**
>
>This component is supported since API version 6. Updates will be marked with a superscript to indicate their earliest API version.

## Required Permissions

ohos.permission.INTERNET, required only for accessing online web pages.

## Constraints

The **\<web>** component does not follow the transition animation. A page allows only one **\<web>** component.

## Child Components

Not supported

## Attributes

| Name| Type| Default Value| Mandatory| Description|
| -------- | -------- | -------- | -------- | -------- |
| src      | string |   -    |   No     |Address of the web page to be displayed. The domain name of the address must use the HTTPS protocol and have completed ICP filing. If not set, no web page is displayed.|
| id  | string | -  | No  |Unique ID of the component. It is required when you need to call component methods (such as **reload**) through JavaScript code. If not set, a component instance cannot be obtained through **$element**.|

## Styles

Universal style settings are not supported.

## Events

Only the following events are supported.

| Name| Parameter| Description|
| -------- |  -------- | -------- |
| pagestart      | {url: string} | Triggered when web page loading starts.|
| pagefinish  | {url: string} |  Triggered when web page loading is completed. |
| error  | {url: string, errorCode: number, description: string} |Triggered when an error occurs during web page loading or opening. For details about the error codes, see [Webview Error Codes](../../apis-arkweb/errorcode-webview.md) and [Universal Error Codes](../../errorcode-universal.md).|

## Methods

The following methods are supported.

| Name| Parameter| Description|
| -------- |  -------- | -------- |
| reload      | - | Reloads a page.|

## Example

```html
<!-- xxx.hml -->
<div style="height: 500px; width: 500px; flex-direction: column;">
    <button onclick="reloadWeb">click to reload</button>
    <web src="www.example.com" id="web" onpagestart="pageStart" onpagefinish="pageFinish" on:error="pageError"></web>
</div>
```

```js
// xxx.js
export default {
    reloadWeb() {
        this.$element('web').reload()
    },

    pageStart: function(e) {
        console.info('web pageStart: ' + e.url)
    },

    pageFinish: function(e) {
        console.info('web pageFinish: ' + e.url)
    },

    pageError: function(e) {
        console.info('web pageError url: ' + e.url)
        console.info('web pageError errorCode: ' + e.errorCode)
        console.info('web pageError description: ' + e.description)
    }
}
```
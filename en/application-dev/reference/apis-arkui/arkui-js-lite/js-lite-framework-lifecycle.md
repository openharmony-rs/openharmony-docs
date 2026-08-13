# Lifecycle

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @huangxiaolinabc-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @Giacinta-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=828befee530895124aaf1637c9402999a598c883 translatedAt=2026-07-31T01:13:31.784Z pushedAt=2026-07-31T12:04:26.588Z -->

A lifecycle describes status changes of an application or page from creation, display, and hiding to destruction. You can use application lifecycle and page lifecycle functions to process logic such as initialization, page display and hiding response, destruction, and cleanup in corresponding stages. This method can be used to manage application startup and exit, page switching, and foreground and background status changes, helping you organize service logic and manage resources by stage.

## Application Lifecycle

You can define the following application lifecycle methods in the **app.js** file.

| Attribute     | Type      | Description    | Called When          |
| --------- | ---------- | -------- | ------------------ |
| onCreate  | () => void | App creation | Triggered when the application is created. |
| onDestroy | () => void | Application uninstallation | Triggered when the application exits.|

## Page Lifecycle

You can define the following page lifecycle functions in the **.js** file of the page.

> **NOTE**
>
> To prevent affecting the page switching performance, do not perform complex, time-consuming operations in a lifecycle function.

| Attribute     | Type      | Description        | Called When                              |
| --------- | ---------- | ------------ | -------------------------------------- |
| onInit    | () => void | Listens for page initialization.  | Page initialization is complete. This function is called only once in the page lifecycle.|
| onReady   | () => void | Listens for page creation.| A page is created. This function is called only once in the page lifecycle.      |
| onShow    | () => void | Listens for page display.    | The page is displayed.                      |
| onHide    | () => void | Listens for page hiding.    | The page is hidden.                      |
| onDestroy | () => void | Listens for page destruction.    | The page is destroyed.                      |

The lifecycle functions of page A are called in the following sequence:

- Open page A: **onInit()** -> **onReady()** -> **onShow()**

- Open page B on page A: **onHide()** -> **onDestroy()**

- Go back to page A from page B: **onInit()** -> **onReady()** -> **onShow()**

- Exit page A: **onHide()** -> **onDestroy()**

- Hide page A: **onHide()**

- Show background page A on the foreground: **onShow()**

![img](figures/lifecycle.png)
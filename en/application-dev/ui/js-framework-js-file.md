# app.js
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=3b17ae247298f1cf952b1cbdcb60f1ff0e80beac translatedAt=2026-11-12T04:11:25.250Z pushedAt=2026-11-13T09:11:07.728Z nl=1 -->

## Application Lifecycle

You can customize the [lifecycle](../ui/js-framework-lifecycle.md) implementation logic on an application-by-application basis in app.js. The following example only prints the corresponding logs in the lifecycle function:
```js
// app.js
export default {
    onCreate() {
        console.info('Application onCreate');
    },

    onDestroy() {
        console.info('Application onDestroy');
    },
}
```

## Application Object<sup>6+</sup>

| Property    | Type      | Description                                      |
| ------ | -------- | ---------------------------------------- |
| getApp | Function | Obtains the object exposed in the **app.js** file from the custom **.js** file.|

The following is a sample code snippet:

```js
// app.js
export default {
    data: {
        test: "by getApp"
    },
    onCreate() {
        console.info('AceApplication onCreate');
    },
    onDestroy() {
        console.info('AceApplication onDestroy');
    },
}
```

```js
// test.js custom logic code.
export var appData = getApp().data;
```

# app.js

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=828befee530895124aaf1637c9402999a598c883 translatedAt=2026-07-31T01:13:18.194Z pushedAt=2026-07-31T12:04:26.583Z -->

The app.js file defines application-level lifecycle functions and global data objects of an application. It can execute initialization or resource release logic during application creation and destruction, and supports global data sharing between different pages. This file can be used to implement unified management of the application status and lifecycle.

## Application Lifecycle<sup>4+</sup>

You can implement lifecycle logic specific to your application in the app.js file. Available application lifecycle functions are as follows:

- **onCreate()**: called when an application is created

- **onDestroy()**: called when an application is destroyed

In the following example, logs are printed only in the lifecycle functions.

```js
// app.js
export default {
  onCreate() {
    console.info('Application onCreate');
  },
  onDestroy() {
    console.info('Application onDestroy');
  },
};
```

## Application Object <sup>10+</sup>

| Attribute    | Type      | Description                                      |
| ------ | -------- | ---------------------------------------- |
| getApp | Function | Obtains the object exposed in the app.js file from the JS file of the page. This API works globally. To be compatible with earlier versions that do not support the getApp API, check whether the API is available before using it. |

> **NOTE**
>
> The application object is global data and occupies JS memory before the application exits. Although it facilitates data sharing between different pages, exercise caution when using it on small-sized devices, whose available memory is usually limited. If the application object stores too much data or data that occupies a large amount of memory, an exception may occur due to insufficient memory when a page that contains many components or resources is opened.

The following is an example:

Declare the application object in **app.js**.

```javascript
// app.js
export default {
    data: {
        name: 'by getApp'
    },
    onCreate() {
        console.info('Application onCreate');
    },
    onDestroy() {
        console.info('Application onDestroy');
    },
};
```

Access the app object on a specific page.

```javascript
// index.js
export default {
    data: {
        title: ''
    },
    onInit() {
        if (typeof getApp !== 'undefined') {
            var appData = getApp().data;
            if (typeof appData !== 'undefined') {
                this.title = appData.name; // read from app data
            }
        }
    },
    clickHandler() {
        if (typeof getApp !== 'undefined') {
            var appData = getApp().data;
            if (typeof appData !== 'undefined') {
                appData.name = this.title; // write to app data
            }
        }
    }
};
```

> **NOTE**
>
> To ensure that the application can run properly on an earlier version that does not support **getApp**, compatibility processing must be performed in the code. That is, before using **getApp**, check whether it is available.
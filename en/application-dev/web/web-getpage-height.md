# Obtaining the Web Page Content Height
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhou-ke13-->
<!--Designer: @LongLie-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

The [getPageHeight](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#getpageheight) API can obtain the actual height of the current web page content. You can select a proper method as required.

## When to Use

The height obtained during web page loading may be inaccurate, especially when the rendering is not complete. The value will be updated after dynamic content is loaded. The web page content may take a long time to load. To speed up the initial loading, many websites use dynamic loading. When the first frame of a web page is displayed, remaining images and content continue to load.
You are advised to not obtain the height of a non-static web page during the [onPageEnd](../reference/apis-arkweb/arkts-basic-components-web-events.md#onpageend), [onPageVisible](../reference/apis-arkweb/arkts-basic-components-web-events.md#onpagevisible9), [onFirstContentfulPaint](../reference/apis-arkweb/arkts-basic-components-web-events.md#onfirstcontentfulpaint10) and [onFirstMeaningfulPaint](../reference/apis-arkweb/arkts-basic-components-web-events.md#onfirstmeaningfulpaint12) callbacks. You need to obtain the actual height of the current web page content through JSBridge or delay in a specific callback notification on the frontend based on the characteristics of the current web page.

## Common Static Page

For a common static web page, you can obtain the page content height through **getPageHeight()** in the **Web** component lifecycle callback (such as **onPageEnd**) and web performance metric callback.

Code on the application side:
```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct Index {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Row() {
      Column() {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .onPageEnd(() => {
            console.info("page height: onPageEnd: " + this.controller.getPageHeight());
          })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

## Using JSBridge to Transfer Specific Callbacks for Complex Dynamic Web Pages

The dynamic web page can pass a specific callback through JSBridge to notify the application side to call it.

Code on the application side:
```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

class TestClass {
  testController: webview.WebviewController;

  constructor(controller: webview.WebviewController) {
    this.testController = controller;
  }

  notifyToGet(): void {
    console.info("page height:" + this.testController.getPageHeight());
  }
}

@Entry
@Component
struct Index {
  controller: webview.WebviewController = new webview.WebviewController();
  @State jsbObj: TestClass = new TestClass(this.controller);

  build() {
    Row() {
      Column() {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .javaScriptAccess(true)
          .javaScriptProxy({
            object: this.jsbObj,
            name: "jsbObj",
            methodList: ["notifyToGet"],
            controller: this.controller
          })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

### Loading a Common Web Page

For a common web page, you can trigger height measurement via the load event once all resources have finished loading.

Frontend code:
```html
<!--index.html-->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<script>
    window.addEventListener("load", function() {
        if (typeof jsbObj !== 'undefined') {
            jsbObj.notifyToGet();
        } else {
            console.info("jsbObj is error");
        }
    })
</script>
</body>
</html>
```

### Loading a Web Page with Large Images

When a web page contains large images, use the image loading completion callback to trigger the height measurement.

Replace the image in the frontend code with a real image.
```html
<!--index.html-->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<img src="example.jpg" id="largeImage" alt="Large Image">
<script>
    var img = document.getElementById('largeImage');

    img.addEventListener('load', function() {
        if (typeof jsbObj !== 'undefined') {
            jsbObj.notifyToGet();
        } else {
            console.info("jsbObj is error");
        }
    });
</script>
</body>
</html>
```

### Loading a Web Page with a Large Number of Images

When a web page contains a large number of images, trigger the height measurement after all images are loaded.

Replace the image in the frontend code with a real image.
```html
<!--index.html-->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <img src="example1.jpg" >
    <img src="example2.jpg" >
<script>
    function waitForImages() {
        const images = Array.from(document.images);
        const promises = images.map(img => {
            if (img.complete) return Promise.resolve();
            return new Promise(resolve => {
                img.onload = img.onerror = resolve;
            });
        });

        return Promise.all(promises).then(() => {
            if (typeof jsbObj !== 'undefined') {
                jsbObj.notifyToGet();
            } else {
                console.info("jsbObj is error");
            }
        })
    }
    document.addEventListener("DOMContentLoaded", waitForImages);
</script>
</body>
</html>
```

## Scenarios Where JSBridge Cannot Be Used

If JSBridge is unavailable, you can add functions such as **setTimeout** to delay the height measurement of the current page. You can determine the specific delay time based on the complexity of the web page.

Code on the application side:
```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';

@Entry
@Component
struct Index {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Row() {
      Column() {
        Web({ src: $rawfile('index.html'), controller: this.controller })
          .onPageEnd(() => {
            setTimeout(()=>{
                console.info("page height: onPageEnd: setTimeout: " + this.controller.getPageHeight());
            },2000)
          })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

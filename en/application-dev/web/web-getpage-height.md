# Obtaining the Web Page Content Height
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhou-ke13-->
<!--Designer: @LongLie-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

You can call [getPageHeight](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#getpageheight) to obtain the actual height of the current web page content. You can select a proper method based on the site requirements.

## Use Cases

The height obtained during web page loading may be inaccurate, especially when the web page is not rendered. This is because the value will be updated after dynamic content is loaded. Web page content may take a long time to load. Nowadays, to optimize the first loading speed, websites use dynamic web page loading technologies. When users see the first frame of a web page, the web page background is still dynamically loading the page, especially the page that contains images and dynamic content.
It is not recommended that you obtain the height of a non-static web page in the lifecycle callback of web components such as [onPageEnd](../reference/apis-arkweb/arkts-basic-components-web-events.md#onpageend), [onPageVisible](../reference/apis-arkweb/arkts-basic-components-web-events.md#onpagevisible9), [onFirstContentfulPaint](../reference/apis-arkweb/arkts-basic-components-web-events.md#onfirstcontentfulpaint10) and [onFirstMeaningfulPaint](../reference/apis-arkweb/arkts-basic-components-web-events.md#onfirstmeaningfulpaint12) or web performance indicator callback. You need to obtain the actual height of the current web page content in a specific callback notification on the frontend based on the characteristics of the current web page through JSBridge or delay.

## Common Static Display Page

For a common static web page, you can obtain the web page height by calling getPageHeight in the lifecycle callback (such as onPageEnd) and web performance indicator callback.

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

Dynamic web pages can transfer specific callbacks through JSBridge to notify the app side of the call.

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

The load event can be triggered when all resources of a common web page are loaded.

Frontend Code
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
</script>>
</body>
</html>
```

### Loading a Web Page with a Large Image

When a web page contains a large image, the image loading completion callback can be used to trigger the loading.

Replace the image in the frontend code with the actual image.
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
</script>>
</body>
</html>
```

### Web Page with a Large Number of Images

This event is triggered when all images on an image-intensive web page are loaded.

Replace the images in the frontend code with actual images.
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

## JSBridge Unavailable

If JSBridge is unavailable, you can add functions such as setTimeout to delay the obtaining of the height of the current page. The delay time can be determined based on the complexity of the web page.

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

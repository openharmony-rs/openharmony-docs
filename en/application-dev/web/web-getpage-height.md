# Obtaining the Web Page Content Height
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @sinat_22543221-->
<!--Designer: @dzichou-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=db997b7b2bf80ce82bf23c07da01ff7aca61a238 translatedAt=2026-11-05T10:40:51.535Z pushedAt=2026-11-05T11:55:36.522Z nl=1 -->

The [getPageHeight](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#getpageheight) API can obtain the actual height of the current web page content. You can select a proper method as required.

## When to Use

The height obtained during web page loading may be inaccurate, especially when the rendering is not complete. The value will be updated after dynamic content is loaded. The web page content may take a long time to load. To optimize the first-load speed, websites currently use dynamic web page loading techniques. When you see the first frame of a web page, the page resources are still being loaded dynamically, especially for pages that contain images and dynamic content.

For a non-static web page, you are advised to not obtain the web page content height in the [onPageEnd](../reference/apis-arkweb/arkts-basic-components-web-events.md#onpageend), [onPageVisible](../reference/apis-arkweb/arkts-basic-components-web-events.md#onpagevisible9), [onFirstContentfulPaint](../reference/apis-arkweb/arkts-basic-components-web-events.md#onfirstcontentfulpaint10), and [onFirstMeaningfulPaint](../reference/apis-arkweb/arkts-basic-components-web-events.md#onfirstmeaningfulpaint12) events, which are Web component lifecycle callbacks and Web performance metric callbacks. Instead, based on the characteristics of the current web page, obtain the actual height of the web page content in a specific frontend callback notification through JSBridge or a delayed approach.

## Common Static Page

For a common static web page, you can obtain the page content height through **getPageHeight()** in the **Web** component lifecycle callback (such as **onPageEnd**) and web performance metric callback.

Code on the application side:
<!-- @[ordinary_static_display_page](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ArkWebPageHeight/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
@Component
struct Scene1Static {
  controller: webview.WebviewController = new webview.WebviewController();
  @State heightText: ResourceStr = $r('app.string.waiting_for_height');

  build() {
    Column() {
      Text('getPageHeight: ' + this.heightText)
        .width('100%')
        .padding(12)
        .fontSize(16)
        .backgroundColor('#f5f5f5')
        .textAlign(TextAlign.Center)

      Web({ src: $rawfile('scene1_index.html'), controller: this.controller })
        .layoutWeight(1)
        .onPageEnd(() => {
          this.heightText = $r('app.string.scene1_on_page_end');
          setTimeout(() => {
            try {
              const h: number = this.controller.getPageHeight();
              console.info(`page height: onPageEnd: ${h}`);
              this.heightText = String(h) + ' px';
            } catch (err) {
              console.error(`page height: onPageEnd error: ${JSON.stringify(err)}`);
              this.heightText = $r('app.string.get_height_failed');
            }
          }, 300)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## Using JSBridge to Transfer Specific Callbacks for Complex Dynamic Web Pages

The dynamic web page can pass a specific callback through JSBridge to notify the application side to call it.

Code on the application side:
<!-- @[complex_dynamic_web_pages](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ArkWebPageHeight/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
@Component
struct Scene2JsBridge {
  controller: webview.WebviewController = new webview.WebviewController();
  @State heightText: ResourceStr = $r('app.string.waiting_for_height');
  @State jsbObj: TestClass = new TestClass(this.controller);

  aboutToAppear(): void {
    this.jsbObj.onGetHeight = (h: string) => {
      this.heightText = h + ' px';
    };
  }

  build() {
    Column() {
      Text('getPageHeight: ' + this.heightText)
        .width('100%')
        .padding(12)
        .fontSize(16)
        .backgroundColor('#f5f5f5')
        .textAlign(TextAlign.Center)

      Web({ src: $rawfile('scene2_index.html'), controller: this.controller })
        .layoutWeight(1)
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
            console.error("jsbObj is undefined");
        }
    })
</script>
</body>
</html>
```

### Loading a Web Page with Large Images

When a web page contains large images, use the image loading completion callback to trigger the height measurement.

In the frontend code, replace the sample image path with the actual image resource.
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
            console.error("jsbObj is undefined");
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
                console.error("jsbObj is undefined");
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
<!-- @[jsb_cannot_be_used](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ArkWebPageHeight/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
@Component
struct Scene3SetTimeout {
  controller: webview.WebviewController = new webview.WebviewController();
  @State heightText: ResourceStr = $r('app.string.waiting_for_height');

  build() {
    Column() {
      Text('getPageHeight: ' + this.heightText)
        .width('100%')
        .padding(12)
        .fontSize(16)
        .backgroundColor('#f5f5f5')
        .textAlign(TextAlign.Center)

      Web({ src: $rawfile('scene3_index.html'), controller: this.controller })
        .layoutWeight(1)
        .onPageEnd(() => {
          this.heightText = $r('app.string.scene3_on_page_end');
          setTimeout(() => {
            try {
              const h: number = this.controller.getPageHeight();
              console.info(`page height: onPageEnd: setTimeout: ${h}`);
              this.heightText = String(h) + ' px';
            } catch (err) {
              console.error(`page height: onPageEnd setTimeout error: ${JSON.stringify(err)}`);
              this.heightText = $r('app.string.get_height_failed');
            }
          }, 2000)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

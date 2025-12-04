# Implementing Content Scrolling
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @zhufenghao-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

A web page can be scrolled only when its content height or width exceeds the visible area. You can scroll a web page by using external devices, or by calling APIs on the ArkTS or JS side.

## Using External Devices

You can use the touchscreen, touchpad, and mouse to scroll the web page.
+ Through the touchscreen, you can swipe up, down, left, or right with a single finger to scroll the web page.
+ Through the touchpad, you can swipe up, down, left, or right on the laptop to scroll the web page.
+ Through the mouse, you can scroll up and down the mouse wheel to control the scrolling of the Web page.

## Calling ArkTS APIs
+ [scrollTo](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#scrollto): scrolls the page to a specified absolute position within a specified period.

  Return to the top of the page.

  <!-- @[scrollTo_ArkTS_one](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/WebScrollDemo/entry/src/main/ets/pages/WebScrollDemo.ets) -->
  
  ``` TypeScript
  this.webController.scrollTo(0, 0);
  ```
+ [scrollBy](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#scrollby): scrolls the page by a specified offset within a specified period.

  This API can be used to control the scrolling of **Web** components in nested scrolling. For details, see [Distributing Scrolling Offsets Through the Parent Scroll Component](web-nested-scrolling.md#distributing-scrolling-offsets-through-the-parent-scroll-component)

+ [pageUp](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#pageup): scrolls up the Webview content by half of the viewport or jumps to the top of the page based on the input parameter **top**.
+ [pageDown](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#pagedown): scrolls down the Webview content by half of the viewport or jumps to the bottom of the page based on the input parameter **bottom **.
## Calling JS APIs
+ **scrollBy**: scrolls by a certain distance relative to the current position (a positive number is downward/rightward, and a negative number is upward/leftward).

  ```javascript
  window.scrollBy (deltaX, deltaY);// deltaX indicates the scrolling distance of the element on the horizontal axis, and deltaY indicates the scrolling distance of the element on the vertical axis.
  ```
  Progressive scrolling (such as the **Read more** button).
  ```javascript
  document.getElementById("read-more").addEventListener("click", ()=>{
    window.scrollBy(0, 300);
  })
  ```
+ **scrollTo**: scrolls the page to the absolute coordinate position.
  ```javascript
  window.scrollTo (x, y);// X is the pixel of the element to be displayed in the upper left corner along the horizontal axis, and Y is the pixel of the element to be displayed in the upper left corner along the vertical axis.
  ```
  (1) Return to the top of the page.
  ```javascript
  window.scrollTo(0, 0);
  ```
  (2) Jump to a specific position on the page.
  ```javascript
  window.scrollTo (0, 500); // Scroll to a fixed pixel position (for example, 500 px).
  ```

## Scrolling to the Top by Tapping the Status Bar

By calling the [backToTop](../reference/apis-arkweb/arkts-basic-components-web-attributes.md#backtotop22) method, you can touch the status bar to interrupt the fling and scroll back to the top of the web page.

+ The sample code is as follows:
  ```ts
  // xxx.ets
  import { webview } from '@kit.ArkWeb';

  @Entry
  @Component
  struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();

    build() {
      Column() {
        Web({ src: $rawfile("index.html"), controller: this.controller })
          .backToTop(true)
      }
    }
  }
  ```

  HTML file to be loaded:
  ```html
  <!-- index.html -->
  <!DOCTYPE html>
  <html>
  <head>
      <meta name="viewport" id="viewport" content="width=device-width, initial-scale=1.0">
      <style>
          .blue {
            background-color: lightblue;
          }
          .green {
            background-color: lightgreen;
          }
          .blue, .green {
           font-size:16px;
           height:200px;
           text-align: center;       /* Horizontally centered */
           line-height: 200px;       /* Vertically centered (the height matches the container height) */
          }
      </style>
  </head>
  <body>
  <div class="blue" >webArea</div>
  <div class="green">webArea</div>
  <div class="blue">webArea</div>
  <div class="green">webArea</div>
  <div class="blue">webArea</div>
  <div class="green">webArea</div>
  <div class="blue">webArea</div>
  <div class="green">webArea</div>
  <div class="blue">webArea</div>
  </body>
  </html>
  ```

+ Effect<br>
![backToTop](figures/backToTop.gif)

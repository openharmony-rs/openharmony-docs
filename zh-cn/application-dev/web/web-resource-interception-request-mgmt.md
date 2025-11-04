# 自定义页面请求响应
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->


Web组件支持在应用拦截到页面请求后自定义响应请求能力。开发者通过[onInterceptRequest()](../reference/apis-arkweb/arkts-basic-components-web-events.md#oninterceptrequest9)接口来实现自定义资源请求响应 。自定义请求能力可以用于开发者自定义Web页面响应、自定义文件资源响应等场景。


Web网页上发起资源加载请求，应用层收到资源请求信息。应用层构造本地资源响应信息发送给Web内核。Web内核解析应用层响应信息，根据此响应信息进行页面资源加载。


在下面的示例中，Web组件通过拦截页面请求“https://www.example.com/test.html”， 在应用侧代码构建响应资源，实现自定义页面响应场景。


- 前端页面index1.html代码。

  ```html
  <!DOCTYPE html>
  <html>
  <head>
      <meta charset="utf-8">
  </head>
  <body>
  <!-- 页面资源请求 -->
  <a href="https://www.example.com/test.html">intercept test!</a>
  </body>
  </html>
  ```

- 应用侧代码。
  <!-- @[build_response_resources_to_implement_custom_page_response_scenarios](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/CustomizePageResp/entry/src/main/ets/pages/OnInterceptRequest_one.ets) -->

- 被拦截后的页面

  ![输入图片说明](figures/web-rescource-interception-request-1.PNG)

为自定义的JavaScript请求响应生成 CodeCache：自定义请求响应的资源类型如果是JavaScript脚本，可以在响应头中添加“ResponseDataID”字段，Web内核读取到该字段后会在为该JS资源生成CodeCache，加速JS执行，并且ResponseData如果有更新时必须更新该字段。不添加“ResponseDataID”字段的情况下默认不生成CodeCache。

在下面的示例中，Web组件通过拦截页面请求“https://www.example.com/test.js”， 应用侧代码构建响应资源，在响应头中添加“ResponseDataID”字段，开启生成CodeCache的功能。

- 前端页面index2.html代码。

  ```html
  <!DOCTYPE html>
  <html>
  <head>
      <meta charset="utf-8">
  </head>
  <body>
  
  <div id="div-1">this is a test div</div>
  <div id="div-2">this is a test div</div>
  <div id="div-3">this is a test div</div>
  <div id="div-4">this is a test div</div>
  <div id="div-5">this is a test div</div>
  <div id="div-6">this is a test div</div>
  <div id="div-7">this is a test div</div>
  <div id="div-8">this is a test div</div>
  <div id="div-9">this is a test div</div>
  <div id="div-10">this is a test div</div>
  <div id="div-11">this is a test div</div>
  
  <script src="https://www.example.com/test.js"></script>
  </body>
  </html>
  ```

- 应用侧代码。
  <!-- @[build_response_resource_enable_gen](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/CustomizePageResp/entry/src/main/ets/pages/OnInterceptRequest_two.ets) -->

- 被拦截后的页面

  ![输入图片说明](figures/web-rescource-intercption-request-2.PNG)
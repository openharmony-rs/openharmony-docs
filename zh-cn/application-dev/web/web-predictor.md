# 加速Web页面的访问
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

当Web页面加载缓慢时，可以使用预连接、预加载和预获取post请求的能力加速Web页面的访问。
针对Web页面加载性能优化的详细内容请参考[Web页面加载优化性能指导](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-web-develop-optimization#section128761465256)

## 预解析和预连接

此方法可以针对域名级进行优化，通过[prepareForPageLoad()](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#prepareforpageload10)来预解析或者预连接将要加载的页面。该方式仅对url进行DNS解析以及建立tcp连接，但不会获取主资源子资源。

  在下面的示例中，在Web组件的onAppear中对要加载的页面进行预连接。

<!-- @[previously_connect_in_onAppear_to_pages_being_loaded](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/AcceleratePageAccess/entry1/src/main/ets/pages/Index.ets) -->

也可以通过[initializeWebEngine()](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#initializewebengine)来提前初始化内核，然后在初始化内核后调用[prepareForPageLoad()](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#prepareforpageload10)对即将要加载的页面进行预解析、预连接。这种方式适合提前对首页进行预解析、预连接。

  在下面的示例中，Ability的onCreate中提前初始化Web内核并对首页进行预连接。

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    console.info("EntryAbility onCreate");
    webview.WebviewController.initializeWebEngine();
    // 预连接时，需要将'https://www.example.com'替换成真实要访问的网站地址。
    webview.WebviewController.prepareForPageLoad("https://www.example.com/", true, 2);
    AppStorage.setOrCreate("abilityWant", want);
    console.info("EntryAbility onCreate done");
  }
}
```

## 预加载

此方法可针对资源级进行优化。如果能够预测到Web组件将要加载的页面或者即将要跳转的页面。可以通过[prefetchPage()](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#prefetchpage10)来预加载即将要加载页面。

预加载会提前下载页面所需的资源，包括主资源子资源，避免阻塞页面渲染。但不会执行网页JavaScript代码。预加载是WebviewController的实例方法，需要一个已经关联好Web组件的WebviewController实例。

在下面的示例中，在onPageEnd的时候触发下一个要访问的页面的预加载。
  
<!-- @[on_page_end_triggers_preload_of_next_page](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/AcceleratePageAccess/entry2/src/main/ets/pages/Prefetching.ets) -->

## 预获取post请求

此方法可以针对请求级进行优化。可以通过[prefetchResource()](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#prefetchresource12)预获取将要加载页面中的post请求。在页面加载结束时，可以通过[clearPrefetchedResource()](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#clearprefetchedresource12)清除后续不再使用的预获取资源缓存。

  以下示例，在Web组件onAppear中，对要加载页面中的post请求进行预获取。在onPageEnd中，可以清除预获取的post请求缓存。

<!-- @[prefetch_post_request_on_page_end_clear_cache](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/AcceleratePageAccess/entry2/src/main/ets/pages/PrefetchingAPOSTRequest_one.ets) -->

如果能够预测到Web组件将要加载页面或者即将要跳转页面中的post请求。可以通过[prefetchResource()](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#prefetchresource12)预获取即将要加载页面的post请求。

  以下示例，在onPageEnd中，触发预获取一个要访问页面的post请求。

<!-- @[on_page_end_trigger_prefetch_post_request_access_page](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/AcceleratePageAccess/entry2/src/main/ets/pages/PrefetchingAPOSTRequest_three.ets) -->

也可以通过[initializeWebEngine()](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#initializewebengine)提前初始化内核，然后在初始化内核后调用[prefetchResource()](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#prefetchresource12)预获取将要加载页面中的post请求。这种方式适合提前预获取首页的post请求。

  以下示例，在Ability的onCreate中，提前初始化Web内核并预获取首页的post请求。

```ts
// xxx.ets
import { webview } from '@kit.ArkWeb';
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam) {
    console.info("EntryAbility onCreate");
    webview.WebviewController.initializeWebEngine();
    // 预获取时，需要将"https://www.example1.com/post?e=f&g=h"替换成真实要访问的网站地址。
    webview.WebviewController.prefetchResource(
      {
        url: "https://www.example1.com/post?e=f&g=h",
        method: "POST",
        formData: "a=x&b=y",
      },
      [{
        headerKey: "c",
        headerValue: "z",
      },],
      "KeyX", 500);
    AppStorage.setOrCreate("abilityWant", want);
    console.info("EntryAbility onCreate done");
  }
}
```

## 预编译生成编译缓存

可以通过[precompileJavaScript()](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#precompilejavascript12)在页面加载前提前生成脚本文件的编译缓存。

推荐配合动态组件使用，使用离线的Web组件用于生成字节码缓存，并在适当的时机加载业务用Web组件使用这些字节码缓存。下方是代码示例：

1. 首先，在EntryAbility中将UIContext存到localStorage中。

   ```ts
   // EntryAbility.ets
   import { UIAbility } from '@kit.AbilityKit';
   import { window } from '@kit.ArkUI';

   const localStorage: LocalStorage = new LocalStorage('uiContext');

   export default class EntryAbility extends UIAbility {
     storage: LocalStorage = localStorage;

     onWindowStageCreate(windowStage: window.WindowStage) {
       windowStage.loadContent('pages/Index', this.storage, (err, data) => {
         if (err.code) {
           return;
         }

         this.storage.setOrCreate<UIContext>("uiContext", windowStage.getMainWindowSync().getUIContext());
       });
     }
   }
   ```

2. 编写动态组件所需基础代码。

   <!-- @[underlying_code_required_for_dynamic_components](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/AcceleratePageAccess/entry3/src/main/ets/pages/DynamicComponent.ets) -->

3. 编写用于生成字节码缓存的组件，本例中的本地Javascript资源内容通过文件读取接口读取rawfile目录下的本地文件。

   <!-- @[read_local_js_resource_from_rawfile_dir_via_file_api](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/AcceleratePageAccess/entry3/src/main/ets/pages/PrecompileWebview.ets) -->

JavaScript资源的获取方式也可通过[网络请求](../reference/apis-network-kit/js-apis-http.md)的方式获取，但此方法获取到的http响应头非标准HTTP响应头格式，需额外将响应头转换成标准HTTP响应头格式后使用。如通过网络请求获取到的响应头是e-tag，则需要将其转换成E-Tag后使用。

4. 编写业务用组件代码。

   <!-- @[write_code_for_business_components](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/AcceleratePageAccess/entry3/src/main/ets/pages/BusinessWebview.ets) -->

5. 编写资源配置信息。

   <!-- @[compile_resource_allocation_information](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/AcceleratePageAccess/entry3/src/main/ets/pages/PrecompileConfig.ets) -->

6. 在页面中使用。

   <!-- @[dynamic_webview_component_loading](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/AcceleratePageAccess/entry3/src/main/ets/pages/Index.ets) -->

当需要更新本地已经生成的编译字节码时，修改cacheOptions参数中responseHeaders中的E-Tag或Last-Modified响应头对应的值，再次调用接口即可。

## 离线资源免拦截注入
可以通过[injectOfflineResources()](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#injectofflineresources12)在页面加载前提前将图片、样式表或脚本资源注入到应用的内存缓存中。

推荐配合动态组件使用，使用离线的Web组件用于将资源注入到内核的内存缓存中，并在适当的时机加载业务用Web组件使用这些资源。下方是代码示例：

1. 首先，在EntryAbility中将UIContext存到localStorage中。

   ```ts
   // EntryAbility.ets
   import { UIAbility } from '@kit.AbilityKit';
   import { window } from '@kit.ArkUI';

   const localStorage: LocalStorage = new LocalStorage('uiContext');

   export default class EntryAbility extends UIAbility {
     storage: LocalStorage = localStorage;

     onWindowStageCreate(windowStage: window.WindowStage) {
       windowStage.loadContent('pages/Index', this.storage, (err, data) => {
         if (err.code) {
           return;
         }

         this.storage.setOrCreate<UIContext>("uiContext", windowStage.getMainWindowSync().getUIContext());
       });
     }
   }
   ```

2. 编写动态组件所需基础代码。

   <!-- @[underlying_code_required_for_dynamic_components](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/AcceleratePageAccess/entry4/src/main/ets/pages/DynamicComponent.ets) -->

3. 编写用于注入资源的组件代码，本例中的本地资源内容通过文件读取接口读取rawfile目录下的本地文件。

   <!-- @[local_resources_content_read_from_rawfile_directory_by_file_operation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/AcceleratePageAccess/entry4/src/main/ets/pages/InjectWebview.ets) -->

4. 编写业务用组件代码。

   <!-- @[write_code_for_business_components](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/AcceleratePageAccess/entry4/src/main/ets/pages/BusinessWebview.ets) -->

5. 编写资源配置信息。

   <!-- @[compile_resource_allocation_information](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/AcceleratePageAccess/entry4/src/main/ets/pages/Resource.ets) -->
   
   ``` TypeScript
   import { webview } from '@kit.ArkWeb';
   
   export interface ResourceConfig {
     urlList: Array<string>,
     type: webview.OfflineResourceType,
     responseHeaders: Array<Header>,
     localPath: string, // 本地资源存放在rawfile目录下的路径
   }
   
   export const resourceConfigs: ResourceConfig[] = [
     {
       localPath: 'example.png',
       urlList: [
         'https://www.example.com/',
         'https://www.example.com/path1/example.png',
         'https://www.example.com/path2/example.png',
       ],
       type: webview.OfflineResourceType.IMAGE,
       responseHeaders: [
         { headerKey: 'Cache-Control', headerValue: 'max-age=1000' },
         { headerKey: 'Content-Type', headerValue: 'image/png' },
       ]
     },
     {
       localPath: 'example.js',
       urlList: [ // 仅提供一个url，这个url既作为资源的源，也作为资源的网络请求地址
         'https://www.example.com/example.js',
       ],
       type: webview.OfflineResourceType.CLASSIC_JS,
       responseHeaders: [
         // 以<script crossorigin='anonymous' />方式使用，提供额外的响应头
         { headerKey: 'Cross-Origin', headerValue:'anonymous' }
       ]
     },
   ];
   ```

6. 在页面中使用。
   <!-- @[dynamic_webview_component_loading](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkWeb/ManageWebPageLoadBrowse/AcceleratePageAccess/entry4/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import { webview } from '@kit.ArkWeb';
   import { NodeController } from '@kit.ArkUI';
   import { createNode } from './DynamicComponent';
   import { injectWebview } from './InjectWebview';
   import { businessWebview } from './BusinessWebview';
   
   @Entry
   @Component
   struct Index {
     @State injectNode: NodeController | undefined = undefined;
     injectController: webview.WebviewController = new webview.WebviewController();
   
     @State businessNode: NodeController | undefined = undefined;
     businessController: webview.WebviewController = new webview.WebviewController();
   
     aboutToAppear(): void {
       // 初始化用于注入本地资源的Web组件, 提供一个空的html页面作为url即可
       this.injectNode = createNode(injectWebview,
         { url: 'https://www.example.com/empty.html', controller: this.injectController, context: this.getUIContext()});
     }
   
     build() {
       Column() {
         // 在适当的时机加载业务用Web组件，本例以Button点击触发为例
         Button('加载页面')
           .onClick(() => {
             this.businessNode = createNode(businessWebview, {
               url: 'https://www.example.com/business.html',
               controller: this.businessController,
               context: this.getUIContext()
             });
           })
         // 用于业务的Web组件
         NodeContainer(this.businessNode);
       }
     }
   }
   ```

7. 加载的HTML网页示例。

   ```HTML
   <!DOCTYPE html>
   <html lang="en">
   <head></head>
   <body>
     <img src="https://www.example.com/path1/request.png" />
     <img src="https://www.example.com/path2/request.png" />
     <script src="https://www.example.com/example.js" crossorigin="anonymous"></script>
   </body>
   </html>
   ```
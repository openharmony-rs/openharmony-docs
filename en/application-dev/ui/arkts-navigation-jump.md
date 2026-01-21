# Page Routing
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @mayaolll-->
<!--Designer: @jiangdayuan-->
<!--Tester: @Giacinta-->
<!--Adviser: @Brilliantry_Rui-->

[Navigation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md)-related routing operations are all based on the APIs provided by the navigation controller [NavPathStack](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navpathstack10). For each **Navigation** component, a **NavPathStack** object must be created and passed to manage pages. **NavPathStack** mainly provides page navigation, page return, page replacement, page deletion, parameter acquisition, and route interception.

In API version 9, the **Navigation** component must be used together with the [NavRouter](../reference/apis-arkui/arkui-ts/ts-basic-components-navrouter.md) component for page routing. Since API version 10, **NavPathStack** is recommended for page routing.

Key concepts related to routing:

- Routing table: defines the mapping between page names and [NavDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md) pages. If the page name passed during redirection is not registered in the routing table, the redirection fails. The system provides two implementation modes: [system routing table](./arkts-navigation-cross-package.md#system-routing-table) and [custom routing table](./arkts-navigation-cross-package.md#custom-routing-table).
- Navigation stack: **NavDestination** pages are managed in a stack structure. Each **Navigation** has its own navigation stack, which cannot be shared. The navigation stack is controlled by **NavPathStack**. You can obtain the complete navigation stack information through [NavPathStack.getPathStack](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#getpathstack19).
- Page transition: **Navigation** provides the page transition animation by default. You can also customize the transition animation.

> **NOTE**
>
> - **NavPathStack** and **Navigation** must correspond to each other and cannot be reused.
>
> - **NavPathStack** mainly controls [NavDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md) page redirection and deletion. It cannot directly operate the [NavBar (navigation bar)](./arkts-navigation-architecture.md#navbar-navigation-bar). If you want to redirect to the **NavBar** page, you can only clear the navigation stack through [clear](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#clear10).
>
> - Avoid relying on lifecycle event listeners to manage the navigation stack. Instead, you can query the navigation stack through [NavPathStack.getPathStack](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#getpathstack19).
>
> - When the application is in the background, calling stack operation APIs of **NavPathStack** will trigger a refresh upon the application's return to the foreground.

## Creating a Navigation Page

### Creating a Navigation Root Container

You should first create a [Navigation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md) as the navigation root container and create a [NavPathStack](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navpathstack10) object as the input parameter for the **Navigation** component to bind them. Subsequent routing operations are performed based on the **NavPathStack**.

<!-- @[NavigationCreate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template2/Index.ets) -->

``` TypeScript
@Entry
@Component
struct Index {
  // Create a navigation controller object and pass it to the Navigation component.
  pageStack: NavPathStack = new NavPathStack();
  // ...
  build() {
    Navigation(this.pageStack) {
      // ...
    }.title('Main')
  }
}
```

### Building a Subpage

Declare the instantiation method for each [NavDestination] (../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md), for example, **PageOneBuilder** in the code. Executing this method creates a custom component of **PageOne**, which is a subpage of **Navigation**.

<!-- @[NavDestinationPrepare](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/NavigationExampleOne.ets) -->

``` TypeScript
@Builder
export function PageOneBuilder(name: string, param: string) {
  PageOne({ name: name, value: param });
}

@Component
export struct PageOne {
  navPathStack: NavPathStack = new NavPathStack();
  name: string = '';
  @State value: string = '';
  context = this.getUIContext().getHostContext();

  build() {
    NavDestination() {
      // ...
    }.title(`${this.name}`)
    // ...
  }
}
```

### Configuring a Routing Table

The system provides two route table implementation modes: system routing table and custom routing table. The former is used as an example. Register the instantiation method written on the subpage with its name (customized by you) in the routing table configuration file. The configuration file needs to be created in **entry/src/main/resources/base/profile/router_map.json**.

``` json
{
  "routerMap": [
    {
      "name": "basicPageOne", // Unique identifier of the route page
      "pageSourceFile": "src/main/ets/pages/PageOne.ets", // Path of the source code
      "buildFunction": "PageOneBuilder" // Name of the instantiation method of the page
    }
  ]
}
```

After creating a routing table, register it with the project by configuring **"routerMap": "$profile:router_map"** in the **module** field of the project configuration file [module.json5](../quick-start/module-configuration-file.md).

## Routing Operations

### Navigation Stack Acquisition

After the [Navigation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md) root container, subpages, and routing table are configured, you can call the [NavPathStack](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navpathstack10) API to switch between pages. As mentioned above, there is only one **NavPathStack** object in a **Navigation** container. To perform routing operations on a subpage, you need to obtain the **NavPathStack** object in either of the following ways:

 - Method 1: Use [AppStorage](../reference/apis-arkui/arkui-ts/ts-state-management.md#appstorage) to store and obtain the object.

    <!-- @[AppStorageSetStack](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/animation/NavigationPage.ets) -->
    
    ``` TypeScript
    @Entry
    @Component
    struct NavigationPage {
      navStack: NavPathStack = new NavPathStack();
    
      aboutToAppear(): void {
        AppStorage.setOrCreate<NavPathStack>('basicNavigationStack', this.navStack);
        // ...
      }
    
      build() {
        Navigation(this.navStack) {
          // ...
        }
      }
    }
    ```

    <!-- @[AppStorageGetStack](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/animation/BasicNavDestination.ets) -->
    
    ``` TypeScript
    @Builder
    export function BasicNavDestinationBuilder() {
      BasicNavDestination();
    }
    
    @Component
    struct BasicNavDestination {
      // Obtain the navigation controller in NavDestination.
      stack: NavPathStack = AppStorage.get<NavPathStack>('basicNavigationStack')!;
    
      build() {
        NavDestination() {
          // ...
        }
        .title('BasicNavDestination')
      }
    }
    ```

 - Method 2: Obtain the navigation controller in the [NavDestination.onReady](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onready11) lifecycle callback.

    <!-- @[NavDestinationGetStack](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/NavigationExampleOne.ets) -->
    
    ``` TypeScript
    @Builder
    export function PageOneBuilder(name: string, param: string) {
      PageOne({ name: name, value: param });
    }
    
    @Component
    export struct PageOne {
      navPathStack: NavPathStack = new NavPathStack();
      name: string = '';
      @State value: string = '';
      context = this.getUIContext().getHostContext();
    
      build() {
        NavDestination() {
          // ...
        }.title(`${this.name}`)
        .onReady((ctx: NavDestinationContext) => {
          // Obtain the navigation controller of the current page through NavDestinationContext.
          this.navPathStack = ctx.pathStack;
        })
      }
    }
    ```

### Basic Operations

Since API version 12, the navigation controller can be inherited. You can customize attributes and methods in derived classes or override methods of the parent class. Objects of the derived class can be used as [NavPathStack](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navpathstack10) objects of the base class. For details about the sample code for overriding **NavPathStack**, see [Defining a Derived Class of NavPathStack](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#example-10-defining-a-derived-class-of-navpathstack). The following describes the basic routing APIs provided by **NavPathStack**.

**Page navigation**

**NavPathStack** uses push-related APIs (such as [pushPath](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#pushpath10), [pushPathByName](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#pushpathbyname10), [pushDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#pushdestination11), and [pushDestinationByName](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#pushdestinationbyname11)) to implement page navigation. Page navigation can be classified into the following types:

1. Normal navigation: Navigation is conducted by page name and allows for carrying parameters.

      <!-- @[PushPathParam](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template2/Index.ets) -->
      
      ``` TypeScript
      this.pageStack.pushPath({ name: 'pageOne', param: 'PageOne Param' });
      ```
      <!-- @[PushPathByNameParam](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template2/PageOne.ets) --> 
      
      ``` TypeScript
      this.pageStack.pushPathByName('pageTwo', 'PageTwo Param');
      ```

2. Navigation with a return callback: An **onPop** callback is added during navigation to obtain return information and process it upon page popping.

      <!-- @[PushPathByNameOnPop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template4/PageOne.ets) -->
      
      ``` TypeScript
      let DOMAIN = 0x0000;
      this.pageInfo.pushPathByName('temp4-pageTwo', 'temp4-pageTwo Param', (popInfo) => {
        hilog.info(DOMAIN, 'testTag', 'Pop page name is: ', popInfo.info.name, 'result: ',
          JSON.stringify(popInfo.result));
        // ...
      });
      ```

3. Navigation with an error code: Upon failure, an asynchronous callback is triggered to provide the error code information.

      <!-- @[PushDestination](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template2/PageOne.ets) -->
      
      ``` TypeScript
      const DOMAIN = 0x0000;
      this.pageStack.pushDestination({
        name: 'pageTwo', param: 'PageTwo Param'}).catch((error: BusinessError) => {
        hilog.info(DOMAIN, 'testTag', '[pushDestination]failed', 'error code = ', error.code,
          'error.message = ', error.message);
      }).then(() => {
        hilog.info(DOMAIN, 'testTag', '[pushDestination]success.');
      });
      ```

      <!-- @[PushDestinationByName](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template2/PageOne.ets) -->
      
      ``` TypeScript
      const DOMAIN = 0x0000;
      this.pageStack.pushDestinationByName('pageTwo', 'PageTwo Param').catch((error: BusinessError) => {
        hilog.info(DOMAIN, 'testTag', '[pushDestinationByName]failed', 'error code = ', error.code,
          'error.message = ', error.message);
      }).then(() => {
        hilog.info(DOMAIN, 'testTag', '[pushDestinationByName]success.');
      });
      ```

**Page return**

**NavPathStack** implements the page return feature through [pop](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#pop11)-related APIs. Below shows the examples:

   <!-- @[pop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template2/PageTwo.ets) -->

   ``` TypeScript
   // Navigate back to the previous page.
   this.pathStack.pop();
   ```
   <!-- @[popToName](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template4/PageTwo.ets) -->

   ``` TypeScript
   // Navigate back to the previous pageOne page.
   this.pathStack.popToName('temp4-pageOne');
   ```

   <!-- @[popToIndex](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template4/PageTwo.ets) --> 

   ``` TypeScript
   // Navigate back to the page at index 0.
   this.pathStack.popToIndex(0);
   ```
   <!-- @[clear](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template2/PageOne.ets) -->

   ``` TypeScript
   // Navigate back to the root home page (clearing all pages in the stack).
   this.pageStack.clear();
   ```

**Page replacement**

**NavPathStack** provides replace-related APIs (such as [replacePath](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#replacepath11), [replacePathByName](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#replacepathbyname11), and [replaceDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#replacedestination18)) to implement the page replacement functionality.

   <!-- @[replacePath](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template2/PageOne.ets) -->

   ``` TypeScript
   // Replace the top page of the stack with pageTwo.
   this.pageStack.replacePath({ name: 'pageTwo', param: 'PageTwo Param' });
   this.pageStack.replacePathByName('pageTwo', 'PageTwo Param');
   ```

   <!-- @[replaceDestination](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template2/PageOne.ets) -->

   ``` TypeScript
   const DOMAIN = 0x0000;
   // Replacement with an error code: Upon failure, an asynchronous callback is triggered to provide the error code information.
   this.pageStack.replaceDestination({ name: 'pageTwo', param: 'PageTwo Param' })
     .catch((error: BusinessError) => {
       hilog.info(DOMAIN, 'testTag', '[replaceDestination]failed', 'error code = ', error.code,
         'error.message = ', error.message);
     }).then(() => {
     hilog.info(DOMAIN, 'testTag', '[replaceDestination]success.');
   })
   ```

**Page deletion**

**NavPathStack** uses the remove-related APIs (such as [removeByName](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#removebyname11), [removeByIndexes](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#removebyindexes11), and [removeByNavDestinationId](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#removebynavdestinationid12)) to delete a specific page from the navigation stack. Below shows the examples:

   <!-- @[removeByName](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template2/PageOne.ets) -->

   ``` TypeScript
   // Remove all pages whose name is pageTwo from the stack.
   this.pageStack.removeByName('pageTwo');
   ```
   <!-- @[removeByIndexes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template2/PageOne.ets) -->

   ``` TypeScript
   // Remove the page with the specified index.
   this.pageStack.removeByIndexes([1]);
   ```
   <!-- @[removeByNavDestinationId](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template2/PageOne.ets) -->

   ``` TypeScript
   // Remove the page with the specified ID.
   this.pageStack.removeByNavDestinationId('1');
   ```

**Page moving**

**NavPathStack** provides move-related APIs (such as [moveToTop](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#movetotop10) and [moveIndexToTop](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#moveindextotop10)) to move a specific page to the top of the navigation stack. Below shows the examples:

   <!-- @[moveToTop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template2/PageOne.ets) -->

   ``` TypeScript
   // Move the page named pageTwo to the top of the stack.
   this.pageStack.moveToTop('pageTwo');
   ```
   <!-- @[moveIndexToTop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template2/PageOne.ets) -->

   ``` TypeScript
   // Move the page at index 1 to the top of the stack.
   this.pageStack.moveIndexToTop(1);
   ```

### Singleton Navigation

Singleton navigation in the **Navigation** stack can be achieved by setting [LaunchMode](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#launchmode12) to **LaunchMode.MOVE_TO_TOP_SINGLETON** or **LaunchMode.POP_TO_SINGLETON**. The rules for singleton navigation are as follows:

1. If **LaunchMode.MOVE_TO_TOP_SINGLETON** is used, the system searches for the **NavDestination** with the specified name from the bottom to the top of the stack. Once found, the **NavDestination** page will be moved to the top of the stack (the replace operation will replace the current top of the stack with the specified **NavDestination**).
2. If **LaunchMode.POP_TO_SINGLETON** is used, the system similarly searches for the **NavDestination** with the specified name from the bottom to the top of the stack. Once it is found, all pages above this **NavDestination** will be removed (the replace operation will replace the current top of the stack with the specified **NavDestination**).

When an existing **NavDestination** page in the stack is moved to the top through singleton mode, the [onNewParam](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onnewparam19) callback is triggered.

For details about the sample code for singleton navigation, see [Using NavPathStack APIs](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#example-2-using-navpathstack-apis).

### Parameter Acquisition

The [onReady](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onready11) callback is triggered when a **NavDestination** page is first created, allowing you to obtain parameters associated with that page.

   <!-- @[onReady](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template7/PageOne.ets) -->

   ``` TypeScript
   @Component
   struct Page01 {
     pathStack: NavPathStack | undefined = undefined;
     // ...
     pageParam: string = '';
     build() {
       NavDestination() {
         // ...
       .title('Page01')
       .onReady((context: NavDestinationContext) => {
         this.pathStack = context.pathStack;
         this.pageParam = context.pathInfo.param as string;
       })
     }
   }
   ```

To receive parameters passed when navigating back, you can use the [onResult](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onresult15) API of the **NavDestination** component.

   <!-- @[onResult](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template2/PageOne.ets) -->

   ``` TypeScript
   class NavParam {
     desc: string = 'navigation-param'
   };
   const DOMAIN = 0x0000;
   // ...
   @Component
   export struct PageOne {
     // ...
     build() {
       NavDestination() {
         // ...
       }
       // ...
       .onResult((param: Object) => {
         if (param instanceof NavParam) {
           console.info('TestTag', 'get NavParam, its desc: ' + (param as NavParam).desc);
           return;
         }
         console.info('TestTag', 'param not instance of NavParam');;
       })
     }
   }
   ```

For other service scenarios, you can proactively call the getter APIs of **NavPathStack** (such as [getAllPathName](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#getallpathname10), [getParamByIndex](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#getparambyindex10), [getParamByName](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#getparambyname10), and [getIndexByName](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#getindexbyname10)) to obtain parameters from specific pages.

   <!-- @[GetParam](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template2/PageOne.ets) -->

   ``` TypeScript
   // Obtain all page names in the stack.
   this.pageStack.getAllPathName();
   // Obtain the parameters of the page whose index is 1.
   this.pageStack.getParamByIndex(1);
   // Obtain the parameters of the PageOne page.
   this.pageStack.getParamByName('PageOne');
   // Obtain the index set of the PageOne page.
   this.pageStack.getIndexByName('pageOne');
   ```


### Route Interception

**NavPathStack** provides the [setInterception](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#setinterception12) API to set callbacks for page navigation interception of **Navigation**. This API requires passing in a [NavigationInterception](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navigationinterception12) object, which contains multiple callback functions such as **willShow** and **didShow**. Different callback functions are invoked at different time. You can select an interception time based on the service requirements.

> **NOTE**
>
> - Regardless of which callback is invoked, the navigation stack has already changed when the callback is executed.
> - The **interception** callback is triggered earlier than the **willShow** callback, and the interception and redirection capabilities can be implemented. The difference is that the intercepted page is not created when the **interception** callback is triggered, but the intercepted page is created and then destroyed when the **willShow** callback is triggered.

Take the **willShow** callback as an example. You can modify the navigation stack in the callback to implement route interception and redirection.

   <!-- @[setInterception](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template2/Index.ets) -->

   ``` TypeScript
   const DOMAIN = 0x0000;
   this.pageStack.setInterception({
     willShow: (from: NavDestinationContext | 'navBar', to: NavDestinationContext | 'navBar',
       operation: NavigationOperation, animated: boolean) => {
       if (typeof to === 'string') {
         hilog.info(DOMAIN, 'testTag', 'target page is navigation home');
         return;
       }
       // Redirect navigation intended for PageTwo to PageOne.
       let target: NavDestinationContext = to as NavDestinationContext;
       if (target.pathInfo.name === 'pageTwo') {
         target.pathStack.pop();
         target.pathStack.pushPathByName('pageOne', null);
       }
     }
   })
   ```

## Examples

### Creating a Navigation Home Page

The implementation procedure is as follows:

1. Create a navigation home page using the **Navigation** component and create a navigation controller **NavPathStack** to enable transitions between pages.

2. Place a **List** component inside the **Navigation** component to display the first‑level pages available from the home page.

3. Attach an **onClick** event to each item in the **List**. Inside the event handler, call the **pushPathByName** method of the **NavPathStack** controller. When the item is clicked, this method navigates from the current page to the page whose name matches the specified parameter in the routing table.

<!-- @[NavigationDemo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/NavigationExample.ets) -->

``` TypeScript
@Entry
@Component
struct NavigationDemo {
  @Provide('navPathStack') navPathStack: NavPathStack = new NavPathStack();
  private listArray: Array<string> = ['WLAN', 'Bluetooth', 'Personal Hotspot', 'Connect & Share'];
  context = this.getUIContext().getHostContext();
  build() {
    Column() {
      Navigation(this.navPathStack) {
        // Replace $r('app.string.enterKeyWordsToSearch') with the actual resource file. In this example, the value in the resource file is "Search by keyword."
        TextInput({ placeholder: $r('app.string.enterKeyWordsToSearch') })
          .width('90%')
          .height(40)
          .margin({ bottom: 10 })

        // Define the level-1 navigation view through List.
        List({ space: 12, initialIndex: 0 }) {
          ForEach(this.listArray, (item: string) => {
            ListItem() {
              Row() {
                Row() {
                  Text(`${item.slice(0, 1)}`)
                    .fontColor(Color.White)
                    .fontSize(14)
                    .fontWeight(FontWeight.Bold)
                }
                .width(30)
                .height(30)
                .backgroundColor('#a8a8a8')
                .margin({ right: 20 })
                .borderRadius(20)
                .justifyContent(FlexAlign.Center)

                Column() {
                  Text(item)
                    .fontSize(16)
                    .margin({ bottom: 5 })
                }
                .alignItems(HorizontalAlign.Start)

                Blank()

                Row()
                  .width(12)
                  .height(12)
                  .margin({ right: 15 })
                  .border({
                    width: { top: 2, right: 2 },
                    color: 0xcccccc
                  })
                  .rotate({ angle: 45 })
              }
              .borderRadius(15)
              .shadow({ radius: 100, color: '#ededed' })
              .width('90%')
              .alignItems(VerticalAlign.Center)
              .padding({ left: 15, top: 15, bottom: 15 })
              .backgroundColor(Color.White)
            }
            .width('100%')
            .onClick(() => {
              // Replace $r('app.string.detailsPageParameters') with the string resource file you use. The value in the resource file is "Details page parameters."
              this.navPathStack.pushPathByName(`${item}`,
                // Push the navigation destination page specified by name, with the data specified by param, to the navigation stack.
                this.context!.resourceManager.getStringSync($r('app.string.detailsPageParameters').id));
            })
          }, (item: string): string => item)
        }
        .listDirection(Axis.Vertical)
        .edgeEffect(EdgeEffect.Spring)
        .sticky(StickyStyle.Header)
        .chainAnimation(false)
        .width('100%')
      }
      .width('100%')
      .mode(NavigationMode.Auto)
      // Replace $r('app.string.settings') with the string resource file you use. The value in the resource file is "Settings."
      .title($r('app.string.settings')) // Set the title.
    }
    .size({ width: '100%', height: '100%' })
    .backgroundColor(0xf4f4f5)
  }
}
```

### Creating a Navigation Subpage
Create navigation subpage 1 as follows:

1. Use **NavDestination** to create a navigation subpage (**PageOne**).

2. Create a navigation controller **NavPathStack** and initialize it in the **onReady** callback. This provides access to the current navigation controller for managing page transitions.

3. Add an **onClick** method to the components within the subpage and use the **pop** method of the **NavPathStack** to pop the top element of the stack and return to the previous page upon click.

<!-- @[NavigationExampleOne](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/NavigationExampleOne.ets) -->

``` TypeScript
@Builder
export function PageOneBuilder(name: string, param: string) {
  PageOne({ name: name, value: param });
}

@Component
export struct PageOne {
  navPathStack: NavPathStack = new NavPathStack();
  name: string = '';
  @State value: string = '';
  context = this.getUIContext().getHostContext();

  build() {
    NavDestination() {
      Column() {
        // Replace $r('app.string.settingPage') with the string resource file you use. The value in the resource file is "Settings page."
        Text(`${this.name}${this.context!.resourceManager.getStringSync($r('app.string.settingPage').id)}`)
          .width('100%')
          .fontSize(20)
          .fontColor(0x333333)
          .textAlign(TextAlign.Center)
          .textShadow({
            radius: 2,
            offsetX: 4,
            offsetY: 4,
            color: 0x909399
          })
          .padding({ top: 30 })
        Text(`${JSON.stringify(this.value)}`)
          .width('100%')
          .fontSize(18)
          .fontColor(0x666666)
          .textAlign(TextAlign.Center)
          .padding({ top: 45 })
        // Replace $r('app.string.return') with the string resource file you use. The value in the resource file is "Back."
        Button($r('app.string.return'))
          .width('50%')
          .height(40)
          .margin({ top: 50 })
          .onClick(() => {
            // Pop the top element of the navigation stack and return to the previous page.
            this.navPathStack.pop();
          })
      }
      .size({ width: '100%', height: '100%' })
    }.title(`${this.name}`)
    .onReady((ctx: NavDestinationContext) => {
      // Obtain the current navigation controller via NavDestinationContext.
      this.navPathStack = ctx.pathStack;
    })
  }
}
```

Create navigation subpage 2 as follows:

1. Use **NavDestination** to create a navigation subpage (**PageTwo**).

2. Create a navigation controller **NavPathStack** and initialize it in the **onReady** callback. This provides access to the current navigation controller for managing page transitions.

3. Attach an **onClick** event to each item in the subpage. Inside the event handler, call the **pushPathByName** method of the **NavPathStack** controller. When the item is clicked, this method navigates from the current page to the page whose name matches the specified parameter in the routing table.

<!-- @[NavigationExampleTwo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/NavigationExampleTwo.ets) -->

``` TypeScript
@Builder
export function PageTwoBuilder(name: string) {
  PageTwo({ name: name });
}

@Component
export struct PageTwo {
  navPathStack: NavPathStack = new NavPathStack();
  name: string = '';
  private listArray: Array<string> = ['Projection', 'Print', 'VPN', 'Private DNS', 'NFC'];
  context = this.getUIContext().getHostContext();
  build() {
    NavDestination() {
      Column() {
        List({ space: 12, initialIndex: 0 }) {
          ForEach(this.listArray, (item: string) => {
            ListItem() {
              Row() {
                Row() {
                  Text(`${item.slice(0, 1)}`)
                    .fontColor(Color.White)
                    .fontSize(14)
                    .fontWeight(FontWeight.Bold)
                }
                .width(30)
                .height(30)
                .backgroundColor('#a8a8a8')
                .margin({ right: 20 })
                .borderRadius(20)
                .justifyContent(FlexAlign.Center)

                Column() {
                  Text(item)
                    .fontSize(16)
                    .margin({ bottom: 5 })
                }
                .alignItems(HorizontalAlign.Start)

                Blank()

                Row()
                  .width(12)
                  .height(12)
                  .margin({ right: 15 })
                  .border({
                    width: { top: 2, right: 2 },
                    color: 0xcccccc
                  })
                  .rotate({ angle: 45 })
              }
              .borderRadius(15)
              .shadow({ radius: 100, color: '#ededed' })
              .width('90%')
              .alignItems(VerticalAlign.Center)
              .padding({ left: 15, top: 15, bottom: 15 })
              .backgroundColor(Color.White)
            }
            .width('100%')
            .onClick(() => {
              // Replace $r('app.string.pageSettingParam') with the string resource file you use. The value in the resource file is "Parameters."
              this.navPathStack.pushPathByName(`${item}`,
                this.context!.resourceManager.getStringSync($r('app.string.pageSettingParam').id));
            })
          }, (item: string): string => item)
        }
        .listDirection(Axis.Vertical)
        .edgeEffect(EdgeEffect.Spring)
        .sticky(StickyStyle.Header)
        .width('100%')
      }
      .size({ width: '100%', height: '100%' })
    }.title(`${this.name}`)
    .onReady((ctx: NavDestinationContext) => {
      // Obtain the current navigation controller via NavDestinationContext.
      this.navPathStack = ctx.pathStack;
    })
  }
}
```

### Creating a Routing Table

The implementation procedure is as follows:

1. Configure **{"routerMap": "$profile:router_map"}** in the project configuration file [module.json5](../quick-start/module-configuration-file.md).

2. In the **router_map.json** file, define the global routing table. The navigation controller **NavPathStack** can push the corresponding page information onto the stack based on the name in the routing table.

``` json
{
  "routerMap" : [
    {
      "name" : "WLAN",
      "pageSourceFile"  : "src/main/ets/pages/PageOne.ets",
      "buildFunction" : "PageOneBuilder"
    },
    {
      "name" : "Bluetooth",
      "pageSourceFile"  : "src/main/ets/pages/PageOne.ets",
      "buildFunction" : "PageOneBuilder"
    },
    {
      "name" : "Personal Hotspot",
      "pageSourceFile"  : "src/main/ets/pages/PageOne.ets",
      "buildFunction" : "PageOneBuilder"
    },
    {
      "name" : "Connect & Share",
      "pageSourceFile"  : "src/main/ets/pages/PageTwo.ets",
      "buildFunction" : "PageTwoBuilder"
    },
    {
      "name" : "Projection",
      "pageSourceFile"  : "src/main/ets/pages/PageOne.ets",
      "buildFunction" : "PageOneBuilder"
    },
    {
      "name" : "Print",
      "pageSourceFile"  : "src/main/ets/pages/PageOne.ets",
      "buildFunction" : "PageOneBuilder"
    },
    {
      "name" : "VPN",
      "pageSourceFile"  : "src/main/ets/pages/PageOne.ets",
      "buildFunction" : "PageOneBuilder"
    },
    {
      "name" : "Private DNS",
      "pageSourceFile"  : "src/main/ets/pages/PageOne.ets",
      "buildFunction" : "PageOneBuilder"
    },
    {
      "name" : "NFC",
      "pageSourceFile"  : "src/main/ets/pages/PageOne.ets",
      "buildFunction" : "PageOneBuilder"
    }
  ]
}
```

![en-us_image_0000001588458252](figures/arkts-navigation-transition_1.gif)

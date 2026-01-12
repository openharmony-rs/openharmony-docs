# Component Navigation (Navigation) (Recommended)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @mayaolll-->
<!--Designer: @jiangdayuan-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

Component navigation, implemented using the [Navigation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md) component, is instrumental for managing transitions between navigation pages ([NavDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md) components). It allows for the passing of parameters across various navigation pages and offers flexible navigation stack operations to simplify access to and reuse of pages. This documentation delves into the display modes, routing operations, subpage management, cross-package navigation, and navigation transition effects.

The [Navigation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md) component serves as the root view container for route navigation and is commonly used as the root container for pages decorated with @Entry. It supports three display modes: Stack, Split, and Auto. This component is designed for both intra-module and cross-module routing, leveraging component-level routing to provide a more natural and seamless transition between pages. It also offers multiple title bar styles to enhance the interaction between titles and content. As for one-time development for multi-device deployment, the **Navigation** component can automatically adapt to window sizes, automatically switching to split-column mode for large windows.

The **Navigation** component consists of a navigation page and subpages. The navigation page consists of the title bar (with the menu bar), content area, and toolbar, and can be hidden through the [hideNavBar](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#hidenavbar9) attribute. The navigation page does not reside in the [navigation stack](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navpathstack10). Routing is used to manage transitions between the navigation page and its subpages, as well as between subpages themselves.

In API version 9, the **Navigation** component must be used together with the [NavRouter](../reference/apis-arkui/arkui-ts/ts-basic-components-navrouter.md) component for page routing. Since API version 10, whenever possible, use [NavPathStack](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navpathstack10) instead to implement page routing.


## Setting the Page Display Mode

The [Navigation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md) component uses the [mode](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#mode9) attribute to set the page display mode.

- Adaptive mode

  By default, the **Navigation** component is in adaptive mode, where the **mode** attribute is **NavigationMode.Auto**. In adaptive mode, when the device width is greater than or equal to the threshold (520 vp for API version 9 and earlier and 600 vp for API version 10 and later), the **Navigation** component uses the split-column mode. Otherwise, the **Navigation** component uses the single-column mode.


  <!-- @[NavigationModeAuto](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/PageDisplayModeAuto.ets) -->
  
  ``` TypeScript
  Navigation() {
    // ···
  }
  .mode(NavigationMode.Auto)
  ```

- Single-column mode

  The single-column mode is designed for narrow-screen devices. When route navigation occurs, the entire page content is replaced.

    **Figure 1** Single-column mode 

  ![en-us_image_0000001511740532](figures/en-us_image_0000001511740532.png)

  To configure the **Navigation** component to single-column mode, set **mode** to **NavigationMode.Stack**.

  <!-- @[NavigationModeStack](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/PageDisplayModeStack.ets) -->
  
  ``` TypeScript
  Navigation() {
    // ···
  }
  .mode(NavigationMode.Stack)
  ```

  ![Navigation in stack mode](figures/navigation-mode-stack.jpg)

- Split-column mode

  The split-column mode is suitable for wide-screen devices. It is divided into left and right sections. During route navigation, only the right subpage is replaced.

  **Figure 2** Split-column mode

  ![en-us_image_0000001562820845](figures/en-us_image_0000001562820845.png)

  To configure the **Navigation** component for split-column display mode, set **mode** to **NavigationMode.Split**.


  <!-- @[NavigationModeSplit](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/PageDisplayModeSplit.ets) -->
  
  ``` TypeScript
  import { hilog } from '@kit.PerformanceAnalysisKit';
  const DOMAIN = 0x0000;
  @Entry
  @Component
  struct PageDisplayModeSplit {
    @State toolTmp: ToolbarItem = {
      'value': 'func',
      'icon': 'ets/pages/navigation/template1/image/ic_public_highlights.svg',  // Icon resource from the image folder in the current directory.
      'action': () => {}
    };
    @Provide('navPathStack') navPathStack: NavPathStack = new NavPathStack();
    private arr: number[] = [1, 2, 3];
  
    @Builder
    pageMap(name: string) {
      if (name === 'NavDestinationTitle1') {
        pageOneTmp();
      } else if (name === 'NavDestinationTitle2') {
        pageTwoTmp();
      } else if (name === 'NavDestinationTitle3') {
        pageThreeTmp();
      }
    }
  
    build() {
      Column() {
        Navigation(this.navPathStack) {
          TextInput({ placeholder: 'Search...' })
            .width('90%')
            .height(40)
            .backgroundColor('#FFFFFF')
  
          List({ space: 12 }) {
            ForEach(this.arr, (item: number) => {
              ListItem() {
                Text('Page' + item)
                  .width('100%')
                  .height(72)
                  .backgroundColor('#FFFFFF')
                  .borderRadius(24)
                  .fontSize(16)
                  .fontWeight(500)
                  .textAlign(TextAlign.Center)
                  .onClick(() => {
                    this.navPathStack.pushPath({ name: 'NavDestinationTitle' + item });
                  })
              }
            }, (item: number) => item.toString())
          }
          .width('90%')
          .margin({ top: 12 })
        }
        // Replace $r('app.string.mainTitle') with the string resource file you use.
        .title($r('app.string.mainTitle'))
        .mode(NavigationMode.Split)
        .navDestination(this.pageMap)
        .menus([
          {
            value: '', icon: 'resources/base/media/ic_public_search.svg', action: () => {
          }
          },
          {
            value: '', icon: 'resources/base/media/ic_public_add.svg', action: () => {
          }
          },
          {
            value: '', icon: 'resources/base/media/ic_public_search.svg', action: () => {
          }
          },
          {
            value: '', icon: 'resources/base/media/ic_public_search.svg', action: () => {
          }
          },
          {
            value: '', icon: 'resources/base/media/ic_public_search.svg', action: () => {
          }
          }
        ])
        .toolbarConfiguration([this.toolTmp, this.toolTmp, this.toolTmp])
      }
      .height('100%')
      .width('100%')
      .backgroundColor('#F1F3F5')
    }
  }
  
  @Component
  export struct pageOneTmp {
    @Consume('navPathStack') navPathStack: NavPathStack;
    context = this.getUIContext().getHostContext();
    build() {
      NavDestination() {
        Column() {
          Text('NavDestinationContent1')
        }.width('100%').height('100%')
      }.title('NavDestinationTitle1')
      .onBackPressed(() => {
        const popDestinationInfo = this.navPathStack.pop(); // Pop the top element out of the navigation stack.
        // The value in the $r('app.string.returnValue') resource file is "Return value."
        hilog.info(DOMAIN, 'testTag', 'pop', this.context!.resourceManager.getStringSync($r('app.string.returnValue').id),
          JSON.stringify(popDestinationInfo));
        return true;
      })
    }
  }
  
  @Component
  export struct pageTwoTmp {
    @Consume('navPathStack') navPathStack: NavPathStack;
    context = this.getUIContext().getHostContext();
    build() {
      NavDestination() {
        Column() {
          Text('NavDestinationContent2')
        }.width('100%').height('100%')
      }.title('NavDestinationTitle2')
      .onBackPressed(() => {
        const popDestinationInfo = this.navPathStack.pop(); // Pop the top element out of the navigation stack.
        // The value in the $r('app.string.returnValue') resource file is "Return value."
        hilog.info(DOMAIN, 'testTag', 'pop', this.context!.resourceManager.getStringSync($r('app.string.returnValue').id),
          JSON.stringify(popDestinationInfo));
        return true;
      })
    }
  }
  
  @Component
  export struct pageThreeTmp {
    @Consume('navPathStack') navPathStack: NavPathStack;
    context = this.getUIContext().getHostContext();
    build() {
      NavDestination() {
        Column() {
          Text('NavDestinationContent3')
        }.width('100%').height('100%')
      }.title('NavDestinationTitle3')
      .onBackPressed(() => {
        const popDestinationInfo = this.navPathStack.pop(); // Pop the top element out of the navigation stack.
        // The value in the $r('app.string.returnValue') resource file is "Return value."
        hilog.info(DOMAIN, 'testTag', 'pop', this.context!.resourceManager.getStringSync($r('app.string.returnValue').id),
          JSON.stringify(popDestinationInfo));
        return true;
      })
    }
  }
  ```

  ![Navigation in split mode](figures/navigation-mode-split.jpg)


## Setting the Title Bar Mode

Located on the top of the page, the title bar displays the page name and operation entry. The **Navigation** component uses the [titleMode](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#titlemode) attribute to set the title bar mode.

> **NOTE**
> If no main title or subtitle is set for **Navigation** or **NavDestination** and there is no back button, the title bar is not displayed.

- Mini mode

  Applicable when the title of a level-1 page does not need to be highlighted.

  **Figure 3** Title bar in Mini mode 

  ![mini](figures/mini.jpg)


  <!-- @[NavigationTitleModeMini](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/TitleModeMini.ets) -->
  
  ``` TypeScript
  Navigation() {
    // ···
  }
  .titleMode(NavigationTitleMode.Mini)
  ```

- Full mode

  Applicable when the title of a level-1 page needs to be highlighted.

    **Figure 4** Title bar in Full mode 

  ![free1](figures/free1.jpg)


  <!-- @[NavigationTitleModeFUll](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/TitleModeFull.ets) -->
  
  ``` TypeScript
  Navigation() {
    // ···
  }
  .titleMode(NavigationTitleMode.Full)
  ```

## Setting the Menu Bar

The menu bar is in the upper right corner of the **Navigation** component. You can set the menu bar through the [menus](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#menus) attribute, which supports two parameter types: Array&lt;[NavigationMenuItem](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navigationmenuitem)&gt; and [CustomBuilder](../reference/apis-arkui/arkui-ts/ts-types.md#custombuilder8). When the Array\<NavigationMenuItem> type is used, a maximum of three icons can be displayed in portrait mode and a maximum of five icons can be displayed in landscape mode. Extra icons will be placed in the automatically generated More icons.

**Figure 5** Menu bar with three icons 

![menu-bar-2](figures/menu-bar-2.jpg)

   <!-- @[NavigationMenuThreeImage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/MenusThreeImage.ets) -->
   
   ``` TypeScript
   let toolTmp: NavigationMenuItem  = {
     'value': 'func',
     'icon': 'ets/pages/navigation/template1/image/ic_public_add.svg',
     'action': () => {}
   };
   // ...
         Navigation(this.navPathStack) {
           // ...
         }
         .menus([toolTmp, toolTmp, toolTmp])
   ```

You can also reference images in the **resources** folder.

   <!-- @[NavigationMenuThreeResource](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/MenusThreeResource.ets) -->
   
   ``` TypeScript
   let toolTmp: NavigationMenuItem  = {
     'value': 'func',
     'icon': 'resources/base/media/ic_public_add.svg',
     'action': () => {}
   };
   // ...
         Navigation(this.navPathStack) {
           // ...
         }
         .menus([toolTmp, toolTmp, toolTmp])
   ```

**Figure 6** Menu bar with four icons 

![menu-bar](figures/menu-bar.jpg)

   <!-- @[NavigationMenuFour](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/MenusFour.ets) -->
   
   ``` TypeScript
   let toolTmp: NavigationMenuItem  = {
     'value': 'func',
     'icon': 'ets/pages/navigation/template1/image/ic_public_add.svg',
     'action': () => {}
   };
   // ...
         Navigation(this.navPathStack) {
           // ...
         }
         // In portrait mode, the toolbar shows a maximum of three icons, with any additional icons placed under an automatically generated More icon.
         .menus([toolTmp, toolTmp, toolTmp, toolTmp])
   ```

## Setting the Toolbar

Use the [toolbarConfiguration](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#toolbarconfiguration10) attribute to customize the toolbar, which is located at the bottom of the **Navigation** component.


  **Figure 7** Toolbar 

![free3](figures/free3.jpg)

   <!-- @[ToolBar](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/ToolBar.ets) -->
   
   ``` TypeScript
   let toolTmp: ToolbarItem = {
     'value': 'func',
     'icon': 'ets/pages/navigation/template1/image/ic_public_highlights.svg',
     'action': () => {}
   };
   let tooBar: ToolbarItem[] = [toolTmp,toolTmp,toolTmp];
   // ...
         Navigation(this.navPathStack) {
           // ...
         }
         .toolbarConfiguration(tooBar)
   ```

## Routing Operations

Navigation-related routing operations are all based on the APIs provided by the navigation controller [NavPathStack](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navpathstack10). For each **Navigation** component, a **NavPathStack** object must be created and passed in to manage pages. The router operations mainly involve page navigation, page return, page replacement, page deletion, parameter acquisition, and route interception.

Since API version 12, the navigation controller can be inherited. You can customize attributes and methods in derived classes or override methods of the parent class. Derived class objects can be used in place of the base class **NavPathStack** objects. [NavDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navdestination10) pages within **Navigation** are managed in a stack structure within **NavPathStack**, referred to as the navigation stack. For details about the sample code, see [Example 10: Defining a Derived Class of NavPathStack](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#example-10-defining-a-derived-class-of-navpathstack).

> **NOTE**
>
> 1. Avoid relying on lifecycle event listeners as a means to manage the navigation stack.
>
> 2. When the application is in the background, calling stack operation APIs of **NavPathStack** will trigger a refresh upon the application's return to the foreground.

   <!-- @[NavigationCreate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template2/Index.ets) -->
   
   ``` TypeScript
   @Entry
   @Component
   struct Index {
     //Create a navigation controller object and pass it to the Navigation component.
     pageStack: NavPathStack = new NavPathStack();
   // ···
     build() {
       Navigation(this.pageStack) {
       // ···
       }.title('Main')
     }
   }
   ```


### Page Navigation

**NavPathStack** uses push-related APIs (such as [pushPath](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#pushpath10), [pushPathByName](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#pushpathbyname10), [pushDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#pushdestination11), and [pushDestinationByName](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#pushdestinationbyname11)) to implement page redirection. Page redirection can be classified into the following types:

1. Normal navigation: Navigation is conducted by page name and allows for passing of **param**.

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
      // ···
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


### Page Return

**NavPathStack** implements the page return feature through pop-related APIs, including [pop](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#pop10), [popToName](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#poptoname10), [popToIndex](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#poptoindex10), and [clear](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#clear10).

   <!-- @[pop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template2/PageTwo.ets) -->
   
   ``` TypeScript
   // Return to the previous page.
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
   // Return to the root home page (clear all pages in the stack).
   this.pageStack.clear();
   ```

### Page Replacement

NavPathStack provides replace-related APIs (such as [replacePath](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#replacepath11), [replacePathByName](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#replacepathbyname11), and [replaceDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#replacedestination18)) to implement the page replacement functionality.

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

### Page Deletion

NavPathStack uses the Remove APIs (such as [removeByName](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#removebyname11), [removeByIndexes](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#removebyindexes11) and [removeByNavDestinationId](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#removebynavdestinationid12)) to delete a specific page from the navigation stack.

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

### Page Moving

**NavPathStack** provides move-related APIs (such as [moveToTop](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#movetotop10) and [moveIndexToTop](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#moveindextotop10)) to move a specific page to the top of the navigation stack.

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

### Parameter Acquisition

The [onReady](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onready11) callback is triggered when a [NavDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md) page is first created, allowing you to obtain parameters associated with that page.

   <!-- @[onReady](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template7/PageOne.ets) -->
   
   ``` TypeScript
   @Component
   struct Page01 {
     pathStack: NavPathStack | undefined = undefined;
   // ···
     pageParam: string = '';
     build() {
       NavDestination() {
       // ···
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
   // ···
   @Component
   export struct PageOne {
   // ···
     build() {
       NavDestination() {
       // ···
       }
       // ···
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

**NavPathStack** provides the [setInterception](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#setinterception12) API to set callbacks for page navigation interception of **Navigation**. This API requires passing in a [NavigationInterception](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navigationinterception12) object, which contains three callback functions described below.

| Name      | Description                                                |
| ------------ | ------------------------------------------------------ |
| willShow   | Callback invoked before a page transition, allowing for stack operations, which take effect immediately for the current transition.      |
| didShow    | Callback invoked after a page transition. Stack operations in this callback take effect on the next transition.|
| modeChange | Callback invoked when the display mode of the **Navigation** component switches between single-column and split-column. |

> **NOTE**
>
> Regardless of which callback is invoked, the navigation stack has already changed when the callback is executed.

You can implement route interception and redirection capabilities by modifying the navigation stack within the **willShow** callback.

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


### Singleton Navigation

Singleton navigation in the **Navigation** stack can be achieved by setting [LaunchMode](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#launchmode12) to **LaunchMode.MOVE_TO_TOP_SINGLETON** or **LaunchMode.POP_TO_SINGLETON**. The rules for singleton navigation are as follows:

1. When **LaunchMode.MOVE_TO_TOP_SINGLETON** is used, the system searches for the **NavDestination** with the specified name from the bottom to the top of the stack. Once found, the **NavDestination** page will be moved to the top of the stack (the replace operation will replace the current top of the stack with the specified **NavDestination**).
2. When **LaunchMode.POP_TO_SINGLETON** is used, the system similarly searches for the **NavDestination** with the specified name from the bottom to the top of the stack. Once it is found, all pages above this **NavDestination** will be removed (the replace operation will replace the current top of the stack with the specified **NavDestination**).

When an existing **NavDestination** page in the stack is moved to the top through singleton mode, the [onNewParam](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onnewparam19) callback is triggered.

For sample code related to singleton navigation, see [Example 2: Using NavPathStack APIs](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#example-2-using-navpathstack-apis).

## Subpage

[NavDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md) is the root container for [Navigation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md) subpages, used to hold some special attributes as well as lifecycles of subpages. You can set separate attributes such as the title bar and menu bar for **NavDestination**, in the same way you set attributes for **Navigation**. You can also set different display modes for **NavDestination** through the [mode](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#mode11) attribute to meet different page requirements.

### Page Display Mode

- Standard mode

  By default, subpages in the **NavDestination** component are in standard mode, which corresponds to the **NavDestinationMode.STANDARD** value of the **mode** attribute. The lifecycle of a **NavDestination** in standard mode follows the changes in its position in the **NavPathStack** navigation stack.

- Dialog mode
  
  With **mode** set to **NavDestinationMode.DIALOG**, a **NavDestination** is displayed transparently by default. The appearance and disappearance of the **NavDestination** in dialog mode do not affect the display and lifecycle of the underlying **NavDestination** in standard mode, and both can be displayed at the same time.

  <!-- @[PageDisplayType](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/PageDisplayType.ets) -->
  
  ``` TypeScript
  // Dialog NavDestination
  @Entry
  @Component
  struct PageDisplayType {
    @Provide('NavPathStack') pageStack: NavPathStack = new NavPathStack();
  
    @Builder
    PagesMap(name: string) {
      if (name == 'DialogPage') {
        DialogPage();
      }
    }
  
    build() {
      Navigation(this.pageStack) {
        Button('Push DialogPage')
          .margin(20)
          .width('80%')
          .onClick(() => {
            this.pageStack.pushPathByName('DialogPage', '');
          })
      }
      .mode(NavigationMode.Stack)
      .title('Main')
      .navDestination(this.PagesMap)
    }
  }
  
  @Component
  export struct DialogPage {
    @Consume('NavPathStack') pageStack: NavPathStack;
  
    build() {
      NavDestination() {
        Stack({ alignContent: Alignment.Center }) {
          Column() {
            Text('Dialog NavDestination')
              .fontSize(20)
              .margin({ bottom: 100 })
            Button('Close').onClick(() => {
              this.pageStack.pop();
            }).width('30%')
          }
          .justifyContent(FlexAlign.Center)
          .backgroundColor(Color.White)
          .borderRadius(10)
          .height('30%')
          .width('80%')
        }.height('100%').width('100%')
      }
      .backgroundColor('rgba(0,0,0,0.5)')
      .hideTitleBar(true)
      .mode(NavDestinationMode.DIALOG)
    }
  }
  ```

  ![dialog_navdestination](figures/dialog_navdestination.png)

### Page Lifecycle

**Navigation**, as a routing container, hosts its lifecycle within the **NavDestination** component and exposes lifecycle events as component events.

The lifecycle of **Navigation** can be divided into three categories: custom component lifecycle, universal component lifecycle, and its own exclusive lifecycle. [aboutToAppear](../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoappear) and [aboutToDisappear](../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttodisappear) are the lifecycle callbacks of custom components (custom components contained in the outer layer of **NavDestination**); [OnAppear](../reference/apis-arkui/arkui-ts/ts-universal-events-show-hide.md#onappear) and [OnDisappear](../reference/apis-arkui/arkui-ts/ts-universal-events-show-hide.md#ondisappear) are universal component lifecycle callbacks. The remaining lifecycle events are unique to **NavDestination**.

The sequence of these lifecycle events is illustrated in the figure below.

![navigation_lifecycle](figures/navigation_lifecycle.png)

- **aboutToAppear**: Invoked when the custom component is about to appear. Specifically, it is invoked after a new instance of the custom component is created and before its **build()** function is executed (before the creation of **NavDestination**). You can change state variables in this callback, and the changes take effect in the subsequent execution of **build()**.
- **onWillAppear**: invoked after the **NavDestination** component is created and before it is mounted to the component tree. Changing the state variable in this callback takes effect in the current frame.
- **onAppear**: invoked when the **NavDestination** component is mounted to the component tree. It is a universal lifecycle event.
- **onWillShow**: invoked before the **NavDestination** component layout is displayed. In this case, the page is invisible. (This callback is not invoked when the application is switched to the foreground.)
- **onShown**: invoked after the **NavDestination** component layout is displayed. At this time, the page layout is complete.
- **onActive**: invoked when the **NavDestination** component becomes active (on top of the stack and operable, with no special components blocking it).
- **onWillHide**: invoked when the **NavDestination** component is about to be hidden (it is not invoked when the application is switched to the background).
- **onInactive**: invoked when the **NavDestination** component becomes inactive (not on top of the stack and inoperable, or on top but blocked by special components).
- **onHidden**: invoked after the **NavDestination** component is hidden (when a non-top page is pushed into the stack, the top page pops out of the stack, or the application is switched to the background).
- **onWillDisappear**: invoked before the **NavDestination** component is about to be destroyed. If there is a transition animation, this callback is invoked before the animation (when the top page of the stack pops out of the stack).
- **onDisappear**: invoked when the **NavDestination** component is unloaded and destroyed from the component tree. It is a universal lifecycle event.
- **aboutToDisappear**: invoked before the custom component is destroyed. The state variable cannot be changed in this callback.

### Page Listening and Query

To facilitate the decoupling of components from pages, custom components within **NavDestination** subpages can listen for or query some page status information through global APIs.

- Page information query

  Custom components provide the [queryNavDestinationInfo](../reference/apis-arkui/arkui-ts/ts-custom-component-api.md#querynavdestinationinfo) API, which can be used to query the information of the current page within **NavDestination**. The return value is [NavDestinationInfo](../reference/apis-arkui/js-apis-arkui-observer.md#navdestinationinfo). If the query fails, the return value is **undefined**.

  <!-- @[MyComponent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/observer/template1/Index.ets) -->
  
  ``` TypeScript
  import { uiObserver } from '@kit.ArkUI';
  
  // Custom components within NavDestination
  @Component
  struct MyComponent {
    navDesInfo: uiObserver.NavDestinationInfo | undefined;
    context = this.getUIContext().getHostContext();
  
    aboutToAppear() {
      this.navDesInfo = this.queryNavDestinationInfo();
    }
  
    build() {
      // ···
        Column() {
          // Replace r('app.string.onPageName') with the string resource file you use.
          Text(this.context!.resourceManager.getStringSync($r('app.string.onPageName').id) + `${this.navDesInfo?.name}`)
        }.width('100%').height('100%')
      // ···
    }
  }
  ```

- Page status listening
  
  You can register a listener for **NavDestination** lifecycle changes using the [observer.on('navDestinationUpdate')](../reference/apis-arkui/js-apis-arkui-observer.md#uiobserveronnavdestinationupdate) API.
  
  <!-- @[uiObserver](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/observer/template2/Index.ets) -->
  
  ``` TypeScript
  const DOMAIN = 0x0000;
  uiObserver.on('navDestinationUpdate', (info) => {
    hilog.info(DOMAIN, 'testTag', 'NavDestination state update', JSON.stringify(info));
  });
  ```

  
  You can also register a callback for page transition states to obtain page information during route changes using [NavDestinationSwitchInfo](../reference/apis-arkui/js-apis-arkui-observer.md#navdestinationswitchinfo12). This registration supports different scopes: UIAbilityContext and UIContext.
  
  <!-- @[callbackFunc](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/observer/template3/Index.ets) -->
  
  ``` TypeScript
  // Used in UIAbility
  import { UIContext, uiObserver } from '@kit.ArkUI';
  
  // callbackFunc is a callback defined by you.
  function callBackFunc(info: uiObserver.NavDestinationSwitchInfo) {
  // ···
  };
  // ···
      uiObserver.on('navDestinationSwitch', this.context, callBackFunc);
      // ···
  
  // ···
    // The getUIContext() API of the window can be used to obtain the corresponding UIContent.
    uiContext: UIContext | null = null;
  // ···
      uiObserver.on('navDestinationSwitch', this.uiContext, callBackFunc);
      // ···
  ```

## Page Transition

The [Navigation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md) component provides default transition animations. These animations are activated when operations are performed using the navigation controller, producing different transition effects. Note that for pages in dialog mode, the default transition animations are available only since API version 13. The **Navigation** component also offers advanced features such as disabling the default transitions and implementing custom transitions as well as shared element transitions. The default animation duration is determined by physical curve parameters and varies across different devices.

### Disabling Transitions

- On a Global Basis
  
  To enable or disable all transition animations in the current **Navigation** component, you can use the [disableAnimation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#disableanimation11) API provided in **NavPathStack**.

  <!-- @[PageAnimated](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/PageAnimated.ets) -->
  
  ``` TypeScript
  pageStack: NavPathStack = new NavPathStack();
  
  aboutToAppear(): void {
    this.pageStack.disableAnimation(true);
  }
  ```

- On a One-Time Basis
  
  To disable the transition animation for a single operation (implemented by APIs provided by **NavPathStack**, such as **Push**, **Pop**, and **Replace**), set the **animated** parameter in the API to **false**. This setting does not affect the next transition.

  <!-- @[PageOnceClose](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/PageOnceClose.ets) -->
  
  ``` TypeScript
  @Provide('pageStack') pageStack: NavPathStack = new NavPathStack();
  ```
  <!-- @[PageOnceCloseOne](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/PageOnceClose.ets) -->
  
  ``` TypeScript
  this.pageStack.pushPath({ name: 'MyComponent' }, false);
  ```
  <!-- @[PageOnceCloseTwo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/PageOnceClose.ets) -->
  
  ``` TypeScript
  this.pageStack.pop(false);
  ```

### Defining a Custom Transition

- Custom Transition for Navigation

  Use the [customNavContentTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#customnavcontenttransition11) event to define a transition that applies to all pages within the **Navigation** component.

  1. Build a custom transition animation utility class **CustomNavigationUtils** to manage custom animation objects **CustomTransition** for each page via a **Map**. A page registers its custom transition animation object when created and unregisters it when destroyed.
  2. Implement a transition protocol object [NavigationAnimatedTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navigationanimatedtransition11). The **timeout** property indicates the timeout for transition completion, with a default value of 1000 ms, and the **transition** property is the custom transition animation API. You need to implement your own transition animation logic here; the system will call this API when the transition starts, and **onTransitionEnd** is the callback when the transition ends.
  3. Call the **customNavContentTransition** API and return the implemented transition protocol object. If **undefined** is returned, the system default transition will be used.

  For details about the sample code, see [Example 3: Setting an Interactive Transition Animation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#example-3-setting-an-interactive-transition-animation).

- Custom Transition for NavDestination

  Use the [customTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#customtransition15) attribute to define a transition specific to a particular [NavDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md) page. To achieve this, follow these steps:

  1. Implement the [transition delegate for NavDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#navdestinationtransitiondelegate15), returning custom transition protocol objects [NavDestinationTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#navdestinationtransition15) for different stack operation types. **event** is a required parameter where the logic for custom transition animations should be written; **onTransitionEnd**, **duration**, **curve**, and **delay** are optional parameters corresponding to the callback after animation completion, animation duration, animation curve type, and delay before start, respectively. If multiple transition protocol objects are returned in the transition delegate, these animation effects will be applied incrementally.
  2. Complete the custom transition setup by calling the **customTransition** property of the **NavDestination** component and passing in the implemented transition delegate.

  For details about the sample code, see [Example 2: Setting a Custom Transitions for the NavDestination Component](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#example-2-setting-a-custom-transitions-for-the-navdestination-component).

- Suggestions
  1. [customNavContentTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#customnavcontenttransition11) controls all pages within the **Navigation** component and provides unified transition animation effects.
  2. [customTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#customtransition15) controls the transition effect for individual pages.
  3. When both [customNavContentTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#customnavcontenttransition11) and [customTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#customtransition15) are used, **customNavContentTransition** takes precedence.

### Defining a Shared Element Transition

You can implement shared element transitions between navigation destination pages using [geometryTransition](../reference/apis-arkui/arkui-ts/ts-transition-animation-geometrytransition.md#geometrytransition). Ensure that the default transition animations are disabled for pages configured with shared element transitions.
1. Add the **geometryTransition** attribute to the components that need to implement shared element transitions, ensuring that the **id** parameter is consistent between the two **NavDestination** components.

   <!-- @[GeometryTransitionFromPage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/GeometryTransition.ets) -->
   
   ``` TypeScript
   // Set id of the source page.
   NavDestination() {
     Column() {
       // ···
       // Replace $r('app.media.startIcon') with the resource file you use.
       Image($r('app.media.startIcon'))
         .geometryTransition('sharedId')
         .width(100)
         .height(100)
     }
   }.title('FromPage')
   ```

   <!-- @[GeometryTransitionToPage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/GeometryTransition.ets) -->
   
   ``` TypeScript
   // Set id of the destination page.
   NavDestination() {
     Column() {
       // Replace $r('app.media.startIcon') with the resource file you use.
       Image($r('app.media.startIcon'))
         .geometryTransition('sharedId')
         .width(200)
         .height(200)
     }
   }
   .title('ToPage')
   ```

2. Place the page routing operation in the **animateTo** animation closure, set the corresponding animation parameters, and disable the default transition.

   <!-- @[GeometryTransitionFromPageOne](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/GeometryTransition.ets) -->
   
   ``` TypeScript
   NavDestination() {
     Column() {
       // Replace $r('app.string.ToPage') with the string resource file you use.
       Button($r('app.string.ToPage'))
         .width('80%')
         .height(40)
         .margin(20)
         .onClick(() => {
           this.getUIContext()?.animateTo({ duration: 1000 }, () => {
             this.navPathStack.pushPath({ name: 'ToPage' }, false)
           });
         })
       // ···
     }
   }.title('FromPage')
   ```

## Cross-Package Routing

The system provides two implementation modes: [system routing table](#system-routing-table) and [custom routing table](#custom-routing-table).

- The system routing table is easier to use than the custom routing table. It only requires adding the corresponding page navigation configuration items to implement page navigation.

- The custom route table is more complex to use, but can be customized to meet specific service requirements.

The custom route table and system route table can be used together.

### Routing Table Capability Comparison

Different routing modes meet different requirements. Usability and scalability should be balanced based on project characteristics.

| Routing Mode    | Cross-Package Redirection Capability            | Scalability    | Usability                              |
| ------------ | ------------------------ | ------------ | ------------------------------------ |
| [System routing table](#system-routing-table)  | No need to import page files before redirection; pages are dynamically loaded on demand| Moderate| High; the system automatically maintains the routing table      |
| [Custom routing table](#custom-routing-table)| Page files must be imported before redirection| High| Moderate; you must maintain the routing table manually|

### System Routing Table

The system routing table is an implementation of dynamic routing. [Navigation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md) supports the system routing table for dynamic routing since API version 12. Each service module ([HSP](../quick-start/in-app-hsp.md) or [HAR](../quick-start/har-package.md)) requires an individual **route_map.json** file. When routing is triggered, the application only needs to pass the name of the page that needs to be routed through the routing API provided by **NavPathStack**. The system then automatically completes the dynamic loading of the target module, page component construction, and route redirection. This way, module decoupling is achieved at the development level. The system routing table supports the Emulator but not the Previewer. The main steps are as follows:

1. Add routing table configuration to the [module.json5](../quick-start/module-configuration-file.md) file of the target module.

    <!-- @[moduleJson5](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/module.json5) -->
    
    ``` JSON5
    {
      "module": {
        // ···
        "routerMap": "$profile:route_map",
        // ···
      }
    }
    ```

2. Create the **route_map.json** file in **resources/base/profile** of the project directory. Add the following configuration information:
   
     ```json
     {
       "routerMap": [
         {
           "name": "PageOne",
           "pageSourceFile": "src/main/ets/pages/PageOne.ets",
           "buildFunction": "PageOneBuilder",
           "data": {
             "description" : "this is PageOne"
           }
         }
       ]
     }
     ```

    The configuration is described as follows.

   | Item| Description|
   |---|---|
   | name | Name of the target page.|
   | pageSourceFile | Path of the target page in the package, relative to the **src** directory.|
   | buildFunction | Name of the entry point function for redirection to the target page, which must be decorated by @Builder.|
   | data | Custom data. You can obtain the value through the **getConfigInRouteMap** API.|

3. On the target page, configure the @Builder decorated entry point function. The function name must be the same as the value of **buildFunction** in the **route_map.json** file. Otherwise, an error is reported at compile time.

   <!-- @[SystemRoutingTableOne](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/PageOne.ets) -->
   
   ``` TypeScript
   // Entry point function for redirection to the target page
   @Builder
   export function PageOneBuilder() {
     PageOne();
   }
   
   @Component
   struct PageOne {
     pathStack: NavPathStack = new NavPathStack();
   
     build() {
       NavDestination() {
       }
       .title('PageOne')
       .onReady((context: NavDestinationContext) => {
         this.pathStack = context.pathStack;
       })
     }
   }
   ```

4. Use a routing API such as [pushPathByName](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#pushpathbyname10) to navigate to the target page. (Note: In this case, you do not need to configure the [navDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navdestination10) attribute on the **Navigation** component.)

   <!-- @[SystemRoutingTable](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/PageOne.ets) -->
   
   ``` TypeScript
   @Entry
   @Component
   struct SystemRoutingTable {
     pageStack : NavPathStack = new NavPathStack();
   
     build() {
       Navigation(this.pageStack){
       }.onAppear(() => {
         this.pageStack.pushPathByName('PageOne', null, false);
       })
       .hideNavBar(true)
     }
   }
   ```

### Custom Routing Table

A custom routing table is implemented by configuring the Builder function for the [navDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navdestination10) attribute of **Navigation**. This approach requires importing page modules, which can be done through either static or dynamic import. The differences between these two methods are as follows.

| Import Mode| Module Coupling  | Implementation Complexity| Performance                                    |
| ---------- | -------------- | ---------- | ---------------------------------------- |
| Dynamic import| Low coupling between modules| High| Excellent; pages are loaded on demand, with target pages loaded just before navigation|
| Static import| High coupling between modules| Low| Average; all dependent pages are loaded during initialization|

**Dynamic Import (Recommended)**

Dynamic import enables reuse of service logic across multiple modules (HAR/HSP) to achieve service module decoupling. In addition, it supports route function extension and integration while allowing on-demand loading. For implementation details, see <!--RP1-->the [dynamic route example](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/BasicFeature/ApplicationModels/DynamicRouter)<!--RP1End-->.

Dynamic import offers the following advantages:

- Beyond the navigation URL, you can configure extended information in route definitions, such as the default orientation (landscape or portrait) and authentication requirements, which is processed during route navigation.
- You can assign a name to each routing page and navigate by name instead of file path.
- Dynamic imports (on-demand loading) can be used to load pages to prevent the first page from loading a large amount of code, which can cause stuttering.

Implementation solution:

1. Define page navigation configuration items.
   - Use resource files for definitions and use the [@ohos.resourceManager](../reference/apis-localization-kit/js-apis-resource-manager.md) module to parse the resource files at runtime.
   - Configure the route loading options in the .ets file, including the route page name (that is, the alias of the page in APIs like **pushPath**), name of the module where the file is located (name of the HSP/HAR module), and path to the target page in the module (relative to the **src** directory).
2. Use [dynamic import](../arkts-utils/arkts-dynamic-import.md) to load the module containing the target page at runtime. Once the module is loaded, call a method within the module that uses **import** to load and display the target page, then return the **Builder** function defined after the page has finished loading.
3. Execute the **Builder** function loaded in step 2 on the [navDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navdestination10) attribute of the **Navigation** component to navigate to the target page.

**Static Import**

Static import is straightforward to implement. However, using static imports for routing navigation creates dependency coupling between modules and increases the initial page loading time. Whenever possible, use either dynamic imports with a [custom routing table](#custom-routing-table) or the [system routing table](#system-routing-table) instead.

Implementation solution:

<!-- @[CustomRoutingTable](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/CustomRoutingTable.ets) -->

``` TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
const DOMAIN = 0x0000;
@Entry
@Component
struct NavigationExample {
  @Provide('navPathStack') navPathStack: NavPathStack = new NavPathStack();
  private arr: number[] = [1, 2];

  @Builder
  pageMap(name: string) {
    if (name === 'NavDestinationTitle1') {
      pageOneTmp();
    } else if (name === 'NavDestinationTitle2') {
      pageTwoTmp();
    }
  }

  build() {
    Column() {
      Navigation(this.navPathStack) {
        TextInput({ placeholder: 'Search...' })
          .width('90%')
          .height(40)

        List({ space: 12 }) {
          ForEach(this.arr, (item: number) => {
            ListItem() {
              Text('Page' + item)
                .width('100%')
                .height(72)
                .borderRadius(24)
                .fontSize(16)
                .fontWeight(500)
                .textAlign(TextAlign.Center)
                .onClick(() => {
                  this.navPathStack.pushPath({ name: 'NavDestinationTitle' + item });
                })
            }
          }, (item: number) => item.toString())
        }
        .width('90%')
        .margin({ top: 12 })
      }
      // The value in the $r('app.string.mainTitle') resource file is "Main Title."
      .title($r('app.string.mainTitle'))
      .navDestination(this.pageMap)
      .mode(NavigationMode.Split)
    }
    .height('100%')
    .width('100%')
  }
}

@Component
export struct pageTwoTmp {
  @Consume('navPathStack') navPathStack: NavPathStack;
  context = this.getUIContext().getHostContext();
  build() {
    NavDestination() {
      Column() {
        Text('NavDestinationContent2')
      }.width('100%').height('100%')
    }.title('NavDestinationTitle2')
    .onBackPressed(() => {
      const popDestinationInfo = this.navPathStack.pop(); // Pop the top element out of the navigation stack.
      // The value in the $r('app.string.returnValue') resource file is "Return value."
      hilog.info(DOMAIN, 'testTag', 'pop', this.context!.resourceManager.getStringSync($r('app.string.returnValue').id),
        JSON.stringify(popDestinationInfo));
      return true;
    })
  }
}

@Component
export struct pageOneTmp {
  @Consume('navPathStack') navPathStack: NavPathStack;
  context = this.getUIContext().getHostContext();
  build() {
    NavDestination() {
      Column() {
        Text('NavDestinationContent1')
      }.width('100%').height('100%')
    }.title('NavDestinationTitle1')
    .onBackPressed(() => {
      const popDestinationInfo = this.navPathStack.pop(); // Pop the top element out of the navigation stack.
      // The value in the $r('app.string.returnValue') resource file is "Return value."
      hilog.info(DOMAIN, 'testTag', 'pop', this.context!.resourceManager.getStringSync($r('app.string.returnValue').id),
        JSON.stringify(popDestinationInfo));
      return true;
    })
  }
}
```

## Navigation Examples

### Creating a Navigation Home Page
The implementation procedure is as follows:

1. Create a navigation home page using the [Navigation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md) component and create a navigation controller **NavPathStack** to enable transitions between pages.

2. Place a [List](../reference/apis-arkui/arkui-ts/ts-container-list.md) component inside the **Navigation** component to display the first‑level pages available from the home page.

3. Attach an **onClick** event to each item in the **List**. Inside the event handler, call the [pushPathByName](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#pushpathbyname10) method of the **NavPathStack** controller. When the item is clicked, this method navigates from the current page to the page whose name matches the specified parameter in the routing table.

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
        // Replace $r('app.string.enterKeyWordsToSearch') with the string resource file you use.
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
      .title($r('app.string.settings')) // Set the title text.
    }
    .size({ width: '100%', height: '100%' })
    .backgroundColor(0xf4f4f5)
  }
}
```


### Creating a Navigation Subpage
Create navigation subpage 1 as follows:

1. Use [NavDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md) to define the subpage UI (**PageOne**).

2. Create a navigation controller ([NavPathStack](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navpathstack10)) and initialize it in the [onReady](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#onready11) callback. This provides access to the current navigation stack for managing page transitions.

3. Attach an **onClick** event to a component within the subpage. In the event handler, call the [pop](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#pop10) method of the **NavPathStack** controller. When the component is clicked, this removes the current page from the stack and returns to the previous page.

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

1. Use **NavDestination** to create a navigation subpage **PageTwo**.

2. Create a navigation controller **NavPathStack** and initialize it when **onReady** is triggered. Obtain the current navigation controller to enable transitions between different pages.

3. Attach an **onClick** event to each item on the subpage. Inside the event handler, call the [pushPathByName](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#pushpathbyname10) method of the **NavPathStack** controller. When the item is clicked, this method navigates from the current page to the page whose name matches the specified parameter in the routing table.

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


### Creating Route Navigation
The implementation procedure is as follows:

1. Configure {"routerMap": "$profile:router_map"} in the project configuration file [module.json5](../quick-start/module-configuration-file.md).

2. In the **router_map.json** file, define the global routing table. The navigation controller **NavPathStack** can push the corresponding page information onto the stack based on the name in the routing table.
```ts
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
<!--RP2--><!--RP2End-->

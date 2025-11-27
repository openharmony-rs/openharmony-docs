# Navigation基础架构介绍

组件导航（[Navigation](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navigation)）主要用于实现Navigation页面（[NavDestination](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navdestination)）间的跳转，支持在不同NavDestination间传递参数，提供灵活的跳转栈操作，从而更便捷地实现对不同页面的访问和复用。Navigation组件结构较为复杂，包含几个关键概念：

- [Navigation](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navigation)：导航根视图容器，所有的导航组件都被此容器包裹。
- [NavDestination](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navdestination)：子页面容器，导航的所有页面路由操作均是针对NavDestination的操作，主要部分有：
  - 标题栏：包括返回按钮、标题，系统提供默认风格，同时支持自定义。
  - 内容区：NavDestination的子组件，完全由开发者定义。
  - 工具栏：位于NavBar底部，系统提供默认风格，同时支持自定义。
- NavBar：导航栏，也称为主页面，主要部分有：
  - 标题栏：位于NavBar顶部，包括标题与菜单栏，系统提供默认风格，同时支持自定义。
  - 内容区：位于NavBar中心区域，其内容完全由开发者自定义。
  - 工具栏：位于NavBar底部，系统提供默认风格，同时支持自定义。
- [ NavPathStack](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navigation#navpathstack10)：导航控制器，其封装了各种控制页面跳转的接口。

  **图1** Navigation总体架构图  

![NavigationArchitectureDiagram](figures/NavigationArchitectureDiagram.png)

此外Navigation提供两种布局模式：单栏模式、分栏模式，不同模式下的结构如下：

- 单栏模式

  单栏模式适用于窄屏设备，发生路由跳转时，整个页面都会被替换。

  **图2** 单栏布局示意图  

  ![zh-cn_image_0000001511740532](figures/zh-cn_image_0000001511740532.png)

  ![导航单栏模式](figures/导航单栏模式.jpg)

- 分栏模式

  分栏模式适用于宽屏设备，分为左右两部分，发生路由跳转时，只有右边子页会被替换。

  **图3** 分栏布局示意图

  ![zh-cn_image_0000001562820845](figures/zh-cn_image_0000001562820845.png)

  ![导航分栏模式](figures/导航分栏模式.jpg)



## Navigation（导航容器）

Navigation是路由导航的根视图容器，一般作为页面（@Entry修饰的自定义组件，定义为Router页面）的根容器（作为全局导航使用），包括单栏（Stack）、分栏（Split）和自适应（Auto）三种显示模式，Auto模式会基于Navigation组件的宽度自动在Stack和Split中切换。

Navigation组件本身可不作为显示容器，只用于承载路由的相关功能，如绑定导航控制器对象，路由切换，分栏显示，自定义转场动画控制等。

Navigation组件主要包含导航栏（NavBar）和子页（NavDestination），子页通过栈结构管理（存在NavPathStack中）。导航栏又称Navbar（Navigation的子组件，直接挂载到Navigation上），可以通过[hideNavBar](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navigation#hidenavbar9)属性进行隐藏（单栏应用推荐隐藏导航页），导航栏不存在页面栈中。

子页面是一个以NavDestination为根节点的子树，通过[@Builder](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/arkts-builder)构造出来，再通过NavPathStack提供的栈操作方法挂载到Navigation上显示，后续详细介绍。



## NavDestination（子页面容器）

Navigation子页面的根容器，每个子页面都需要包裹在一个NavDestination中，通过NavPathStack提供的栈操作方法（push，pop等）将子页面挂载到Navigation上显示或删除。

NavDestination作为页面根容器，除了支持普通组件的通用属性外，还支持页面相关的属性，如：[页面的生命周期](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navdestination#%E4%BA%8B%E4%BB%B6)，页面[工具栏](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navdestination#toolbarconfiguration13)、[标题栏](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navdestination#title)与[菜单栏](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navdestination#menus12)，[自定义页面转场动画](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navdestination#customtransition15)，页面级窗口属性控制（横竖屏，系统状态栏，系统导航条）等能力。



## NavBar（导航栏）

Navigation中直接加载的孩子节点称为导航栏（NavBar），单栏显示时它是整个导航的首页，分栏显示时它是固定的导航栏（默认显示在左边，也可以通过[navBarPosition](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navigation#navbarposition9)属性控制）。

开发者可以通过[hideNavBar](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navigation#hidenavbar9)去控制导航栏的显隐（推荐仅单栏显示的应用隐藏掉NavBar），也可以通过[navBarWidth](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navigation#navbarwidth9)属性控制双栏显示下的Navbar宽度，NavBar本身不属于页面栈中的页面，不具备页面的生命周期等，不能通过NavPathStack的方法控制。 开发者可以通过[onNavBarStateChange](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navigation#onnavbarstatechange9)去感知导航栏的显隐，通过[mode](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navigation#mode9)属性控制单双栏切换，也可以通过[onNavigationModeChange](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navigation#onnavigationmodechange11)去感知单双栏的切换。

NavBar的内容区可以通过两种方式指定：

方式一，直接指定Navigation的子节点。

  <!-- @[Navigation_NavBar](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template7/PageOne.ets) -->

```typescript
    Navigation(this.stack) {
      Stack({ alignContent: Alignment.Center }) {
        // ...
      }
      .width('100%')
      .height('100%')
    }
    .width('100%')
    .height('100%')
    .title('Navigation')
```

方式二，从API version 20开始，使用[主页类型NavDestination](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navigation#navigation20)将某个NavDestination直接指定为导航栏内容，此方法需要配置路由表，配置方式将在后文介绍。

## NavPathStack（导航控制器）

Navigation的子页面栈存在NavPathStack中，每个Navigation都需要绑定一个NavPathStack对象，NavPathStack用于控制Navigation中所有子页的切换，NavPathStack提供了很多基础的路由切换方法，如：pushPath，pushDestination（带返回回调），pop，replacePath等，以及路由拦截，转场动画控制，路由栈信息获取等能力。

NavPathStack也支持开发者继承并复写相关路由操作方法。 NavPathStack跟Navigation一一对应，在每个子页中可以通过NavDestination的onReady回调获取，也可以全局维护一个单例的NavPathStack，在任意地方获取并执行路由操作（注意：页面切换动画和布局必须在UI线程中才可以生效，依赖Vsync信号）。



## 标题栏、工具栏与菜单栏

### 设置标题栏模式

标题栏在界面顶部，用于呈现界面名称和操作入口，Navigation组件通过[title](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navigation#title)属性设置标题内容，通过[titleMode](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navigation#titlemode)属性设置标题栏模式。

> **说明：**
> Navigation或NavDestination未设置主副标题并且没有返回键时，不显示标题栏。

- Mini模式

  普通型标题栏，用于一级页面不需要突出标题的场景。

  **图4** Mini模式标题栏  

  ![mini](figures/mini.jpg)


  <!-- @[NavigationTitleModeMini](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/TitleModeMini.ets) -->

  ``` TypeScript
  Navigation() {
    // ···
  }
  .titleMode(NavigationTitleMode.Mini)
  ```

- Full模式

  强调型标题栏，用于一级页面需要突出标题的场景。

    **图5** Full模式标题栏  

  ![free1](figures/free1.jpg)


  <!-- @[NavigationTitleModeFUll](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/TitleModeFull.ets) -->

  ``` TypeScript
  Navigation() {
    // ···
  }
  .titleMode(NavigationTitleMode.Full)
  ```

### 设置菜单栏

菜单栏位于Navigation组件的右上角，开发者可以通过[menus](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navigation#menus)属性进行设置。menus支持Array&lt;[NavigationMenuItem](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navigationmenuitem)&gt;和[CustomBuilder](../reference/apis-arkui/arkui-ts/ts-types.md#custombuilder8)两种参数类型。使用Array&lt;NavigationMenuItem&gt;类型时，竖屏最多支持显示3个图标，横屏最多支持显示5个图标，多余的图标会被放入自动生成的更多图标。

**图6** 设置了3个图标的菜单栏  

![菜单栏2](figures/菜单栏2.jpg)

   <!-- @[NavigationMenuThreeImage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/MenusThreeImage.ets) -->

   ``` TypeScript
   let toolTmp: NavigationMenuItem  = {
     'value': 'func',
     'icon': 'ets/pages/navigation/template1/image/ic_public_add.svg',
     'action': () => {}
   };
   // ···
         Navigation(this.pageInfos) {
           // ···
         }
         .menus([toolTmp, toolTmp, toolTmp])
   ```

图片也可以引用resources中的资源。

   <!-- @[NavigationMenuThreeResource](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/MenusThreeResource.ets) -->

   ``` TypeScript
   let toolTmp: NavigationMenuItem  = {
     'value': 'func',
     'icon': 'resources/base/media/ic_public_add.svg',
     'action': () => {}
   };
   // ···
         Navigation(this.pageInfos) {
           // ···
         }
         .menus([toolTmp, toolTmp, toolTmp])
   ```

**图7** 设置了4个图标的菜单栏  

![菜单栏](figures/菜单栏.jpg)

竖屏状态下菜单栏，最多支持显示3个按钮，当按钮超过3个时，多余的按钮会被折叠。

   <!-- @[NavigationMenuFour](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/MenusFour.ets) -->

   ``` TypeScript
   let toolTmp: NavigationMenuItem  = {
     'value': 'func',
     'icon': 'ets/pages/navigation/template1/image/ic_public_add.svg',
     'action': () => {}
   };
   // ···
         Navigation(this.pageInfos) {
           // ···
         }
         // 竖屏最多支持显示3个图标，多余的图标会被放入自动生成的更多图标
         .menus([toolTmp, toolTmp, toolTmp, toolTmp])
   ```

### 设置工具栏

工具栏位于Navigation组件的底部，开发者可以通过[toolbarConfiguration](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#toolbarconfiguration10)属性进行设置。


  **图8** 工具栏  

![free3](figures/free3.jpg)

   <!-- @[ToolBar](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/ToolBar.ets) -->

   ``` TypeScript
   let toolTmp: ToolbarItem = {
     'value': 'func',
     'icon': 'ets/pages/navigation/template1/image/ic_public_highlights.svg',
     'action': () => {}
   };
   let tooBar: ToolbarItem[] = [toolTmp,toolTmp,toolTmp];
   // ···
         Navigation(this.pageInfos) {
           // ···
         }
         .toolbarConfiguration(tooBar)
   ```
# Navigation转场动画

Navigation默认提供了页面切换的转场动画，通过导航控制器操作时，会触发不同的转场效果（API version 13之前，Dialog类型的页面默认无转场动画。从API version13开始，Dialog类型的页面支持系统转场动画。），Navigation也提供了关闭系统转场、自定义转场以及共享元素转场的能力。系统默认动画时长由物理曲线参数决定，不同设备上动画时长存在差异。

## 关闭转场

- 全局关闭
  
  Navigation通过NavPathStack中提供的[disableAnimation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#disableanimation11)方法可以在当前Navigation中关闭或打开所有转场动画。

  <!-- @[PageAnimated](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/PageAnimated.ets) -->
  
  ``` TypeScript
  pageStack: NavPathStack = new NavPathStack();
  
  aboutToAppear(): void {
    this.pageStack.disableAnimation(true);
  }
  ```

- 单次关闭
  
  NavPathStack中提供的Push、Pop、Replace等接口中可以设置animated参数，默认为true表示有转场动画，需要单次关闭转场动画可以置为false，不影响下次转场动画。

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

## 自定义转场

- Navigation自定义转场

  Navigation自定义转场动画能力通过[customNavContentTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#customnavcontenttransition11)事件提供，可以通过以下三步定义自定义转场动画：

  1. 构建一个自定义转场动画工具类CustomNavigationUtils，通过一个Map管理各页面的自定义动画对象CustomTransition。页面在创建时注册其自定义转场动画对象，在销毁时取消注册。
  2. 实现一个转场协议对象[NavigationAnimatedTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#navigationanimatedtransition11)。其中，timeout属性表示转场结束的超时时间，默认为1000ms，transition属性为自定义的转场动画方法。开发者需在此实现自己的转场动画逻辑，系统在转场开始时会调用此方法，onTransitionEnd为转场结束时的回调。
  3. 调用customNavContentTransition方法并返回实现的转场协议对象，若返回undefined，则使用系统默认转场。

  具体示例代码可参考[Navigation自定义转场示例](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#示例3设置可交互转场动画)。

- NavDestination自定义转场

  NavDestination支持自定义转场动画，通过设置[customTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#customtransition15)属性即可实现单个页面的自定义转场效果。要实现这一功能，需完成以下步骤：

  1. 实现[NavDestination的转场代理](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#navdestinationtransitiondelegate15)，针对不同的堆栈操作类型返回自定义的转场协议对象[NavDestinationTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#navdestinationtransition15)。其中，event是必填参数，需在此处编写自定义转场动画的逻辑；而onTransitionEnd、duration、curve与delay为可选参数，分别对应动画结束后的回调、动画持续时间、动画曲线类型与开始前的延时。若在转场代理中返回多个转场协议对象，这些动画效果将逐层叠加。
  2. 通过调用NavDestination组件的customTransition属性，并传入上述实现的转场代理，完成自定义转场的设置。

  具体示例代码可以参考[NavDestination自定义转场示例](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#示例2设置navdestination自定义转场)。

- 使用建议
  1. Navigation自定义转场[customNavContentTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#customnavcontenttransition11)适用于控制Navigation内所有页面，统一转场动画效果。
  2. NavDestination自定义转场[customTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#customtransition15)适用于控制单个页面的转场效果。
  3. 在同时使用[customNavContentTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#customnavcontenttransition11)和[customTransition](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md#customtransition15)时，customNavContentTransition优先级更高。

## 共享元素转场

NavDestination之间切换时可以通过[geometryTransition](../reference/apis-arkui/arkui-ts/ts-transition-animation-geometrytransition.md#geometrytransition)实现共享元素转场。配置了共享元素转场的页面同时需要关闭系统默认的转场动画。
1. 为需要实现共享元素转场的组件添加geometryTransition属性，id参数必须在两个NavDestination之间保持一致。

   <!-- @[GeometryTransitionFromPage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/GeometryTransition.ets) -->
   
   ``` TypeScript
   // 起始页配置共享元素id
   NavDestination() {
     Column() {
       // ···
       // $r('app.media.startIcon')需要替换为开发者所需的资源文件
       Image($r('app.media.startIcon'))
         .geometryTransition('sharedId')
         .width(100)
         .height(100)
     }
   }.title('FromPage')
   ```

   <!-- @[GeometryTransitionToPage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/GeometryTransition.ets) -->
   
   ``` TypeScript
   // 目的页配置共享元素id
   NavDestination() {
     Column() {
       // $r('app.media.startIcon')需要替换为开发者所需的资源文件
       Image($r('app.media.startIcon'))
         .geometryTransition('sharedId')
         .width(200)
         .height(200)
     }
   }
   .title('ToPage')
   ```

2. 将页面路由的操作，放到[animateTo](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/arkts-apis-uicontext-uicontext#animateto)动画闭包中，配置对应的动画参数以及关闭系统默认的转场。

   <!-- @[GeometryTransitionFromPageOne](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NavigationSample/entry/src/main/ets/pages/navigation/template1/GeometryTransition.ets) -->
   
   ``` TypeScript
   NavDestination() {
     Column() {
       // $r('app.string.ToPage')需要替换为开发者所需的字符串资源文件
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

## 导航动画常见问题

### 1 Dialog类型NavDestination蒙层动画不流畅如何解决？

**问题现象：**

使用NavDestinationMode.DIALOG默认转场动画

- 将蒙层背景色设置在页面上：pop页面的时候蒙层没有马上消失，而是等内容下滑退出后才消失。
- 将蒙层背景色设置在内容区域：蒙层一起从上向下退出。

期望退出时蒙层渐隐，同时内容区域向下退出。

**解决方案：**

在`onWillAppear`、`onWillDisappear`生命周期里执行背景色动画即可，参考如下实现：

```typescript
@Component
export struct Dialog {
  @Consume('pageInfos') pageInfos: NavPathStack;
  @State backColor: ResourceColor = "#0000000"

  build() {
    NavDestination() {
      Stack() {
        Text("Dialog")
          .fontSize(44)
      }
      .width('100%')
      .height('100%')
    }
    .hideTitleBar(true)
    .backgroundColor(this.backColor)
    .mode(NavDestinationMode.DIALOG)
    .onWillAppear(() => {
      //启动时候蒙层渐现
      this.getUIContext().animateTo({ duration:450 }, () => {
        this.backColor = "#66000000"
      })
    })
    .onWillDisappear(() => {
      // 消失时候蒙层渐隐
      this.getUIContext().animateTo({ duration: 450 }, () => {
        this.backColor = "#00000000"
      })
    })
  }
}
```

### 2 router、navigation动画冲突如何解决？

**问题现象：**

router跳到navigation页面，navigation在aboutToAppear回调里马上push一个NavDestination页面，这样会导致page和NavDestination页面同时做动画，效果不好。

**解决方案：**

关闭aboutToAppear中push的动画即可：

```typescript
@Entry
@Component
struct NavigationExample {
  navStack: NavPathStack = new NavPathStack();

  aboutToAppear(): void {
    AppStorage.setOrCreate<NavPathStack>('basicNavigationStack', this.navStack)
    this.navStack.pushPath({ name: 'PageOne' }, false) // 关闭本次push动画即可
  }

  build() {
    Navigation(this.navStack) {
        // ......
    }
  }
}
```

### 3 pop、push同时进行，为何展示pop动画？

**问题现象：**

先pop栈顶页面，再马上push一个页面，动画效果是栈顶页面pop的动画，并不是PageOne的push动画

```typescript
this.pageInfos.pop();
this.pageInfos.pushPath({name: 'PageOne'});
```

**解决方案：**

首先在一次操作中，不管调用了多少次pop、push接口，Navigation会计算最终结果，并且只做一次动画。

当前Navigation页面切换的动画规格是：以操作前的栈顶页面为主，如果栈顶页面在操作后不在栈中，则执行pop动画，若在栈中则执行push动画。

以此案例为例说明，当前栈顶是‘PageTop’，先执行pop将‘PageTop’移除再执行push将‘PageOne’入栈，本次操作完成后‘PageTop’页面已不在栈中，所以最终执行的动画是pop动画。

如果想移除页面的同时push另一个页面并且执行push动画，可以将push的页面设置为NEW_INSTANCE，默认执行push动画：

```typescript
this.pageInfos.pop();
this.pageInfos.pushPath({name: 'PageOne'}, { launchMode: LaunchMode.NEW_INSTANCE });
```



### 4 跳转动画是否有结束回调？

当前系统动画并没有提供动画结束回调，仅自定义转场动画提供了结束回调，若需要动画结束回调，则需要实现[自定义转场动画](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/arkts-navigation-navigation#自定义转场)，相关接口如下：

- [NavDestinationTransition](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navdestination#navdestinationtransition15)
- [NavigationAnimatedTransition](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navigation#navigationanimatedtransition11)

### 5 自定义动画太复杂，是否有系统封装好的不同类型的动画？

可以设置[NavDestination.systemTransition](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-basic-components-navdestination#systemtransition14)接口，系统提供了各种动画类型枚举。

### 6 如何实现 Navigation 和 NavDestination 之间的共享元素转场？

目前仅NavDestination间的跳转支持共享元素转场动效，NavBar与NavDestination间的跳转系统暂不支持共享元素动效。

Navigation的共享元素转场需要配合[geometryTransition](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-transition-animation-geometrytransition)接口实现，几个关键点需要注意：

- 需要关闭[Navigation跳转动画](#1 如何关闭跳转动画？)
- 跳转接口需要在[animateTo](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/arkts-apis-uicontext-uicontext#animateto)动画闭包内执行
- 给内容组件设置[geometryTransition](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-transition-animation-geometrytransition)属性，不要设置到NavDestination上

简易demo可参考：

- [共享元素转场](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/arkts-navigation-navigation#共享元素转场)

最佳实践案例可参考：

- [一镜到底动效-最佳实践](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-one-shot-to-the-end#section11650141951719)

### 7 给NavDestination设置zIndex后为何跳转动画异常？

[zIndex](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-universal-attributes-z-order#zindex)用于修改组件显示层级，给NavDestination此属性会覆盖掉系统设置的层级，导致动画被打乱。因此不建议给NavDestination设置zIndex。

此外也不建议设置如：[transition](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-transition-animation-component#transition)、[geometryTransition](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-transition-animation-shared-elements)、[sharedTransition](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-transition-animation-shared-elements#sharedtransition)、[animation](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/ts-animatorproperty)等特殊属性，可能与系统默认动画产生冲突。如果有业务需要设置这些属性，建议将这些属性设置在NavDestination的内容节点上，也可以达到相同效果。

### 8 NavDestination的默认转场动画时长是多久？

NavDestination的默认转场动画使用[弹簧曲线](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/arkts-spring-curve)，其时长与物理曲线参数有关，而且不同设备上的默认动画不同，因此默认转场动画时长不可控，不建议与业务耦合，若需要监听动画结束，建议使用[自定义转场动画](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/arkts-navigation-navigation#自定义转场)。
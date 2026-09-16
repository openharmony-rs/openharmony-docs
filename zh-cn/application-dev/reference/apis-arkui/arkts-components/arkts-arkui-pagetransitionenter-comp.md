# PageTransitionEnter

定义PageTransitionEnter组件。

## PageTransitionEnter

```TypeScript
PageTransitionEnter(value: PageTransitionOptions)
```

设置当前页面的自定义入场动效，需在pageTransition()函数中配置，继承自[CommonTransition](arkts-arkui-commontransition-c.md)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PageTransitionOptions](arkts-arkui-pagetransitionoptions-i.md) | 是 | 配置入场动效的参数，包含页面转场效果的路由类型(type)、动画时长(duration)、动画曲线(curve)、动画延迟时长(delay)配置项。 |

## PageTransitionEnter

```TypeScript
PageTransitionEnter(event: PageTransitionCallback)
```

逐帧回调，直到入场动画结束，progress从0变化到1。与slide、translate、scale、opacity等预设动效方法配合使用时，onEnter在预设动效基础上提供逐帧自定义逻辑；也可单独使用onEnter实现完全自定义的入场动画效果。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [PageTransitionCallback](arkts-arkui-pagetransitioncallback-t.md) | 是 | 入场动画的逐帧回调，直到动画结束，progress从0变化到1。该回调仅在配置的type与实际路由类型匹配时触发。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [PageTransitionExitInterface](arkts-arkui-pagetransitionexitinterface-i.md) | 当前页面的自定义退场动效。 |
| [PageTransitionOptions](arkts-arkui-pagetransitionoptions-i.md) | 退场/入场动效的参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [PageTransitionCallback](arkts-arkui-pagetransitioncallback-t.md) | 页面转场事件回调。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [RouteType](arkts-arkui-routetype-e.md) | 页面转场类型。 |
| [SlideEffect](arkts-arkui-slideeffect-e.md) | 页面转场时的滑入滑出效果。 |

## 示例

```TypeScript
### 示例1（设置退入场动画）

自定义方式1：通过不同的退入场类型配置不同的退场和入场动画。
```

```TypeScript
// Page1.ets
@Entry
@Component
struct Page1 {
  @State pageScale: number = 1;
  @State pageOpacity: number = 1;

  build() {
    Column() {
      // $r("app.media.transition_image2")需要替换为开发者所需的图像资源文件。
      Image($r("app.media.transition_image2")).width('100%').height('100%') // 图片存放在media文件夹下
    }
    .width('100%')
    .height('100%')
    .scale({ x: this.pageScale })
    .opacity(this.pageOpacity)
    .onClick(() => {
      this.getUIContext().getRouter().pushUrl({ url: 'pages/Index' });
    })
  }

  pageTransition() {
    PageTransitionEnter({ duration: 1200, curve: Curve.Linear })
      .onEnter((type: RouteType, progress: number) => {
        if (type == RouteType.Push || type == RouteType.Pop) {
          this.pageScale = progress;
        }
        this.pageOpacity = progress;
      })
    PageTransitionExit({ duration: 1200, curve: Curve.Ease })
      .onExit((type: RouteType, progress: number) => {
        if (type == RouteType.Pop) {
          this.pageScale = 1 - progress;
          this.pageOpacity = 1 - progress;
        }
      })
  }
}
```

```TypeScript


自定义方式2：配置了当前页面的入场动画为从左侧滑入，退场为平移加透明度变化。
```

```TypeScript

```

```TypeScript
### 示例2（设置退入场平移效果）

自定义方式1：配置提供的不同退入场平移效果，将系统语言排版模式改为RTL。
```

```TypeScript
// Page1.ets
@Entry
@Component
struct Page1 {
  @State pageScale: number = 1;
  @State pageOpacity: number = 1;

  build() {
    Column() {
      Button("页面2").onClick(() => {
        this.getUIContext().getRouter().pushUrl({
          url: "pages/Index"
        });
      })
        .width(200)
        .height(60)
        .fontSize(36)
      Text("END")
        .fontSize(36)
        .textAlign(TextAlign.Center)
    }
    .scale({ x: this.pageScale })
    .opacity(this.pageOpacity)
    .height("100%")
    .width("100%")
    .justifyContent(FlexAlign.Center)
  }

  // 自定义方式2：使用系统提供的多种默认效果（平移、缩放、透明度等）
  pageTransition() {
    PageTransitionEnter({ duration: 200 })
      .slide(SlideEffect.END) // Right
    PageTransitionExit({ delay: 100 })
      .slide(SlideEffect.END)
  }
}
```

```TypeScript


自定义方式2：使用系统默认的退入场效果，将系统语言排版模式改为RTL。
```

```TypeScript
// Page1.ets
@Entry
@Component
struct Page1 {
  @State pageScale: number = 1;
  @State pageOpacity: number = 1;

  build() {
    Column() {
      Button("页面2").onClick(() => {
        this.getUIContext().getRouter().pushUrl({
          url: "pages/Index"
        });
      })
        .width(200)
        .height(60)
        .fontSize(36)
    }
    .scale({ x: this.pageScale })
    .opacity(this.pageOpacity)
    .height("100%")
    .width("100%")
    .justifyContent(FlexAlign.Center)
  }
}
```

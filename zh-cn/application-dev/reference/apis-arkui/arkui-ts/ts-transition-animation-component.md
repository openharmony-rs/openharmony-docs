# 组件内转场 (transition)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @yangfan229-->
<!--Tester: @lxl007-->
<!--Adviser: @HelloCrease-->

组件内转场主要通过transition属性配置转场参数，在组件插入和删除时显示过渡动效，主要用于容器组件中的子组件插入和删除时，提升用户体验。 

>  **说明：**
>
>  从API version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
>  当前有两种方式触发组件的transition：
>  1. 当组件插入或删除时（如if条件改变、ForEach新增删除组件），会递归的触发所有新插入/删除的组件的transition效果。
>  2. 当组件[Visibility](ts-universal-attributes-visibility.md)属性在可见和不可见之间改变时，只触发该组件的transition效果。

## 接口

### transition

transition(value: TransitionOptions | TransitionEffect): T

组件插入显示和删除隐藏的过渡效果。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- |  ---- | -------- |
| value | [TransitionOptions](#transitionoptionsdeprecated)<sup>(deprecated)</sup> \| [TransitionEffect](#transitioneffect10对象说明)<sup>10+</sup>  | 是 | 设置组件插入显示和删除隐藏的过渡效果。<br/>**说明：** <br/>详细描述见[TransitionOptions](#transitionoptionsdeprecated)和[TransitionEffect](#transitioneffect10对象说明)对象说明。|

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回当前组件。 |

### transition<sup>12+</sup>

transition(effect: TransitionEffect, onFinish: Optional&lt;TransitionFinishCallback&gt;): T

组件插入显示和删除隐藏的过渡效果。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- |  ---- | -------- |
| effect | [TransitionEffect](#transitioneffect10对象说明)  | 是 | 设置组件插入显示和删除隐藏的过渡效果。 |
| onFinish | Optional&lt;[TransitionFinishCallback](#transitionfinishcallback12)&gt; | 是 | 转场动画结束回调。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| T | 返回当前组件。 |

## TransitionEdge<sup>10+</sup>

**卡片能力：** 从API version 10开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称     | 值 | 说明     |
| ------ | ------ | ------ |
| TOP    | - | 窗口的上边缘。 |
| BOTTOM | - | 窗口的下边缘。 |
| START  | - | 窗口的起始边缘，LTR时为左边缘，RTL时为右边缘。 |
| END    | - | 窗口的终止边缘，LTR时为右边缘，RTL时为左边缘。 |

## TransitionEffect<sup>10+</sup>对象说明

TransitionEffect以函数的形式指定转场效果。提供了以下接口：

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | ---------- | -------- | -------- | -------- |
| opacity | number | 否 | 否 | 设置组件转场时的透明度效果，为插入时起点和删除时终点的值。<br/>取值范围： [0, 1]<br/>**说明：** <br/>设置小于0的非法值按0处理，大于1的非法值按1处理。<br/>**卡片能力：** 从API version 10开始，该接口支持在ArkTS卡片中使用。 |
| translate | [TranslateOptions](ts-universal-attributes-transformation.md#translateoptions对象说明) | 否 | 否 | 设置组件转场时的平移效果，为插入时起点和删除时终点的值。<br/>-x：横向的平移距离。<br/>-y：纵向的平移距离。<br/>-z：竖向的平移距离。<br/>**卡片能力：** 从API version 10开始，该接口支持在ArkTS卡片中使用。 |
| scale |   [ScaleOptions](ts-universal-attributes-transformation.md#scaleoptions对象说明)| 否 | 否 | 设置组件转场时的缩放效果，为插入时起点和删除时终点的值。<br/>-x：横向放大倍数（或缩小比例）。<br/>-y：纵向放大倍数（或缩小比例）。<br/>-z：当前为二维显示，该参数无效 。<br/>-&nbsp;centerX、centerY指缩放中心点，centerX和centerY默认值是"50%"，即默认以组件的中心点为缩放中心点。<br/>-&nbsp;中心点为(0, 0)代表组件的左上角。<br>**说明：** <br>设置centerX、centerY为非法字符串时（例如，"illegalString"），默认值为"0"。<br/>**卡片能力：** 从API version 10开始，该接口支持在ArkTS卡片中使用。 |
| rotate | [RotateOptions](ts-universal-attributes-transformation.md#rotateoptions对象说明)  | 否 | 否 | 设置组件转场时的旋转效果，为插入时起点和删除时终点的值。<br/>-x：横向的旋转向量分量。<br/>-y：纵向的旋转向量分量。<br/>-z：竖向的旋转向量分量。<br/>-&nbsp;centerX、centerY指旋转中心点，centerX和centerY默认值是"50%"，即默认以组件的中心点为旋转中心点。<br/>-&nbsp;中心点为(0, 0)代表组件的左上角。<br/>-centerZ指z轴锚点，即3D旋转中心点的z轴分量，centerZ默认值是0。<br/>-perspective指视距，不支持perspective属性做转场动画。<br/>**卡片能力：** 从API version 10开始，该接口支持在ArkTS卡片中使用。 |
| move | [TransitionEdge](#transitionedge10) | 否 | 否 | 指定组件转场时从屏幕边缘滑入和滑出的效果，本质为平移效果，为插入时起点和删除时终点的值。<br/>**卡片能力：** 从API version 10开始，该接口支持在ArkTS卡片中使用。 |
| asymmetric | {appear: [TransitionEffect](#transitioneffect10对象说明),<br/>disappear: [TransitionEffect](#transitioneffect10对象说明)}<br/> | 否 | 否 | 指定非对称的转场效果。<br/>第一个参数指定出现的转场效果，第二个参数指定消失的转场效果。<br/>如不通过asymmetric函数构造TransitionEffect，则表明该效果在组件出现和消失时均生效。<br/>**卡片能力：** 从API version 10开始，该接口支持在ArkTS卡片中使用。 |

上表提供的静态函数用于构造TransitionEffect对象，而非静态函数作用于构造好的TransitionEffect对象，以指定多种转场效果的组合效果和动画参数。
此外TransitionEffect提供了一些转场效果的静态成员变量：
| 静态成员名称 | 参数描述 |
| -------- | -------- |
| IDENTITY | 禁用转场效果。 |
| OPACITY | 为组件添加透明度转场效果，出现时透明度从0到1、消失时透明度从1到0，相当于TransitionEffect.opacity(0)。 |
| SLIDE | 相当于TransitionEffect.asymmetric(TransitionEffect.move(TransitionEdge.START), TransitionEffect.move(TransitionEdge.END))。从START边滑入，END边滑出。即在LTR模式下，从左侧滑入，右侧滑出；在RTL模式下，从右侧滑入，左侧滑出。 |
| SLIDE_SWITCH | 指定出现时从右先缩小再放大侧滑入、消失时从左侧先缩小再放大滑出的转场效果。自带动画参数，也可覆盖动画参数，自带的动画参数时长600ms，指定动画曲线cubicBezierCurve(0.24, 0.0, 0.50, 1.0)，最小缩放比例为0.8。|

>  **说明：**
>
>  1. TransitionEffect可通过combine函数实现多个转场效果的组合，可以为每个效果分别指定animation参数，且前一效果的animation的参数也可适用于后一效果。例如，TransitionEffect.OPACITY.animation({duration: 1000}).combine(TransitionEffect.translate({x: 100}))，则时长为1000ms的动画参数对OPACITY和translate均生效。
>  2. 动画参数的生效顺序为：本TransitionEffect指定的animation参数 > 前面的TransitionEffect指定的animation参数 > 触发该组件出现消失的animateTo中的动画参数。
>  3. 如果未使用animateTo触发转场动画且TransitionEffect中也无animation参数，则该组件直接出现或者消失。
>  4. TransitionEffect中指定的属性值如与默认值相同，则该属性不会产生转场动画。如TransitionEffect.opacity(1).animation({duration:1000})，由于opacity默认值也为1，未产生透明度动画，该组件直接出现或者消失。
>  5. 更详细的关于scale、rotate效果的介绍可参考[图形变换](ts-universal-attributes-transformation.md)。
>  6. 如果在动画范围([animateTo](../arkts-apis-uicontext-uicontext.md#animateto)、[animation](ts-animatorproperty.md))内触发组件的上下树或可见性([Visibility](ts-universal-attributes-visibility.md))改变，而根组件没有配置transition，会给该组件加上默认透明度转场，即TransitionEffect.OPACITY，动画参数跟随所处动画环境的参数。如不需要可通过主动配置TransitionEffect.IDENTITY来禁用，使该组件直接出现或消失。
>  7. 当通过删除整棵子树的方式触发消失转场，如需看到完整的消失转场过程，需要保证被删除子树的根组件的有充足的消失转场时间，见示例3。

### constructor<sup>10+</sup>

constructor(type: Type, effect: Effect)

构造TransitionEffect对象。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API version 10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型                                   | 必填 | 说明           |
| ------ | ------------------------------------------ | ---- | ------------------ |
| type  | [Type](ts-appendix-enums.md#transitiontype)                                    | 是   | 转场类型。 |
| effect  | [Effect](#transitioneffect10对象说明)                                     | 是   | 转场参数。 |

### combine<sup>10+</sup>

combine(transitionEffect: TransitionEffect): TransitionEffect

对TransitionEffect进行链式组合，以形成包含多种转场效果的TransitionEffect。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API version 10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明           |
| ------ | -------- | ---- | ------------------ |
| transitionEffect  | [TransitionEffect](#transitioneffect10对象说明)   | 是   | 被组合的过渡效果。 |

**返回值：**

| 类型   | 说明                     |
| ------ | ------------------------ |
| [TransitionEffect](#transitioneffect10对象说明) | 组合过渡效应。 |

### animation<sup>10+</sup>

animation(value: AnimateParam): TransitionEffect

指定该TransitionEffect的动画参数。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API version 10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明           |
| ------ | -------- | ---- | ------------------ |
| value  | [AnimateParam](ts-explicit-animation.md#animateparam对象说明)   | 是   | 动画参数。</br>该参数只用来指定动画参数，其入参AnimateParam的onFinish回调不生效。</br>如果通过combine进行TransitionEffect的组合，前一TransitionEffect的动画参数也可用于后一TransitionEffect。 |

**返回值：**

| 类型   | 说明                     |
| ------ | ------------------------ |
| [TransitionEffect](#transitioneffect10对象说明) | 当前动画效果。 |


## TransitionFinishCallback<sup>12+</sup>

type TransitionFinishCallback = (transitionIn: boolean) => void

组件转场动画的结束回调类型。

**卡片能力：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型                      | 必填 | 说明                                                         |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| transitionIn | boolean | 是   | 该入参表示转场动画的结束回调类型。<br/>该参数为true表示该转场回调是出现动画的结束回调，该参数为false表示该转场回调是消失动画的结束回调。 |

>  **说明：**
>  1. 当通过触发一棵子树的上下树，进而递归的触发出现消失转场时，只能保证根组件的消失动画结束回调能被调用。如果子组件的消失动画结束回调时间晚于根组件的消失动画结束回调，由于整棵子树已被销毁，子组件的结束回调不会被调用。
>  2. 当同一组件的最后一个同类型（即出现或者消失）的动画结束后，才会调用结束回调。即如果反复触发出现消失动画（例如通过Visibility触发），只有最后一次的出现消失的结束回调才会被调用。

## TransitionOptions<sup>(deprecated)</sup>

TransitionOptions通过指定结构体内的参数来指定转场效果。

从API version 10开始不再维护，建议使用[TransitionEffect](#transitioneffect10对象说明)代替。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| type | [TransitionType](ts-appendix-enums.md#transitiontype)  | 否 | 是 | 指定该转场样式生效的场景。<br/>默认值：TransitionType.All<br/>**说明：**<br/>不指定type时默认为TransitionType.All，即插入删除都生效。 |
| opacity | number | 否 | 是 | 设置组件转场时的透明度效果，为插入时起点和删除时终点的值。<br/>取值范围： [0, 1]<br/>**说明：** <br/>设置小于0的非法值时，按0处理；设置大于1的非法值时，按1处理。 |
| translate |   [TranslateOptions](ts-universal-attributes-transformation.md#translateoptions对象说明)  | 否 | 是  | 设置组件转场时的平移效果，为插入时起点和删除时终点的值。<br/>-x：横向的平移距离。<br/>-y：纵向的平移距离。<br/>-z：竖向的平移距离。|
| scale |  [ScaleOptions](ts-universal-attributes-transformation.md#scaleoptions对象说明) | 否 | 是 | 设置组件转场时的缩放效果，为插入时起点和删除时终点的值。<br/>-x：横向放大倍数（或缩小比例）。<br/>-y：纵向放大倍数（或缩小比例）。<br/>-z：当前为二维显示，该参数无效 。<br/>-&nbsp;centerX、centerY指缩放中心点，centerX和centerY默认值是"50%"，即默认以组件的中心点为缩放中心点。<br/>-&nbsp;中心点为(0, 0)代表组件的左上角。<br>**说明：** <br>设置centerX、centerY为非法字符串时（例如，"illegalString"），默认值为"0"。 |
| rotate |  [RotateOptions](ts-universal-attributes-transformation.md#rotateoptions对象说明)| 否 | 是 | 设置组件转场时的旋转效果，为插入时起点和删除时终点的值。<br/>-x：横向的旋转向量分量。<br/>-y：纵向的旋转向量分量。<br/>-z：竖向的旋转向量分量。<br/>-&nbsp;centerX、centerY指旋转中心点，centerX和centerY默认值是"50%"，即默认以组件的中心点为旋转中心点。<br/>-&nbsp;中心点为(0, 0)代表组件的左上角。 |

>  **说明：**
>
>  1. 当使用TransitionOptions类型的入参指定转场效果时，**必须**配合[animateTo](../arkts-apis-uicontext-uicontext.md#animateto)使用才有动画效果，动效时长、曲线、延时跟随animateTo中的配置。
>  2. 当使用TransitionOptions作为入参，且不指定除type外的任何参数时，此时相当于指定了透明度的转场效果。例如，指定{type: TransitionType.Insert}相当于指定了{type: TransitionType.Insert, opacity: 0}的转场效果。而指定了具体效果时，则不会添加默认的透明度转场效果。

## 示例

### 示例1（使用同一接口实现图片出现消失）

该示例主要演示如何通过同一TransitionEffect来实现图片的出现与消失，出现和消失互为逆过程。
```ts
// xxx.ets
@Entry
@Component
struct TransitionEffectExample1 {
  @State flag: boolean = true;
  @State show: string = 'show';

  build() {
    Column() {
      Button(this.show).width(80).height(30).margin(30)
        .onClick(() => {
          // 点击Button控制Image的显示和消失
          if (this.flag) {
            this.show = 'hide';
          } else {
            this.show = 'show';
          }
          this.flag = !this.flag;
        })
      if (this.flag) {
        // Image的显示和消失配置为相同的过渡效果（出现和消失互为逆过程）
        // 出现时从指定的透明度为0、绕z轴旋转180°的状态，变为默认的透明度为1、旋转角为0的状态，透明度与旋转动画时长都为2000ms
        // 消失时从默认的透明度为1、旋转角为0的状态，变为指定的透明度为0、绕z轴旋转180°的状态，透明度与旋转动画时长都为2000ms
        // $r('app.media.testImg')需要替换为开发者所需的图像资源文件。
        Image($r('app.media.testImg')).width(200).height(200)
          .transition(TransitionEffect.OPACITY.animation({ duration: 2000, curve: Curve.Ease }).combine(
            TransitionEffect.rotate({ z: 1, angle: 180 })
          ))
      }
    }.width('100%')
  }
}
```
示意图：<br/>
![transitionComponent2](figures/transitionComponent2.gif)

### 示例2（使用不同接口实现图片出现消失）

该示例主要演示使用不同TransitionEffect来实现图片的出现和消失。
```ts
// xxx.ets
@Entry
@Component
struct TransitionEffectExample2 {
  @State flag: boolean = true;
  @State show: string = 'show';

  build() {
    Column() {
      Button(this.show).width(80).height(30).margin(30)
        .onClick(() => {
          // 点击Button控制Image的显示和消失
          if (this.flag) {
            this.show = 'hide';
          } else {
            this.show = 'show';
          }
          this.getUIContext().animateTo({ duration: 2000 }, () => {
            // 第一张图的TransitionEffect包含了animation，transition的动画参数由TransitionEffect指定
            // 第二张图的TransitionEffect不包含animation，transition的动画参数由animateTo指定
            this.flag = !this.flag;
          });
        })
      if (this.flag) {
        // Image的显示和消失配置为不同的过渡效果
        // 出现时做从指定的透明度为0变为默认的透明度1的动画，该动画时长为1000ms，以及做从指定的绕z轴旋转180°变为默认的旋转角为0的动画，该动画1000ms后播放，时长为1000ms
        // 消失时做从默认的透明度为1变为指定的透明度0的动画，该动画1000ms后播放，时长为1000ms，以及做从默认的旋转角0变为指定的绕z轴旋转180°的动画，该动画时长为1000ms
        // $r('app.media.testImg')需要替换为开发者所需的图像资源文件。
        Image($r('app.media.testImg')).width(200).height(200)
          .transition(
            TransitionEffect.asymmetric(
              TransitionEffect.OPACITY.animation({ duration: 1000 }).combine(
              TransitionEffect.rotate({ z: 1, angle: 180 }).animation({ delay: 1000, duration: 1000 }))
              ,
              TransitionEffect.OPACITY.animation({ delay: 1000, duration: 1000 }).combine(
              TransitionEffect.rotate({ z: 1, angle: 180 }).animation({ duration: 1000 }))
            )
          )
        // 出现时做从x方向和y方向scale都为0变为默认的x方向和y方向scale都为1的动画，该动画时长为animateTo中指定的2000ms
        // 消失时无转场效果
        // $r('app.media.testImg')需要替换为开发者所需的图像资源文件。
        Image($r('app.media.testImg')).width(200).height(200).margin({ top: 100 })
          .transition(
            TransitionEffect.asymmetric(
              TransitionEffect.scale({ x: 0, y: 0 }),
              TransitionEffect.IDENTITY
            )
          )
      }
    }.width('100%')
  }
}
```
示意图：<br/>
![transitionComponent3](figures/transitionComponent3.gif)

### 示例3（设置父子组件为transition）

该示例主要演示通过父子组件都配置transition来实现图片的出现和消失。
```ts
// xxx.ets
@Entry
@Component
struct TransitionEffectExample3 {
  @State flag: boolean = true;
  @State show: string = 'show';

  build() {
    Column() {
      Button(this.show).width(80).height(30).margin(30)
        .onClick(() => {
          // 点击Button控制Image的显示和消失
          if (this.flag) {
            this.show = 'hide';
          } else {
            this.show = 'show';
          }
          this.flag = !this.flag;
        })
      if (this.flag) {
        // 改flag条件时，会触发id为"column1"、"image1"、"image2"的transition动画。
        // id为"column1"的组件是这棵新出现/消失的子树的根节点。
        Column() {
          Row() {
            // $r('app.media.testImg')需要替换为开发者所需的图像资源文件。
            Image($r('app.media.testImg')).width(150).height(150).id("image1")
              .transition(TransitionEffect.OPACITY.animation({ duration: 1000 }))
          }

          // $r('app.media.testImg')需要替换为开发者所需的图像资源文件。
          Image($r('app.media.testImg'))
            .width(150)
            .height(150)
            .margin({ top: 50 })
            .id("image2")
            .transition(TransitionEffect.scale({ x: 0, y: 0 }).animation({ duration: 1000 }))
          Text("view").margin({ top: 50 })
        }
        .id("column1")
        .transition(TransitionEffect.opacity(0.99).animation({ duration: 1000 }),
          // 结束回调设置在消失的第一层节点上，确保能有消失的结束回调
          (transitionIn: boolean) => {
            console.info("transition finish, transitionIn:" + transitionIn);
          }
        )
      }
    }.width('100%')
  }
}
```
示意图：<br/>
![transitionComponent4](figures/transitionComponent4.gif)

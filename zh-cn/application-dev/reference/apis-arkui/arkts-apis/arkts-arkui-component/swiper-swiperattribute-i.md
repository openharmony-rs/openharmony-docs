# SwiperAttribute

除支持[通用属性]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_外，还支持以下属性： > **说明：** > > Swiper组件通用属性\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_的默认值为 > true。

**继承/实现关系：** SwiperAttribute extends [CommonMethod](../../../apis-na/arkts-apis/arkts-na-component/common-commonmethod-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface SwiperAttribute extends CommonMethod--><!--Device-unnamed-export declare interface SwiperAttribute extends CommonMethod-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attributeModifier

```TypeScript
default attributeModifier(modifier: AttributeModifier<SwiperAttribute> | AttributeModifier<CommonMethod> | undefined): this
```

动态设置Swiper组件的属性方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default attributeModifier(modifier: AttributeModifier<SwiperAttribute> | AttributeModifier<CommonMethod> | undefined): this--><!--Device-SwiperAttribute-default attributeModifier(modifier: AttributeModifier<SwiperAttribute> | AttributeModifier<CommonMethod> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| AttributeModifier&lt;CommonMethod&gt; \| undefined | 是 | 在当前组件上，动态设置属 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## autoPlay

```TypeScript
default autoPlay(value: boolean | undefined): this
```

设置子组件是否自动播放。轮播方向为索引从小到大。 [loop]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_为false时，自动轮播到最后一页时停止轮播。手势切换完成后，如果当前页面不是最后一页，自动轮播将继续播放。当Swiper不可见时会停止轮播。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default autoPlay(value: boolean | undefined): this--><!--Device-SwiperAttribute-default autoPlay(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 | 子组件是否自动播放。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true：自动播放；false：不自动播放。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_传入非法值时，按false处理。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## autoPlay

```TypeScript
default autoPlay(autoPlay: boolean | undefined, options: AutoPlayOptions | undefined): this
```

设置子组件是否自动播放。options入参控制手指或鼠标按下屏幕时子组件是否停止自动播放。 当[loop]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_设置为false时，自动轮播将在到达最后一页时停止。在通过手势切换且未处于最后一页的情况下，轮播将继续进行。Swiper在不可见时，轮播也将停止。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default autoPlay(autoPlay: boolean | undefined, options: AutoPlayOptions | undefined): this--><!--Device-SwiperAttribute-default autoPlay(autoPlay: boolean | undefined, options: AutoPlayOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| autoPlay | boolean \| undefined | 是 | 子组件是否自动播放。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true：自动播放；false：不自动播放。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_传入非法值时，按false处理。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，按默认值处理。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 配置手指或鼠标按下屏幕时子组件是否停止自动播放。当stopWhenTouched设置为true时，多指按下场景中任意一个手指抬起后，将自动继续播放。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：{ stopWhenTouched: true }，停止自动播放。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## cachedCount

```TypeScript
default cachedCount(value: int | undefined): this
```

设置预加载子组件个数，以当前页面为基准，加载当前显示页面的前后个数。前面item删除，后面会向前补位。例如cachedCount=1时，会将当前显示页面在索引序号上相邻的前一页和后一页的子组件都预加载。如果设置为按组翻页，即 displayCount的swipeByGroup参数设为true，预加载时会以组为基本单位。例如cachedCount=1，swipeByGroup=true时，会将当前组的前面一组和后面一组的子组件都预加载。 > **说明：** > > - 在连续滑动场景中，一屏显示一个Swiper子组件时，通常将cachedCount值设置为1或2即可。最佳实践请参考 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ > 。 > > - 只在\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_和开启了virtualScroll开关的 > \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_中生效，生效后超出显示及缓存范围的子节点会被释放。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default cachedCount(value: int | undefined): this--><!--Device-SwiperAttribute-default cachedCount(value: int | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## cachedCount

```TypeScript
default cachedCount(count: int | undefined, isShown: boolean | undefined): this
```

设置预加载子组件个数。 > **说明：** > > - isShown值为true，且设置的count过大时，如果前后预加载范围内可加载的节点不足，循环场景下同一个可加载节点只会布局在一侧。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default cachedCount(count: int | undefined, isShown: boolean | undefined): this--><!--Device-SwiperAttribute-default cachedCount(count: int | undefined, isShown: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | int \| undefined | 是 | 预加载子组件个数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值范围：[0, +∞)，设置小于0的值时，按照默认值处理。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，按默认值处理。 |
| isShown | boolean \| undefined | 是 | 预加载范围内的节点是否进行绘制，不下渲染树。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true：预加载范围内的节点进行绘制；false：预加载范围内的节点不进行绘制。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_传入非法值以及undefined时，按false处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | the attribute of the swiper. |

## cachedCount

```TypeScript
default cachedCount(count: int | undefined, options: CachedCountOptions | undefined): this
```

设置预加载子组件个数和配置选项。 > **说明：** > > - 当options的independent设置为true时，预加载子组件个数按count个数计算，与 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_的分组swipeByGroup > 计算解耦。例如cachedCount的count为1时，会将当前显示子节点的前一个和后一个子组件预加载。 > > - 当displayCount的swipeByGroup参数设为true，且options的independent为false（默认值）时，预加载子组件个数以组为基本单位。例如cachedCount的count为1， > displayCount的value为2，displayCount的swipeByGroup为true时，会将当前显示组的前一组和后一组的各两个子组件预加载。 > > - 只在\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_和开启了virtualScroll开关的 > \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_中生效，生效后超出缓存范围的子节点会被释放。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default cachedCount(count: int | undefined, options: CachedCountOptions | undefined): this--><!--Device-SwiperAttribute-default cachedCount(count: int | undefined, options: CachedCountOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | int \| undefined | 是 | 预加载子组件个数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值范围：[0, +∞)，设置小于0的值时，按照1处理。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，按照1处理。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 预加载子组件的配置选项。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，按CachedCountOptions中的默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | the attribute of the swiper. |

## curve

```TypeScript
default curve(value: Curve | string | ICurve | undefined): this
```

设置Swiper的动画曲线，默认为弹簧插值曲线，常用曲线参考[Curve]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_，也可以通过 [插值计算]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_模块提供的接口创建自定义的插值曲线对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default curve(value: Curve | string | ICurve | undefined): this--><!--Device-SwiperAttribute-default curve(value: Curve | string | ICurve | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| string \| ICurve \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## customContentTransition

```TypeScript
default customContentTransition(transition: SwiperContentAnimatedTransition | undefined): this
```

自定义Swiper页面切换动画。在页面跟手滑动和离手后执行切换动画的过程中，会对视窗内所有页面逐帧触发回调，开发者可以在回调中设置透明度、缩放比例、位移等属性来自定义切换动画。 使用说明： 1、循环场景下，设置prevMargin和nextMargin属性，使得Swiper视窗的前后两端区域显示同一页面时，该接口不生效。 2、在页面跟手滑动和离手后执行切换动画的过程中，会对视窗内所有页面逐帧触发[SwiperContentTransitionProxy]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_回调。例如，当视窗内有下 标为0、1的两个页面时，会每帧触发两次index值分别为0和1的回调。 3、设置displayCount属性的swipeByGroup参数为true时，若同组中至少有一个页面在视窗内时，则会对同组中所有页面触发回调，若同组所有页面均不在视窗内时，则会一起下渲染树。 4、在页面跟手滑动和离手后执行切换动画的过程中，默认动画（页面滑动）依然会发生，若希望页面不滑动，可以设置主轴方向上负的位移（translate属性）来抵消页面滑动。例如：当displayCount属性值为2，视窗内有下标为0、1 的两个页面时，页面水平滑动过程中，可以逐帧设置第0页的translate属性在x轴上的值为-position * mainAxisLength来抵消第0页的位移，设置第1页的translate属性在x轴上的值为-(position - 1) * mainAxisLength来抵消第1页的位移。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default customContentTransition(transition: SwiperContentAnimatedTransition | undefined): this--><!--Device-SwiperAttribute-default customContentTransition(transition: SwiperContentAnimatedTransition | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transition | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Swiper自定义切换动画相关信息。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，不使用回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | the attribute of the swiper. |

## disableSwipe

```TypeScript
default disableSwipe(value: boolean | undefined): this
```

设置禁用组件滑动切换功能。适用于仅通过按钮或导航点控制翻页的场景，或需要限制用户滑动操作的场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default disableSwipe(value: boolean | undefined): this--><!--Device-SwiperAttribute-default disableSwipe(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## displayArrow

```TypeScript
default displayArrow(value: ArrowStyle | boolean | undefined, isHoverShow?: boolean | undefined): this
```

设置导航点箭头样式。 > **说明：** > > Swiper视窗内显示所有子节点时，只显示一屏，无法翻页，左右翻页箭头均不显示。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default displayArrow(value: ArrowStyle | boolean | undefined, isHoverShow?: boolean | undefined): this--><!--Device-SwiperAttribute-default displayArrow(value: ArrowStyle | boolean | undefined, isHoverShow?: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| boolean \| undefined | 是 | 支持设置箭头和底板样式，异常场景使用ArrowStyle对象中的默认值。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true：显示默认的箭头和底板样式；false：不显示箭头和底板。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：false\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，按默认值处理。 |
| isHoverShow | boolean \| undefined | 否 | 设置鼠标悬停时是否显示箭头。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：false\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true：有导航点时鼠标悬停在导航点和箭头范围内显示箭头，无导航点时鼠标悬停在Swiper显示范围内显示箭头；false：常驻显示箭头。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，按默认值处理。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**说明：**\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_箭头显示时，支持点击翻页。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | return the component attribute. |

## displayCount

```TypeScript
default displayCount(value: int | string | SwiperAutoFill | ItemFillPolicy| undefined, swipeByGroup?: boolean | undefined): this
```

设置Swiper视窗内元素显示个数。 使用number类型时，子元素主轴宽度会基于Swiper主轴宽度适应。子组件按照主轴均分Swiper宽度（减去displayCount-1个itemSpace）的方式进行主轴拉伸（收缩）布局，设置为小于等于0的值时，按默认值1显示 。 使用string类型时，根据子元素的主轴宽度线性布局，不再适应Swiper主轴宽度。此时value值仅支持设置为'auto'，设置 [customContentTransition]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_和 [onContentDidScroll]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_事件不生效。 使用SwiperAutoFill类型时，子元素主轴宽度会基于Swiper主轴宽度适应。通过设置一个子组件最小宽度值minSize，会根据Swiper当前宽度和minSize值自动计算并更改一页内元素显示个数。当minSize为空或 者小于等于0时，Swiper显示1列。 > **说明：** > > 1.按组进行翻页时，判定翻页的拖拽距离阈值将调整为Swiper宽度的50%（若按子元素翻页，该阈值为子元素宽度的50%）。若最后一组的子元素数量少于displayCount，将利用占位子元素进行填充，占位子元素仅用于布局定位， > 不显示任何内容，其位置将直接显示Swiper的背景样式。 > > 2.displayCount设置为'auto'，并且设置非循环时，选中导航点的位置与视窗内首个页面的位置保持一致。如果翻页完成后，视窗内首个页面仅部分显示在视窗内，选中导航点亦与页面的位置保持一致，位于两个未选中的导航点之间。 > 在此情况下，建议开发者隐藏导航点。 > > 3.导航点样式设定为圆形导航点，视窗内显示子元素数量等于1时（单页场景）或者 displayCount设置为'auto'时，显示导航点数量等于子元素数量。 > > 4.displayCount设置为'auto'时，若设置swipeByGroup为true，则单个子元素按组翻页，一次只能翻一页。在此情况下，建议开发者不设置swipeByGroup或者设置swipeByGroup为false > 。 当导航点样式设定为圆形导航点，视窗内显示子元素数量大于1（多页场景），显示导航点数量情况如下表： | 子元素总数量是否大于视窗内显示的子元素数量 | 是否按组翻页 | 是否循环 | 圆形导航点显示数量 | 说明 | | ------------------------------------------ | ------------ | --------------- | ----------------------------------- ------------------------- | ---------------------------------------- | | 是 | 是 | loop设置为true | 圆形导航点的数量将与组数相等（组数计算方式为子元素总数量除以视窗内显示的子元素数 量，若除不尽，则向上取整） | 该效果在displayCount设置为'auto'时不生效 | | 是 | 是 | loop设置为false | 圆形导航点的数量将与组数相等（组数计算方式为子元素总数量除以视窗内显示的子元素数 量，若除不尽，则向上取整） | 该效果在displayCount设置为'auto'时不生效 | | 是 | 否 | loop设置为true | 圆形导航点的数量将与实际可翻页次数一致（显示导航点的数量等于子元素总数量） | —— | | 是 | 否 | loop设置为false | 圆形导航点的数量将与实际可翻页次数一致（计算方式是子元素的总 数量减去视窗内显示的子元素数量+1个） | 该效果在displayCount设置为'auto'时不生效 | | 否（同时子元素的总数量大于0） | —— | —— | 显示1个圆形导航点 | 该效果在 displayCount设置为'auto'时不生效 | | 否（同时子元素的总数量等于0） | —— | —— | 显示0个圆形导航点 | —— |

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default displayCount(value: int | string | SwiperAutoFill | ItemFillPolicy| undefined, swipeByGroup?: boolean | undefined): this--><!--Device-SwiperAttribute-default displayCount(value: int | string | SwiperAutoFill | ItemFillPolicy| undefined, swipeByGroup?: boolean | undefined): this-End-->

**系统能力：** 
- API版本23+：SystemCapability.ArkUI.ArkUI.Full
- API版本23+：SystemCapability.ArkUI.ArkUI.Full
- API版本23+：SystemCapability.ArkUI.ArkUI.Full
- SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int \| string \| SwiperAutoFill \| ItemFillPolicy \| undefined | 是 | 视窗内显示的子元素个数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 默认值：1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值范围：(0,+∞)，设置小于等于0的值时，按照1处理。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，按默认值处理。\_\_\_HTML\_TAG\_USD\_0\_\_\_**起始版本：** 24 |
| swipeByGroup | boolean \| undefined | 否 | if swipe by group.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_Default value: false\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true: The page is turned by group. The number of subelements in each group is the value of displayCount.false: The default page turning behavior is used. That is, pages are turned based on subelements. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## displayMode

```TypeScript
default displayMode(value: SwiperDisplayMode | undefined): this
```

设置主轴方向上元素排列的模式，优先以\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 设置的个数显示，displayCount未设置时本属性生效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default displayMode(value: SwiperDisplayMode | undefined): this--><!--Device-SwiperAttribute-default displayMode(value: SwiperDisplayMode | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## duration

```TypeScript
default duration(value: int | undefined): this
```

设置子组件切换的动画时长。 duration需要和[curve]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_一起使用。 curve默认曲线为[interpolatingSpring]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_，此时动画时长只受曲线自身参数影响，不再受duration 的控制。不受duration控制的曲线可以查阅[插值计算]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_模块，比如， [springMotion]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_、 [responsiveSpringMotion]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_和interpolatingSpring类型的曲线不受 duration控制。如果希望动画时长受到duration控制，需要给curve设置其他曲线。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default duration(value: int | undefined): this--><!--Device-SwiperAttribute-default duration(value: int | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## effectMode

```TypeScript
default effectMode(value: EdgeEffect | undefined): this
```

设置边缘滑动效果，[loop]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_为false或Swiper视窗内一屏显示所有子节点时生效。调用 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 、[SwiperController.showNext()]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_和 [SwiperController.showPrevious()]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_接口跳转至首尾页时不生效回弹。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default effectMode(value: EdgeEffect | undefined): this--><!--Device-SwiperAttribute-default effectMode(value: EdgeEffect | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## index

```TypeScript
default index(value: int | Bindable<int> | undefined): this
```

设置当前在容器中显示的子组件的索引值。设置小于0或大于等于子组件数量时，按照默认值0处理。 从API version 10开始，该属性支持\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_双向绑定变量。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default index(value: int | Bindable<int> | undefined): this--><!--Device-SwiperAttribute-default index(value: int | Bindable<int> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int \| Bindable&lt;int&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## indicator

```TypeScript
default indicator(indicator: IndicatorComponentController | DotIndicator | DigitIndicator | boolean | undefined): this
```

设置可选导航点指示器样式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default indicator(indicator: IndicatorComponentController | DotIndicator | DigitIndicator | boolean | undefined): this--><!--Device-SwiperAttribute-default indicator(indicator: IndicatorComponentController | DotIndicator | DigitIndicator | boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| indicator | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| DotIndicator \| DigitIndicator \| boolean \| undefined | 是 | 可选导航点指示器样式。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- IndicatorComponentController：单独导航点指示器控制器。当使用单独导航点指示器控制器时，可以与外部单独导航点进行绑定，但是绑定的单独导航点和内置导航点不能同时存在。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ -DotIndicator：圆点指示器样式。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ - DigitIndicator：数字指示器样式。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ - boolean：是否启用导航点指示器。设置为true启用，false不启用。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：true\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认类型：DotIndicator。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_6\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true：启用导航点指示器；false：不启用导航点指示器。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_7\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## indicatorInteractive

```TypeScript
default indicatorInteractive(value: boolean | undefined): this
```

设置导航点是否可交互。适用于需要通过其他方式（如按钮）控制翻页，或需要禁止用户通过导航点点击翻页的场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default indicatorInteractive(value: boolean | undefined): this--><!--Device-SwiperAttribute-default indicatorInteractive(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 | 导航点是否可交互。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true：导航点可交互；false：导航点不可交互。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_传入参数非法时，按true处理。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，按true处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## interval

```TypeScript
default interval(value: int | undefined): this
```

设置使用自动播放时播放的时间间隔。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default interval(value: int | undefined): this--><!--Device-SwiperAttribute-default interval(value: int | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | int \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## itemSpace

```TypeScript
default itemSpace(value: double | string | undefined): this
```

设置子组件与子组件之间间隙。不支持设置百分比。 类型为number或double时，默认单位vp。类型为string时，需要显式指定像素单位，如'10px'；未指定像素单位时，如'10'，单位为vp。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default itemSpace(value: double | string | undefined): this--><!--Device-SwiperAttribute-default itemSpace(value: double | string | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double \| string \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## loop

```TypeScript
default loop(value: boolean | undefined): this
```

设置是否开启循环。在LazyForEach懒循环加载模式下，加载的组件数量建议大于5个。预加载的组件数量不足时，可能会导致快速切换时出现空白或卡顿。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default loop(value: boolean | undefined): this--><!--Device-SwiperAttribute-default loop(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## maintainVisibleContentPosition

```TypeScript
default maintainVisibleContentPosition(enabled: boolean | undefined): this
```

设置显示区域上方或前方插入或删除数据时是否保持可见内容位置不变。适用于使用单一 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_作为Swiper子节点的情况，通过LazyForEach的 [onDataAdd]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_、 [onDataDelete]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_等接口修改数据源。其他场景下，显 示区域上方或前方插入或删除数据，可见内容位置会变化。 在\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_属性的swipeByGroup参数 设置为true，即按组翻页生效时，一次在显示区域上方或前方插入或删除数据，且插入或删除的是一组节点数量倍数的数据量时，才能保持可见内容位置不变，否则可见内容位置可能会随每组数据重新分组改变。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default maintainVisibleContentPosition(enabled: boolean | undefined): this--><!--Device-SwiperAttribute-default maintainVisibleContentPosition(enabled: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean \| undefined | 是 | 设置显示区域上方或前方插入或删除数据时是否要保持可见内容位置不变。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：false，显示区域上方或前方插入或删除数据时可见内容位置会跟随变化。 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true：显示区域上方或前方插入或删除数据时可见内容位置不变。如果改变数据源是在动画过程中，由于目标索引变化会导致动画停止。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | -the attribute of swiper. |

## nestedScroll

```TypeScript
default nestedScroll(value: SwiperNestedScrollMode | undefined): this
```

设置Swiper组件和父组件的嵌套滚动模式。当Swiper嵌套在滚动容器（如List、Scroll）中时，需要根据业务需求选择合适的嵌套滚动模式。[loop]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_为true时Swiper组件没有边缘，不会触发父组件嵌套滚动。 > **说明：** > > 由于Swiper的抛滑动画逻辑和其它滚动类组件不同（Swiper一次只能滑动一页，抛滑时做翻页动画），当Swiper内嵌套其它滚动组件时，如果Swiper的翻页动画已经启动，将无法接受子节点上传的滚动偏移量。这时Swiper的 > 翻页动画和子节点的边缘效果动画会同时执行。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default nestedScroll(value: SwiperNestedScrollMode | undefined): this--><!--Device-SwiperAttribute-default nestedScroll(value: SwiperNestedScrollMode | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Swiper组件和父组件的嵌套滚动模式。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：SwiperNestedScrollMode.SELF\_\_\_ESCAPED\_UNDERSCORE\_\_\_ONLY\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | the attribute of the swiper. |

## nextMargin

```TypeScript
default nextMargin(value: Length | undefined, ignoreBlank?: boolean | undefined): this
```

当主轴方向为横向布局时，nextMargin或prevMargin中任意一个大于子组件测算的宽度，nextMargin和prevMargin均不显示。 当主轴方向为纵向布局时，nextMargin或prevMargin中任意一个大于子组件测算的高度，nextMargin和prevMargin均不显示。 使用nextMargin/prevMargin接口时，不要对子组件进行 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_，否则子节点主轴将不会被拉伸到预期长度 ，边距失去效果。 > **说明：** > > 该接口不支持在 > \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_ > 中调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default nextMargin(value: Length | undefined, ignoreBlank?: boolean | undefined): this--><!--Device-SwiperAttribute-default nextMargin(value: Length | undefined, ignoreBlank?: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 后边距。不支持设置百分比。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_按默认值处理。 |
| ignoreBlank | boolean \| undefined | 否 | 非loop场景下尾页不显示nextMargin。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true：尾页不显示空白的nextMargin，尾页的右边缘与Swiper视窗右边缘对齐；false：尾页显示空白nextMargin，尾页的右边缘与Swiper视窗右边缘的距离为nextMargin。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值： false。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_按默认值处理.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_4\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_**说明：**\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_5\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_尾页场景下，prevMargin和nextMargin的值相加作为左边边距显示前一个页面。 默认值： false。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | The attribute of the swiper. |

## onAnimationEnd

```TypeScript
default onAnimationEnd(event: OnSwiperAnimationEndCallback | undefined): this
```

切换动画结束时触发该回调。 当Swiper切换动效结束时触发，包括动画过程中手势中断，通过SwiperController调用finishAnimation。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default onAnimationEnd(event: OnSwiperAnimationEndCallback | undefined): this--><!--Device-SwiperAttribute-default onAnimationEnd(event: OnSwiperAnimationEndCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onAnimationStart

```TypeScript
default onAnimationStart(event: OnSwiperAnimationStartCallback | undefined): this
```

切换动画开始时触发该回调。 > **说明：** > > - 调用此回调后，切换动画的逻辑将在渲染线程中执行，从而使处于空闲状态的主线程能够充分利用这段时间来加载子组件所需资源，减少后续在cachedCount范围内节点的预加载时间。最佳实践请参考 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ > 。 > > - 当翻页动画时长为0时，只有以下场景会触发该回调：滑动翻页、自动轮播、调用SwiperController.showNext()和SwiperController.showPrevious()接口以及手指点击导航点翻页。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default onAnimationStart(event: OnSwiperAnimationStartCallback | undefined): this--><!--Device-SwiperAttribute-default onAnimationStart(event: OnSwiperAnimationStartCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onChange

```TypeScript
default onChange(event: Callback<int> | undefined): this
```

当前显示元素索引变化时触发该事件，返回值为当前显示元素的索引值。 Swiper组件结合LazyForEach使用时，不能在onChange事件里触发子页面UI的刷新。 > **说明：** > > 如果是动画引起的索引变化，回调在动画结束时触发。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default onChange(event: Callback<int> | undefined): this--><!--Device-SwiperAttribute-default onChange(event: Callback<int> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;int&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onContentDidScroll

```TypeScript
default onContentDidScroll(handler: ContentDidScrollCallback | undefined): this
```

监听Swiper页面滑动事件。 使用说明： 1、循环场景下，设置prevMargin和nextMargin属性，使得Swiper视窗的前后两端区域显示同一页面时，该接口不生效。 2、在页面滑动过程中，会对视窗内所有页面逐帧触发[ContentDidScrollCallback]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_回调。例如，当视窗内有下标为0、1的两个页面时，会每帧触发两次 index值分别为0和1的回调。 3、设置displayCount属性的swipeByGroup参数为true时，若同组中至少有一个页面在视窗内时，则会对同组中所有页面触发回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default onContentDidScroll(handler: ContentDidScrollCallback | undefined): this--><!--Device-SwiperAttribute-default onContentDidScroll(handler: ContentDidScrollCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Swiper滑动时触发的回调。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，不使用回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | the attribute of the swiper. |

## onContentWillScroll

```TypeScript
default onContentWillScroll(handler: ContentWillScrollCallback | undefined): this
```

Swiper滑动行为拦截事件，在滑动前触发。Swiper会依据该事件的返回值来决定是否允许此次滑动行为。若返回true，表示允许此次滑动行为，Swiper页面将跟随滑动。若返回false，表示不允许此次滑动，页面将保持静止。 1. 触发该事件的场景仅限于手势操作，具体包括手指滑动、滚动鼠标滚轮以及使用键盘方向键进行焦点移动。 2. 在手指滑动的过程中，每帧都将触发该事件，系统会依据事件的返回值判断是否对每帧的滑动做出响应。 3. 对于滚动鼠标滚轮和使用键盘方向键进行焦点移动的场景，每次翻页操作都会触发一次该事件，翻页是否被允许将根据事件的返回值来决定。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default onContentWillScroll(handler: ContentWillScrollCallback | undefined): this--><!--Device-SwiperAttribute-default onContentWillScroll(handler: ContentWillScrollCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | Swiper滑动时触发的回调。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，不使用回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | the attribute of the swiper. |

## onGestureSwipe

```TypeScript
default onGestureSwipe(event: OnSwiperGestureSwipeCallback | undefined): this
```

在页面跟手滑动过程中，逐帧触发该回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default onGestureSwipe(event: OnSwiperGestureSwipeCallback | undefined): this--><!--Device-SwiperAttribute-default onGestureSwipe(event: OnSwiperGestureSwipeCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onScrollStateChanged

```TypeScript
default onScrollStateChanged(event: Callback<ScrollState> | undefined): this
```

Swiper滑动状态变化事件回调，在跟手滑动、离手动画、停止三种滑动状态变化时触发，返回值为当前滑动状态。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default onScrollStateChanged(event: Callback<ScrollState> | undefined): this--><!--Device-SwiperAttribute-default onScrollStateChanged(event: Callback<ScrollState> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| undefined | 是 | 滑动状态变化的回调。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，不使用回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | -this |

## onSelected

```TypeScript
default onSelected(event: Callback<int> | undefined): this
```

当选中元素改变时触发该回调，返回值为当前选中的元素的索引值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default onSelected(event: Callback<int> | undefined): this--><!--Device-SwiperAttribute-default onSelected(event: Callback<int> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;int&gt; \| undefined | 是 | 当前选中元素的索引。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，不使用回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onUnselected

```TypeScript
default onUnselected(event: Callback<int> | undefined): this
```

当选中元素改变时触发该回调，返回值为将要隐藏的元素的索引值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default onUnselected(event: Callback<int> | undefined): this--><!--Device-SwiperAttribute-default onUnselected(event: Callback<int> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;int&gt; \| undefined | 是 | 将要隐藏元素的索引。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值为undefined时，不使用回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## pageFlipMode

```TypeScript
default pageFlipMode(mode: PageFlipMode | undefined): this
```

设置鼠标滚轮翻页模式。未通过该接口设置时，默认为连续翻页模式，取值为PageFlipMode.CONTINUOUS。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default pageFlipMode(mode: PageFlipMode | undefined): this--><!--Device-SwiperAttribute-default pageFlipMode(mode: PageFlipMode | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | page flip mode on mouse wheel event. The default value is PageFlipMode.CONTINUOUS. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## prevMargin

```TypeScript
default prevMargin(value: Length | undefined, ignoreBlank?: boolean | undefined): this
```

设置前边距，用于露出前一项的一小部分，使用效果可以参考 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。仅当Swiper子组件的 布局方式为拉伸时生效，主要包括两种场景：1、displayMode属性设置为SwiperDisplayMode.STRETCH；2、displayCount属性设置为number类型。 当主轴方向为横向布局时，nextMargin/prevMargin中任意一个大于子组件测算的宽度，nextMargin和prevMargin均不显示。 当主轴方向为纵向布局时，nextMargin/prevMargin中任意一个大于子组件测算的高度，nextMargin和prevMargin均不显示。 使用nextMargin/prevMargin接口时，不要对子组件进行 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_，否则子节点主轴将不会被拉伸到预期长度 ，边距失去效果。 > **说明：** > > 该接口不支持在 > \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_ > 中调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default prevMargin(value: Length | undefined, ignoreBlank?: boolean | undefined): this--><!--Device-SwiperAttribute-default prevMargin(value: Length | undefined, ignoreBlank?: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 前边距。不支持设置百分比。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_按默认值处理。 |
| ignoreBlank | boolean \| undefined | 否 | 非loop场景下首页不显示prevMargin。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true：首页不显示空白的prevMargin，首页的左边缘与Swiper视窗左边缘对齐；false：首页显示空白prevMargin，首页的左边缘与Swiper视窗左边缘的距离为prevMargin。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值： false。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | The attribute of the swiper. |

## setSwiperOptions

```TypeScript
default setSwiperOptions(controller?: SwiperController): this
```

设置滑动器选项。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default setSwiperOptions(controller?: SwiperController): this--><!--Device-SwiperAttribute-default setSwiperOptions(controller?: SwiperController): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Swiper构造函数选项 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回SwiperAttribute的实例。 |

## vertical

```TypeScript
default vertical(value: boolean | undefined): this
```

设置是否为纵向滑动。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperAttribute-default vertical(value: boolean | undefined): this--><!--Device-SwiperAttribute-default vertical(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |


# swiper
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Hu_ZeQi-->
<!--Designer: @jiangdayuan-->
<!--Tester: @Giacinta-->
<!--Adviser: @Brilliantry_Rui-->


The **\<swiper>** component provides a container that allows users to switch among child components using swipe gestures.


> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.



## Attributes

In addition to the [universal attributes](js-service-widget-common-attributes.md), the following attributes are supported.

| Name       | Type     | Default Value  | Mandatory  | Description                                      |
| --------- | ------- | ----- | ---- | ---------------------------------------- |
| index     | number  | 0     | No   | Index of the child component currently displayed in the container.                       |
| indicator | boolean | true  | No   | Whether to enable the indicator. The value **true** indicates that the indicator is enabled, and **false** indicates the opposite. The default value is **true**.                      |
| digital   | boolean | false | No   | Whether to enable the digital indicator. The value **true** indicates that the digital indicator is enabled, and **false** indicates the opposite. The default value is **false**.<br>The digital indicator takes effect only when **indicator** is set to **true**.|
| loop      | boolean | true  | No   | Whether to enable looping. The value **true** indicates that looping is enabled, and **false** indicates the opposite.                               |
| duration  | number  | 0     | No   | Duration of the autoplay for child component switching.<br>Unit: ms<br>Value range: [0, +∞)                             |
| vertical  | boolean | false | No   | Whether vertical swiping is used. The value **true** means vertical swiping, and **false** means horizontal swiping. Use a vertical indicator for vertical swiping.                  |


## Styles

In addition to the [universal styles](js-service-widget-common-styles.md), the following styles are supported.

| Name                                | Type                                      | Default Value | Mandatory  | Description                  |
| ---------------------------------- | ---------------------------------------- | ---- | ---- | -------------------- |
| indicator-color                    | &lt;color&gt;                            | -    | No   | Fill color of the indicator.        |
| indicator-selected-color           | &lt;color&gt;                            | -    | No   | Color of the currently selected indicator.        |
| indicator-size                     | &lt;length&gt;                           | 4px  | No   | Diameter of the indicator.        |
| indicator-top\|left\|right\|bottom | &lt;length&gt;&nbsp;\|&nbsp;&lt;percentage&gt; | -    | No   | Relative position of the indicator in the swiper.|


## Events

The [universal events](js-service-widget-common-events.md) are supported.


## Example


```html
<!-- xxx.hml -->
<swiper class="container" index="{{index}}">
  <div class="swiper-item primary-item">
    <text>1</text>
  </div>
  <div class="swiper-item warning-item">
    <text>2</text>
  </div>
  <div class="swiper-item success-item">
    <text>3</text>
  </div>
</swiper>
```


```css
/* xxx.css */
.container {
  left: 0px;
  top: 0px;
  width: 454px;
  height: 454px;
}
.swiper-item {
  width: 454px;
  height: 454px;
  justify-content: center;
  align-items: center;
}
.primary-item {
  background-color: #007dff;
}
.warning-item {
  background-color: #ff7500;
}
.success-item {
  background-color: #41ba41;
}
```


```json
{
  "data": {
    "index": 1
  }
}
```
**4 x 4 widget**

![swiper](figures/swiper.png)

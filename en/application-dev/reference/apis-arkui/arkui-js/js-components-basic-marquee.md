# marquee
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hddgzw-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=87f36412b9792c0776f707878176294c4360c8f0 translatedAt=2026-11-12T04:15:58.075Z pushedAt=2026-11-12T06:42:27.813Z nl=1 -->

>  **NOTE**
>
>  This component is supported since API version 4. Updates will be marked with a superscript to indicate their earliest API version.
>  Since API version 6, the text scrolls only when its width exceeds the width of the **\<marquee>** component.

The **\<marquee>** component is used to display a scrolling piece of text.

## Required Permissions

None


## Child Components

Not supported


## Attributes

In addition to the [universal attributes](js-components-common-attributes.md), the following attributes are supported.

| Name          | Type    | Default Value | Mandatory  | Description                                      |
| ------------ | ------ | ---- | ---- | ---------------------------------------- |
| scrollamount | number | 6    | No    | Step length of each scroll.                         |
| loop         | number | -1   | No    | Number of times the marquee scrolls. If not specified, the default value is **-1**. When the value is less than or equal to 0, the marquee scrolls continuously. |
| direction    | string | left | No   | Direction in which the marquee scrolls, which can be **left** or **right**.            |


## Styles

In addition to the [universal styles](js-components-common-styles.md), the following styles are supported.

| Name         | Type                        | Default Value       | Mandatory  | Description                                      |
| ----------- | -------------------------- | ---------- | ---- | ---------------------------------------- |
| color       | &lt;color&gt;              | \#e5000000 | No   | Font color of the scrolling text.                          |
| font-size   | &lt;length&gt;             | 37.5       | No   | Font size of the scrolling text.                          |
| allow-scale | boolean                    | true       | No   | Whether the font size changes with the system's font size settings.<br>If the **config-changes** tag of **fontSize** is configured for abilities in the **config.json** file, the setting takes effect without application restart.|
| font-weight | number \| string | normal     | No   | Font weight of the scrolling text. For details, see **font-weight** of the **[\<text> component](js-components-basic-text.md#styles)**.|
| font-family | string                     | sans-serif | No   | Font family, in which fonts are separated by commas (,). Each font is set using a font name or font family name. The first font in the family or the specified [custom font](js-components-common-customizing-font.md) is used for the text.|


## Events

In addition to the [universal events](js-components-common-events.md), the following events are supported.

| Name    | Parameter  | Description                                      |
| ------ | ---- | ---------------------------------------- |
| bounce | -    | Triggered when the marquee scrolls to the end.                         |
| finish | -    | Triggered when the marquee finishes the specified number of scrollings (value of the **loop** attribute). It can be triggered only when the **loop** attribute is set to a number greater than 0.|
| start  | -    | Triggered when the marquee starts to scroll.                          |

## Methods

In addition to the [universal methods](js-components-common-methods.md), the following methods are supported.

| Name   | Parameter  | Description   |
| ----- | ---- | ----- |
| start | -    | Starts scrolling.|
| stop  | -    | Stops scrolling.|


## Example

```html
<!-- xxx.hml -->
<div class="tutorial-page">
    <div class="myMarquee">
        <marquee  style="color: {{color1}}" loop="{{loopVal}}" scrollamount="{{scroll}}" direction="{{isLeft}}" class="marqueeText"
                  id="testMarquee" onfinish="setFinish">
            Life is a journey, not the destination.
        </marquee>
    </div>
    <div style="width: 600px;height: 150px;flex-direction: row;justify-content: space-around;">
        <button onclick="makeStart"  value="start"></button>
        <button onclick="makeStop" value="stop"></button>
    </div>
</div>
```

```css
/* xxx.css */
.tutorial-page {
  width: 750px;
  height: 100%;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.marqueeText {
  font-size: 40px;
}
.myMarquee {
  margin-top: 20px;
  width:100%;
  height: 100px;
  margin-left: 50px;
  margin-right: 50px;
  border: 1px solid #dc0f27;
  border-radius: 15px;
  align-items: center;
}
button{
  width: 200px;
  height: 80px;
  margin-top: 100px;
}
```

```js
// xxx.js
export default {
    private: {
        loopVal: 1,
        scroll: 8,
        color1: 'red',
        isLeft: 'left',
        r: 255,
        g: 0,
        b: 0
    },
    onInit(){
    },
    setFinish(e) {
        this.loopVal=  this.loopVal + 1,
        this.r = Math.floor(Math.random()*255),
        this.g = Math.floor(Math.random()*255),
        this.b = Math.floor(Math.random()*255),
        this.color1 = 'rgba('+ this.r +','+ this.g +','+ this.b +',0.8)',
        this.$element('testMarquee').start(),
        this.loopVal=  this.loopVal - 1
    },
    makeStart(e) {
        this.$element('testMarquee').start()
    },
    makeStop(e) {
        this.$element('testMarquee').stop()
    }
}
```

![marquee](figures/marquee.gif)



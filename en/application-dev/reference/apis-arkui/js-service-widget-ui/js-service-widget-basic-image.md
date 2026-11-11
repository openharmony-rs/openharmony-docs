# image
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=88508a7bb30626a1ee5afb54e6f736edb0f144ed translatedAt=2026-11-10T07:55:03.743Z pushedAt=2026-11-10T10:58:16.560Z nl=1 -->

The **\<image>** component is used to render and display images.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.

## Child Components

Not supported.


## Attributes

In addition to the [universal attributes](js-service-widget-common-attributes.md), the following attributes are supported.

| Name| Type| Default Value| Mandatory| Description|
| -------- | -------- | -------- | -------- | -------- |
| src | string | - | No| Image path.<br>- The local path is supported. Supported formats are as follows: PNG, JPG, BMP, SVG, and GIF.<br>- The path to the in-memory image is also supported in the format of **memory://**.<br>**NOTE**<br>To display an online image, download it and then access it with its in-memory path. Do not use URLs.|
| alt | string | - | No| Placeholder image displayed during image loading.|


## Styles

In addition to the [universal styles](js-service-widget-common-styles.md), the following styles are supported.

| Name| Type| Default Value| Mandatory| Description|
| -------- | -------- | -------- | -------- | -------- |
| object-fit | string | cover | No| Image scale type. For details about available values, see **object-fit**. This style is not supported for SVG images.|
| match-text-direction | boolean | false | No| Whether image orientation changes with the text direction. This style is not supported for SVG images.<br>The default value is **false**, indicating that image orientation does not change with the text direction.|
| fit-original-size | boolean | false | No| Whether the [\<image>](js-service-widget-basic-image.md) component adapts to the image source size when its width and height are not set. If this style is set to **true**, **object-fit** will not take effect. This style is not supported for SVG images.<br>The default value is **false**, indicating that the [\<image>](js-service-widget-basic-image.md) component does not adapt to the image source size when its width and height are not set.|

  **Table 1** object-fit

| Type| Description|
| -------- | -------- |
| cover | The image is scaled with its aspect ratio retained for both sides to be greater than or equal to the display boundaries and displayed in the middle.|
| contain | The image is scaled with the aspect ratio retained for the image to be completely displayed within the display boundaries and displayed in the middle.|
| fill | The image is scaled to fill the display area, and its aspect ratio is not retained.|
| none | The image is displayed in the middle with its aspect ratio and size retained.|
| scale-down | The image is displayed in the middle with its aspect ratio retained. The size is equal to or smaller than the original size.|

>  **NOTE**
>  When an SVG image resource is used:
>
>  - It is recommended that you set the width and height of the image component. Otherwise, the SVG resource will not be drawn if the width or height of the parent component is infinite.
>
>  - If the width and height are not specified in the SVG description, the SVG will fill the area of the image component.
>
>  - If the width and height are specified in the SVG description, the width and height of the image component take effect as follows:
>
>    - If the width and height of the image component are smaller than those in the SVG, the SVG will be clipped and only the upper left corner will be displayed.
>
>    - If the width and height of the image component are larger than those in the SVG, the SVG will be placed in the upper left corner of the image component, and the rest of the image component will be blank.


## Events

| Name| Parameter| Description|
| -------- | -------- | -------- |
| click | - | Triggered when the component is clicked.|
| complete | - | Triggered when an image is successfully loaded.|
| error | - | Triggered when an exception occurs during image loading.|


## Example


```html
<!-- xxx.hml -->
<stack class="content">
    <image src="/common/bg3.jpg" class="img"></image>
</stack>
```


```css
/* xxx.css */
.img{  
  object-fit: contain
}
```
**4 x 4 widget**

![image.jpg](figures/image.jpg)


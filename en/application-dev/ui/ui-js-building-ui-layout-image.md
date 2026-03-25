# Adding an Image
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

Images are commonly implemented using the [\<image>](../reference/apis-arkui/arkui-js/js-components-basic-image.md)component, whose usage is similar to that of the [\<text>](../reference/apis-arkui/arkui-js/js-components-basic-text.md) component.

It is recommended that you place image resources in the **js/default/common** directory. Note that the **common** directory must be created manually. For details about directory structure, see [Directory Structure](js-framework-file.md#directory-structure). The sample code is as follows:

```html
<!-- xxx.hml -->
<image class="img" src="{{middleImage}}"></image>
```


```css
/* xxx.css */
.img {  
  margin-top: 30px;
  margin-bottom: 30px;
  height: 385px;
}
```


```js
// xxx.js
export default {
  data: {
    middleImage: '/common/ice.png',
  },
}
```

# Custom Font Styles
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hddgzw-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=214e29279f37b00be7bd8f1096b2e4dc3af96177 translatedAt=2026-11-12T04:22:30.274Z pushedAt=2026-11-17T11:16:36.825Z nl=1 -->

The custom font can be loaded from the font file in a project. The font file must be in .ttf or .otf format.

>  **NOTE**
>
>  This component is supported since API version 4. Updates will be marked with a superscript to indicate their earliest API version.


## Defining @font-face

```js
/* xxx.css */
@font-face {   
  font-family: font; 
  src: url('/common/font.ttf'); 
}
```

**font-family**

Customize a font.

**src**

Supported sources of custom fonts:

- Font file in the project: specify the path of the font file in the project through **url** (only absolute paths are supported; for details, see [File Access Rules](../../../ui/js-framework-file.md#file-access-rules)).

- You can set only one **src** attribute.


## Using font-face

You can set **font-face** in **style** and specify the name of the **font-face** using **font-family**.

**Example**

Page layout:
```html
<!-- xxx.hml -->
<div>    
  <text class="demo-text">Test the custom font.</text>  
</div>
```

Page style:

```css
/*xxx.css*/
@font-face {
  font-family: font;
  src: url("/common/font.ttf");
}
.demo-text {
  font-family: font;
}
```

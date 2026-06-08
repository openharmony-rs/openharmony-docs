# Custom Font Styles

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=7b6b884ef565767a6c9d0d7139fb4cb24a435447 translatedAt=2026-06-05T10:28:31.891Z pushedAt=2026-06-08T03:48:27.903Z -->

**font-face** is used to define the font style. You can define **font-face** in **style** to specify a font name and resource for your application and then reference this font from **font-family**.

The custom font can be loaded from the font file in a project or a network font file.

> **NOTE**
>
> This feature is supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> The font format can be .ttf or .otf.

## Defining @font-face

```css
@font-face {   
  font-family: HWfont; 
  src: url('/common/HWfont.ttf'); 
}
```

**font-family**: name of the custom font.

**src**: source of the custom font, which can be a font file in the project or an online font file.

- Font file in the project: Specify the absolute path of the font file in the project through **url**. For details, see [File Organization](js-service-widget-file.md).

- Online font file: Specify the address of the online font through **url**.

- You can set only one **src** attribute.

## Using font-face

You can set **font-face** in **style** and specify the name of the **font-face** using **font-family**. The code snippet is as follows:

- Page layout

  ```html
  <div>    
    <text class="demo-text">Test the custom font.</text>  
  </div>
  ```

- Page style

  ```css
  @font-face {
    font-family: HWfont;
    src: url("/common/HWfont.ttf");
  }
  .demo-text {
    font-family: HWfont;
  }
  ```
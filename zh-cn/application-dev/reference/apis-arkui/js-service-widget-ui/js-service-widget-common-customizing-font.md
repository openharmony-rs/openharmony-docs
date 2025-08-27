# 自定义字体样式
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6-->
<!--Designer: @pssea-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @HelloCrease-->


font-face用于定义字体样式。应用可以在style中定义font-face来指定相应的字体名和字体资源，然后在font-family样式中引用该字体。


自定义字体可以是从项目中的字体文件或网络字体文件中加载的字体。

> **说明：**
>
> 从API Version 8 开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> 字体格式支持ttf和otf。


## 定义font-face


```css
@font-face {   
  font-family: HWfont; 
  src: url('/common/HWfont.ttf'); 
}
```
 
**font-family：** 自定义字体的名称。

**src：** 自定义字体的来源，支持如下类别。

- 项目中的字体文件：通过url指定项目中的字体文件路径(只支持绝对路径，详见[文件组织](js-service-widget-file.md))。

- 网络字体文件：通过url指定网络字体的地址。

- 不支持设置多个src。


## 使用font-face

可以在style中定义font-face，然后在font-family样式中指定该font-face的名称，从而应用font-face定义的字体。示例如下：

- 页面布局
  
  ```html
  <div>    
    <text class="demo-text">测试自定义字体</text>  
  </div>
  ```

- 页面样式
  
  ```css
  @font-face {
    font-family: HWfont;
    src: url("/common/HWfont.ttf");
  }
  .demo-text {
    font-family: HWfont;
  }
  ```

# 自定义字体样式
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hddgzw-->
<!--Designer: @pssea-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @HelloCrease-->

自定义字体可以是从项目中的字体文件中加载的字体，字体格式支持ttf和otf。

>  **说明：**
>
>  从API version 4开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。


## 定义font-face

```
@font-face {   
  font-family: font; 
  src: url('/common/font.ttf'); 
}
```

**font-family：**

自定义字体的名称。

**src：**

自定义字体的来源，支持如下类别：

- 项目中的字体文件：通过url指定项目中的字体文件路径(只支持绝对路径，详见[资源和文件访问规则](../../../ui/js-framework-file.md)章节)。

- 不支持设置多个src。


## 使用font-face

可以在style中定义font-face，然后在font-family样式中指定该font-face的名称，从而应用font-face定义的字体。

**示例：**

页面布局：
```html
<!-- xxx.hml -->
<div>    
  <text class="demo-text">测试自定义字体</text>  
</div>
```

页面样式：

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

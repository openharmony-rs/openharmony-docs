# 文件组织
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @HelloCrease-->

## 目录结构

JS服务卡片(entry/src/main/js/Widget)的典型开发目录结构如下：

```
├─widget
│   ├─common
│   │   └─widget.png
│   ├─i18n
│   │   ├─en-US.json
│   │   └─zh-CN.json
│   └─pages
│       └─index
│           ├─index.css
│           ├─index.hml
│           └─index.json  
```

目录结构中文件分类如下：

- .hml结尾的HML模板文件，这个文件用来描述卡片页面的模板布局结构。

- .css结尾的CSS样式文件，这个文件用于描述页面样式。

- .json结尾的JSON配置文件，这个文件用于配置卡片中使用的变量action事件。

各个文件夹的作用：

- pages目录用于存放卡片模板页面。

- common目录用于存放公共资源文件，比如：图片资源。

- i18n目录用于配置不同语言场景资源内容，比如应用文本词条，图片路径等资源。

## 文件访问规则

应用资源可通过绝对路径或相对路径的方式进行访问，本开发框架中绝对路径以"/"开头，相对路径以"./"或"../"。具体访问规则如下：

- 引用代码文件，需使用相对路径，比如：../common/style.css。

- 引用资源文件，推荐使用绝对路径。比如：/common/test.png。

- 公共代码文件和资源文件推荐放在common下，通过规则1和规则2进行访问。

- CSS样式文件中通过url()函数创建&lt;url&gt;数据类型，如：url(/common/test.png)。

> **说明：**
> 当代码文件A需要引用代码文件B时：
>
> - 如果代码文件A和文件B位于同一目录，则代码文件B引用资源文件时可使用相对路径，也可使用绝对路径。
>
> - 如果代码文件A和文件B位于不同目录，则代码文件B引用资源文件时必须使用绝对路径。因为Webpack打包时，代码文件B的目录会发生变化。
>
> - 在json文件中定义的数据为资源文件路径时，需使用绝对路径。

## 配置文件

FA卡片需要在应用配置文件config.json中进行配置。详细的配置内容请参考[FA卡片配置文件说明](../../../quick-start/application-configuration-file-overview-fa.md)。

Stage卡片需要在应用配置文件module.json5中的extensionAbilities标签下，配置ExtensionAbility相关信息。详细的配置内容请参考[Stage卡片配置文件说明](../../../quick-start/application-configuration-file-overview-stage.md)。

# 多语言支持
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @HelloCrease-->

基于开发框架的应用会覆盖多个国家和地区，开发框架支持多语言能力后，可以让应用开发者无需开发多个不同语言的版本，就可以同时支持多种语言的切换，为项目维护带来便利。


开发者仅需要通过[定义资源文件](#定义资源文件)和[引用资源](#引用资源)两个步骤，就可以使用开发框架的多语言能力。


## 定义资源文件

资源文件用于存放应用在多种语言场景下的资源内容，开发框架使用JSON文件保存资源定义。

在[文件组织](js-service-widget-file.md)中指定的i18n文件夹内放置每个语言地区下的资源定义文件即可，资源文件命名为“语言-地区.json”格式，例如英文（美国）的资源文件命名为en-US.json。当开发框架无法在应用中找到系统语言的资源文件时，默认使用en-US.json中的资源内容。

由于不同语言针对单复数有不同的匹配规则，在资源文件中的使用“zero”、“one”、“two”、“few”、“many”、“other”定义不同单复数场景下的词条内容。例如中文不区分单复数仅存在“other”场景；英文存在“one”、“other”场景；阿拉伯语存在上述6种场景。

 以en-US.json和ar-AE.json为例，资源文件内容格式如下：

```json
{
    "strings": {
        "hello": "Hello world!",
        "symbol": "@#$%^&*()_+-={}[]\\|:;\"'<>,./?",
        "plurals": {
            "one": "one person",
            "other": "other people"
        }
    },

    "files": {
        "image": "image/en_picture.PNG"
    }
}
```


```json
{
    "strings": {
        "plurals": {
            "zero": "لا أحد",
            "one": "وحده",
            "two": "اثنان",
            "few": "ستة اشخاص",
            "many": "خمسون شخص",
            "other": "مائة شخص"
        }
    }
}
```


## 引用资源

在应用开发的页面中使用多语言的语法，包含简单格式化和单复数格式化两种，都可以在hml或js中使用。

- 简单格式化方法
  在应用中使用$t方法引用资源，$t既可以在hml中使用，也可以在js中使用。系统将根据当前语言环境和指定的资源路径（通过$t的path参数设置），显示对应语言的资源文件中的内容。

    **表1** 简单格式化

  | 属性   | 类型       | 参数       | 必填   | 描述                                     |
  | ---- | -------- | -------- | ---- | -------------------------------------- |
  | $t   | Function | 请见$t参数说明 | 是    | 根据系统语言完成简单的替换：this.$t('strings.hello') |

    **表2** $t参数说明

  | 参数   | 类型     | 必填   | 描述   |
  | ---- | ------ | ---- | ---- |
  | path | string | 是    | 资源路径 |

- 简单格式化示例代码

  ```html
  <!-- xxx.hml -->
   <div> 
     <text>{{ $t('strings.hello') }}</text>  
     <image src="{{ $t('files.image') }}" class="image"></image> 
   </div>
  ```

- 单复数格式化方法

  **表3** 单复数格式化

  | 属性   | 类型       | 参数        | 必填   | 描述                                       |
  | ---- | -------- | --------- | ---- | ---------------------------------------- |
  | $tc  | Function | 请见$tc参数说明 | 是    | 根据系统语言完成单复数替换：this.$tc('strings.plurals')<br/>定义资源的内容通过json格式的key为“zero”、“one”、“two”、“few”、“many”和“other”区分。 |

  **表4** $tc参数说明

  | 参数    | 类型     | 必填   | 描述    |
  | ----- | ------ | ---- | ----- |
  | path  | string | 是    | 资源路径  |
  | count | number | 是    | 要表达的值 |

- 单复数格式化示例代码

  ```html
  <!--xxx.hml-->
  <div>
    <!-- 传递数值为0时： "0 people" 阿拉伯语中此处匹配key为zero的词条-->
    <text>{{ $tc('strings.plurals', 0) }}</text>
    <!-- 传递数值为1时： "one person" 阿拉伯语中此处匹配key为one的词条-->
    <text>{{ $tc('strings.plurals', 1) }}</text>
    <!-- 传递数值为2时： "2 people" 阿拉伯语中此处匹配key为two的词条-->
    <text>{{ $tc('strings.plurals', 2) }}</text>
    <!-- 传递数值为6时： "6 people" 阿拉伯语中此处匹配key为few的词条-->
    <text>{{ $tc('strings.plurals', 6) }}</text>
    <!-- 传递数值为50时： "50 people" 阿拉伯语中此处匹配key为many的词条-->
    <text>{{ $tc('strings.plurals', 50) }}</text>
    <!-- 传递数值为100时： "100 people" 阿拉伯语中此处匹配key为other的词条-->
    <text>{{ $tc('strings.plurals', 100) }}</text>
  </div>
  ```

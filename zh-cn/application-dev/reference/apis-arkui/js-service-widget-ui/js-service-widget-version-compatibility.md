# 版本兼容适配
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @HelloCrease-->

卡片特性不断增加，使用了新特性的卡片，在不支持这些新特性的老系统上可能显示异常。可以在卡片工程中指定最小SDK版本，防止使用新特性的卡片推送安装在老的系统上。也可以参考本章节的内容，在卡片开发阶段做前向兼容适配。

开发者可以通过JSON配置文件配置前向兼容能力。该文件提供了apiVersion属性用于兼容版本，该字段和卡片配置文件的数据字段data、事件字段actions同级。在apiVersion标签下定义的内容会基于当前运行版本信息，覆盖原始的data标签内容。


示例如下：

假设JS服务卡片框架从API version 9开始，支持设置webp格式的图源（仅用于举例，不代表实际情况），则可以按照如下的方式，做前向兼容。

```html
<!-- xxx.hml -->
<div>
    <image src="{{imageSrc}}" style="width: 100px;height: 100px;"></image>
</div>
```

JSON配置文件：

```json
{
  "data": {
    "imageSrc": "defaultSrc.png"
  },
  "apiVersion": {
    "9": {
      "imageSrc": "newSrc.webp"
    }
  }
}
```

JS服务卡片开发框架会根据应用中的配置及当前系统运行版本，选取最合适的数据。

假设系统运行版本在8及以下，则实际解析的imageSrc值为defaultSrc.png；

假设系统运行版本为9，则实际解析的imageSrc值为newSrc.webp。

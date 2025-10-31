# 使用Deep Linking实现应用间跳转

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

采用Deep Linking进行跳转时，系统会根据接口中传入的uri信息，在本地已安装的应用中寻找到符合条件的应用并进行拉起。当匹配到多个应用时，会拉起应用选择框。

## 实现原理

Deep Linking基于隐式Want匹配机制中的uri匹配来查询、拉起目标应用。隐式Want的uri匹配规则详见[uri匹配规则](explicit-implicit-want-mappings.md#uri匹配规则)。


## 目标应用操作指导

### 配置module.json5文件

为了能够支持被其他应用访问，目标应用需要在[module.json5配置文件](../quick-start/module-configuration-file.md)中配置[skills标签](../quick-start/module-configuration-file.md#skills标签)。

> **说明：**
> 
> skills标签下默认包含一个skill对象，用于标识应用入口。应用跳转链接不能在该skill对象中配置，需要创建独立的skill对象。如果存在多个跳转场景，需要在skills标签下创建不同的skill对象，否则会导致配置无法生效。
> 
> Deep Linking中的scheme取值不以"ohos"开头。通常不为"https"、"http"、"file"等已被系统应用使用的值，否则会匹配到对应的系统应用。


配置示例如下：

<!-- @[quick_start0](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/PullLinking/entry/src/main/module.json5) -->

### 获取并解析拉起方传入的应用链接

在目标应用的UIAbility的[onCreate()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#oncreate)或者[onNewWant()](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md#onnewwant)生命周期回调中，获取、解析拉起方传入的应用链接。

<!-- @[quick_start0](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/PullLinking/entry/src/main/ets/DeepAbility/DeepAbility.ets) -->

## 拉起方应用实现应用跳转

下面通过三个案例，分别介绍如何使用[openLink()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#openlink12)与[startAbility()](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability)接口实现应用跳转，以及如何在[Web组件](../reference/apis-arkweb/arkts-basic-components-web.md)中实现应用跳转。

### 使用openLink实现应用跳转

在[openLink](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#openlink12)接口的link字段中传入目标应用的URL信息，并将options字段中的[appLinkingOnly](../reference/apis-ability-kit/js-apis-app-ability-openLinkOptions.md#openlinkoptions)配置为`false`。


示例代码如下：

<!-- @[quick_start0](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/PullLinking/entry/src/main/ets/pages/DeepOpenLinkIndex.ets) -->

### 使用startAbility实现应用跳转

[startAbility](../reference/apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability)接口是将应用链接放入want中，通过调用[隐式want匹配](explicit-implicit-want-mappings.md#隐式want匹配原理)的方法触发应用跳转。


示例代码如下：

<!-- @[quick_start0](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/PullLinking/entry/src/main/ets/pages/DeepStartIndex.ets) -->

### 使用Web组件实现应用跳转

Web组件可以在[onLoadIntercept](../reference/apis-arkweb/arkts-basic-components-web-events.md#onloadintercept10)的回调函数中实现应用跳转。

示例代码如下：

<!-- @[quick_start0](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Ability/PullLinking/entry/src/main/ets/pages/DeepWebIndex.ets) -->

前端页面代码：
```html
// index.html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
</head>
<body>
<h1>Hello World</h1>
<!--方式一、通过绑定事件window.open方法实现跳转-->
<button class="doOpenLink" onclick="doOpenLink()">跳转其他应用一</button>
<!--方式二、通过超链接实现跳转-->
<a href="link://www.example.com">跳转其他应用二</a>
</body>
</html>
<script>
    function doOpenLink() {
        window.open("link://www.example.com")
    }
</script>
```
# PluginComponent (系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--SE: @lmleon-->
<!--TSE: @fredyuan0912-->

提供外部应用组件嵌入式显示功能，即外部应用提供的UI可在本应用内显示。如需通过跨进程通信实现更新，请参考[@ohos.pluginComponent](../js-apis-plugincomponent.md)。


>  **说明：**
>
>  - 该组件从API Version 9开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
>  - 本模块系统接口。

## 子组件

无


## 接口

PluginComponent(options: PluginComponentOptions)

创建插件组件，用于显示外部应用提供的UI。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                                                     | 必填 | 说明                                                     |
| ------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| options | [PluginComponentOptions](#plugincomponentoptions18类型说明) | 是   | 定义用于构造插件组件的选项。 |

## PluginComponentOptions<sup>18+</sup>类型说明

定义用于构造插件组件的选项。

> **说明：**
>
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 参数       | 类型   | 描述                        |
| ---------- | ------ | --------------------------- |
| template<sup>9+</sup>   | [PluginComponentTemplate](#plugincomponenttemplate9类型说明) | 组件模板，用于跟提供方定义的组件绑定。                |
| data<sup>9+</sup>       | any    | 传给插件组件提供方使用的数据。 |

## PluginComponentTemplate<sup>9+</sup>类型说明

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 参数       | 类型   | 描述                        |
| ---------- | ------ | --------------------------- |
| source     | string | 组件模板名。                |
| bundleName | string | 提供方Ability的bundleName。 |

## 属性

必须显式设置组件宽高为非0有效值。

**说明：**

  模板支持两种提供方式：
* 1.使用绝对路径进行资源提供：source字段填写模板绝对路径，bundleName不需要填写。仅适用于不需要加载资源的单独模板页面，不建议使用。
* 2.通过应用包进行资源提供：bundleName字段需要填写应用包名；source字段填写相对hap包的模板相对路径，对于多hap场景，通过“相对路径&模块名称”的方式进行hap包的确认。

  例如：{source: 'pages/PluginProviderExample.ets&entry', bundleName: 'com.example.provider'}

  仅对FA模型支持source字段填写AbilityName、bundleName字段填写应用包名的方式进行资源提供。

  例如：{source: 'plugin', bundleName: 'com.example.provider'}


## 事件

支持[绑定手势方法](ts-gesture-settings.md)，并分发给提供方页面，在提供方页面内部处理。

除支持[通用事件](ts-component-general-events.md)，还支持以下事件：

### onComplete

onComplete(callback:&nbsp;VoidCallback)

组件加载完成时触发回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                                                     | 必填 | 说明                                                     |
| ------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | [VoidCallback](../../apis-basic-services-kit/js-apis-base.md#callback) | 是   | 回调函数，组件加载完成时触发的回调。 |

### onError

onError(callback:&nbsp;PluginErrorCallback)

组件加载错误时触发回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名    | 类型                                                         | 必填 | 说明                                            |
| --------- | ------------------------------------------------------------ | ---- | ----------------------------------------------- |
| callback  | [PluginErrorCallback](#pluginerrorcallback18类型说明)          | 是   | 发生错误时调用回调。 |

## PluginErrorCallback<sup>18+</sup>类型说明

发生错误时调用回调。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 参数     | 类型               | 描述                        |
| -------- | ------------------ | --------------------------- |
| info     | [PluginErrorData](#pluginerrordata18类型说明)  | 发生错误时提供的数据。 |

## PluginErrorData<sup>18+</sup>类型说明

发生错误时提供的数据。

> **说明：**
>
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 参数       | 类型   | 描述                        |
| ---------- | ------ | -------------------------- |
| errcode<sup>9+</sup>    | number | 错误码。                    |
| msg<sup>9+</sup>        | string | 错误信息。                  |

错误码1为默认错误码，错误信息和处理建议详见下表：

| 错误信息   | 描述                        | 处理建议 |
| ------ | -------------------------- | ----------------- |
| package path is empty. | 包路径为空。 | 检查PluginComponentTemplate参数中source字段是否有误。  |
| Query Active OsAccountIds failed! | 获取激活的用户ID失败。 | 检查Account服务是否异常，或检查应用是否具备用户ID查询权限。    |
| Template source is empty. | 模板source为空。 | 检查PluginComponentTemplate参数中source字段是否有误。  |
| Bms bundleManager is nullptr. | 获取BundleManager失败。 |  检查BMS服务是否异常，或检查应用是否具备ohos.permission.GET_BUNDLE_INFO_PRIVILEGED,ohos.permission.GET_BUNDLE_INFO,ohos.permission.REQUIRE_FORM权限。                  |
| App bundleName is empty. | 应用包名为空。  | 检查PluginComponentTemplate参数中bundleName字段是否有误。                   |
| Bms get bundleName failed! | 获取包名失败。  |  检查PluginComponentTemplate参数中bundleName字段是否有误，或检查bundleName字段对应的包是否已正确安装，或检查BMS服务是否异常，或检查应用是否具备ohos.permission.GET_BUNDLE_INFO_PRIVILEGED,ohos.permission.GET_BUNDLE_INFO,ohos.permission.REQUIRE_FORM权限。                |
| Bms moduleResPaths is empty. | 插件包moduleResPaths属性为空。 |  检查bundleName字段对应的包的moduleResPaths属性是否异常，或检查BMS服务是否异常                   |
| Bms get hapPath failed! Cannot find hap according to BundleName and ModuleName! | 获取hapPath失败。  |   检查PluginComponentTemplate参数中bundleName字段是否有误，检查bundleName字段对应的模块是否已正确安装。               |


## 示例（加载PluginComponent）

本示例展示`PluginComponent`组件的基础使用方式，需要创建一个`bundleName`为"com.example.user"的[使用方应用](#组件使用方)，和一个`bundleName`为"com.example.provider"的[提供方应用](#组件提供方)。应用项目构建完成后，具体测试步骤如下：
1. 将两个应用的hap包安装到设备上；
2. 打开使用方应用页面，使用方与提供方内容都正确显示；
3. 分别点击使用方的“Register Push Listener”按钮和提供方的“Register Request Listener”按钮注册监听；
4. 点击使用方的“Request”按钮向提供方发送事件，日志中打印“onRequestListener”相关信息；
5. 点击提供方的“Push”按钮向使用方发送事件，日志中打印“onPushListener”相关信息。

### 组件使用方

使用方应用的`bundleName`为"com.example.user"，包含一个页面。
- `EntryAbility(UIAbility)`加载入口页面文件`ets/pages/Index.ets`，`Index.ets`内容如下：
  ```ts
  import plugin from "./plugin_component";

  interface Info {
    errcode: number,
    msg: string
  }

  @Entry
  @Component
  struct PluginUserExample {
    build() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
        Text('Hello World')
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
        Button('Register Push Listener')
          .fontSize(30)
          .width(400)
          .height(100)
          .margin({ top: 20 })
          .onClick(() => {
            plugin.onListener();
            console.info("Button('Register Push Listener')");
          })
        Button('Request')
          .fontSize(50)
          .width(400)
          .height(100)
          .margin({ top: 20 })
          .onClick(() => {
            plugin.Request();
            console.info("Button('Request')");
          })
        PluginComponent({
          // 提供方
          template: { source: 'pages/Index.ets&entry', bundleName: 'com.example.provider' },
          data: { 'countDownStartValue': 'new countDownStartValue' }
        }).size({ width: 500, height: 350 })
          .onComplete(() => {
            console.info("onComplete");
          })
          .onError((info: Info) => {
            console.error("onError" + info.errcode + ":" + info.msg);
          })
      }
      .width('100%')
      .height('100%')
    }
  }
  ```
- 根据模型类型，将对应的[Plugin组件工具代码](#plugin组件工具)拷贝至项目的`ets/pages/plugin_component.js`文件中。
- 在`module.json5`配置文件中增加`requestPermissions`标签，允许使用方查询其他应用信息：
  ```json
  "requestPermissions": [
    {
      "name": "ohos.permission.GET_BUNDLE_INFO_PRIVILEGED",
      "usedScene": {
        "abilities": [
          "EntryAbility"
        ],
        "when": "inuse"
      }
    }
  ]
  ```

### 组件提供方

提供方应用的`bundleName`为"com.example.provider"，包含一个页面。
- `EntryAbility(UIAbility)`加载入口页面文件`ets/pages/Index.ets`，`Index.ets`内容如下：
  ```ts
  import plugin from "./plugin_component";

  @Entry
  @Component
  struct PluginProviderExample {
    @State message: string = 'no click!';

    build() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
        Button('Register Request Listener')
          .fontSize(30)
          .width(400)
          .height(100)
          .margin({ top: 20 })
          .onClick(() => {
            plugin.onListener();
            console.info("Button('Register Request Listener')");
          })
        Button('Push')
          .fontSize(30)
          .width(400)
          .height(100)
          .margin({ top: 20 })
          .onClick(() => {
            plugin.Push();
            this.message = "Button('Push')";
            console.info("Button('Push')");
          })
        Text(this.message)
          .height(150)
          .fontSize(30)
          .padding(5)
          .margin(5)
      }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding({ top: 5 })
    }
  }
  ```
- 根据模型类型，将对应的[Plugin组件工具代码](#plugin组件工具)拷贝至项目的`ets/pages/plugin_component.js`文件中。

### Plugin组件工具

Plugin组件工具，用于使用方与提供方之间进行通信。需要根据模型类型选择对应代码，并拷贝至项目中。

#### FA模型
```js
// 当前示例代码仅适用于FA模型
import pluginComponentManager from '@ohos.pluginComponent'

var providerBundleName = 'com.example.provider'
var providerAbilityName = 'com.example.provider.EntryAbility'
var providerName = 'Index'

// push事件监听
function onPushListener(source, template, data, extraData) {
    console.info("onPushListener template.source=" + template.source)
    console.info("onPushListener template.ability=" + template.ability)
    console.info("onPushListener data=" + JSON.stringify(data))
    console.info("onPushListener extraData=" + JSON.stringify(extraData))
}

// request事件监听
function onRequestListener(source, name, data)
{
    console.info("onRequestListener name=" + name);
    console.info("onRequestListener data=" + JSON.stringify(data));
    return {template:"pluginTemplate", data:data};
}

export default {
    // 注册监听事件
    onListener() {
        pluginComponentManager.on("push", onPushListener)
        pluginComponentManager.on("request", onRequestListener)
    },
    Push() {
        // 组件提供方主动发送事件，want: 提供方信息
        pluginComponentManager.push(
            {
                want: {
                    bundleName: providerBundleName,
                    abilityName: providerAbilityName,
                },
                name: providerName,
                data: {
                    "key_1": "plugin component push data",
                    "key_2": 12345
                },
                extraData: {
                    "extra_str": "this is push event"
                },
                jsonPath: "",
            },
            (err, data) => {
                console.info("push_callback: push ok!");
            }
        )
    },
    Request() {
        // 组件使用方主动发送事件，want: 提供方信息
        pluginComponentManager.request({
            want: {
                bundleName: providerBundleName,
                abilityName: providerAbilityName,
            },
            name: providerName,
            data: {
                "key_1": "plugin component request data",
                "key_2": 67890
            },
            jsonPath: "",
        },
            (err, data) => {
                console.info("request_callback: componentTemplate.ability=" + data.componentTemplate.ability)
                console.info("request_callback: componentTemplate.source=" + data.componentTemplate.source)
                console.info("request_callback: data=" + JSON.stringify(data.data))
                console.info("request_callback: extraData=" + JSON.stringify(data.extraData))
            }
        )
    }
}
```

#### Stage模型
```js
// 当前示例代码仅适用于Stage模型
import pluginComponentManager from '@ohos.pluginComponent'

var userBundleName = 'com.example.user'
var userAbilityName = 'com.example.user.EntryAbility'
var providerBundleName = 'com.example.provider'
var providerAbilityName = 'com.example.provider.EntryAbility'
var providerName = 'Index'

// push事件监听
function onPushListener(source, template, data, extraData) {
    console.info("onPushListener template.source=" + template.source)
    console.info("onPushListener template.ability=" + template.ability)
    console.info("onPushListener data=" + JSON.stringify(data))
    console.info("onPushListener extraData=" + JSON.stringify(extraData))
}

// request事件监听
function onRequestListener(source, name, data) {
    console.info("onRequestListener name=" + name)
    console.info("onRequestListener data=" + JSON.stringify(data))
    return { template: "pluginTemplate", data: data }
}

export default {
    // 注册监听事件
    onListener() {
        pluginComponentManager.on("push", onPushListener)
        pluginComponentManager.on("request", onRequestListener)
    },
    Push() {
        // 组件提供方主动发送事件，owner:使用方，target:提供方
        pluginComponentManager.push(
            {
                owner: {
                    bundleName: userBundleName,
                    abilityName: userAbilityName,
                },
                target: {
                    bundleName: providerBundleName,
                    abilityName: providerAbilityName,
                },
                name: providerName,
                data: {
                    "key_1": "plugin component push data",
                    "key_2": 12345
                },
                extraData: {
                    "extra_str": "this is push event"
                },
                jsonPath: "",
            },
            (err, data) => {
                console.info("push_callback: push ok!");
            }
        )
    },
    Request() {
        // 组件使用方主动发送事件，owner:使用方，target:提供方
        pluginComponentManager.request({
            owner: {
                bundleName: userBundleName,
                abilityName: userAbilityName,
            },
            target: {
                bundleName: providerBundleName,
                abilityName: providerAbilityName,
            },
            name: providerName,
            data: {
                "key_1": "plugin component request data",
                "key_2": 67890
            },
            jsonPath: "",
        },
            (err, data) => {
                console.info("request_callback: componentTemplate.ability=" + data.componentTemplate.ability)
                console.info("request_callback: componentTemplate.source=" + data.componentTemplate.source)
                console.info("request_callback: data=" + JSON.stringify(data.data))
                console.info("request_callback: extraData=" + JSON.stringify(data.extraData))
            }
        )
    }
}
```

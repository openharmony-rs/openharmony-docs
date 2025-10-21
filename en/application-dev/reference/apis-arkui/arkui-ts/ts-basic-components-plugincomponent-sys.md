# PluginComponent (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @lmleon-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @HelloCrease-->

The **PluginComponent** allows an application to display external UI from another application. To implement update through inter-process communication (IPC), see [@ohos.pluginComponent](../js-apis-plugincomponent.md).


>  **NOTE**
>
>  - This component is supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
>  - The APIs provided by this module are system APIs.

## Child Components

Not supported


## APIs

PluginComponent(options: PluginComponentOptions)

Creates a **PluginComponent** to display the UI provided by an external application.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                    | Mandatory| Description                                                    |
| ------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| options | [PluginComponentOptions](#plugincomponentoptions18) | Yes  | Configuration options of the **PluginComponent**.|

## PluginComponentOptions<sup>18+</sup>

Defines options for constructing a **PluginComponent**.

> **NOTE**
>
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18. While historical version information is preserved for anonymous objects, there may be cases where the outer element's @since version number is higher than inner elements'. This does not affect interface usability.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Type  | Description                       |
| ---------- | ------ | --------------------------- |
| template<sup>9+</sup>   | [PluginComponentTemplate](#plugincomponenttemplate9) | Template of the **PluginComponent**, which is bound to the component defined by the provider.               |
| data<sup>9+</sup>       | any    | Data passed to the **PluginComponent** provider.|

## PluginComponentTemplate<sup>9+</sup>

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Type  | Description                       |
| ---------- | ------ | --------------------------- |
| source     | string | Component template name.               |
| bundleName | string | Bundle name of the provider ability.|

## Attributes

The width and height of the component must be explicitly set to non-zero valid values.

**NOTE**

  The template can be provided in either of the following modes:
* 1. Use an absolute path. In this case, set **source** to the absolute path of the template and leave **bundleName** blank. This mode is not recommended as it is applicable only to standalone templates that do not need to load resources.
* 2. Use an application package. In this case, set **bundleName** to the application bundle name and **source** to the relative path of the HAP file template. In the multi-HAP scenario, a HAP file is identified based on its relative path and name.

  Example: **{source: 'pages/PluginProviderExample.ets&entry', bundleName: 'com.example.provider'}**

  The template is provided only when **source** can be set to an ability name or bundle name in the FA model.

  Example: **{source: 'plugin', bundleName: 'com.example.provider'}**


## Events

[Gesture events](ts-gesture-settings.md) can be distributed to and processed inside the provider page.

In addition to the [universal events](ts-component-general-events.md), the following events are supported.

### onComplete

onComplete(callback: VoidCallback)

Triggered when the component loading is complete.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                    | Mandatory| Description                                                    |
| ------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | [VoidCallback](../../apis-basic-services-kit/js-apis-base.md#callback) | Yes  | Callback function, which is triggered when the component loading is complete.|

### onError

onError(callback: PluginErrorCallback)

Triggered when an error occurs during component loading.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                                                        | Mandatory| Description                                           |
| --------- | ------------------------------------------------------------ | ---- | ----------------------------------------------- |
| callback  | [PluginErrorCallback](#pluginerrorcallback18)          | Yes  | Callback invoked when an error occurs.|

## PluginErrorCallback<sup>18+</sup>

Callback invoked when an error occurs.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type              | Description                       |
| -------- | ------------------ | --------------------------- |
| info     | [PluginErrorData](#pluginerrordata18)  | Data provided when the error occurs.|

## PluginErrorData<sup>18+</sup>

Data provided when the error occurs.

> **NOTE**
>
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18. While historical version information is preserved for anonymous objects, there may be cases where the outer element's @since version number is higher than inner elements'. This does not affect interface usability.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Type  | Description                       |
| ---------- | ------ | -------------------------- |
| errcode<sup>9+</sup>    | number | Error code.                   |
| msg<sup>9+</sup>        | string | Error message.                 |

Error code 1 is the default error code. The following table describes the error information and handling suggestions.

| Error Message  | Description                       | Handling Suggestion|
| ------ | -------------------------- | ----------------- |
| package path is empty. | Empty package path.| Check whether the source field in the PluginComponentTemplate parameter is correct. |
| Query Active OsAccountIds failed! | Failed to obtain the activated user ID.| Check whether the Account service is abnormal or whether the application has the permission to query the user ID.   |
| Template source is empty. | The template source is empty.| Check whether the source field in the PluginComponentTemplate parameter is correct. |
| Bms bundleManager is nullptr. | Failed to obtain the bundle manager.|  Check whether the BMS service is abnormal or whether the application has the ohos.permission.GET_BUNDLE_INFO_PRIVILEGED,ohos.permission.GET_BUNDLE_INFO,ohos.permission.REQUIRE_FORM permission.                 |
| App bundleName is empty. | The application package name is empty. | Check whether the bundleName field in the PluginComponentTemplate parameter is correct.                  |
| Bms get bundleName failed! | Failed to obtain the package name. |  Check whether the bundleName field in the PluginComponentTemplate parameter is correct, whether the package corresponding to the bundleName field is correctly installed, whether the BMS service is abnormal, or whether the application has the ohos.permission.GET_BUNDLE_INFO_PRIVILEGED,ohos.permission.GET_BUNDLE_INFO,ohos.permission.REQUIRE_FORM permission.               |
| Bms moduleResPaths is empty. | The moduleResPaths attribute of the plugin package is empty.|  Check whether the moduleResPaths attribute of the package corresponding to the bundleName field is abnormal or whether the BMS service is abnormal.                  |
| Bms get hapPath failed! Cannot find hap according to BundleName and ModuleName! | Failed to obtain the hapPath. |   Check whether the bundleName field in the PluginComponentTemplate parameter is correct and whether the module corresponding to the bundleName field is correctly installed.              |


## Example: Loading a PluginComponent

This example demonstrates the basic usage of the **PluginComponent**. Specifically, you need to create an application acting as the **PluginComponent** [user](#plugincomponent-user) with the bundle name of **"com.example.user"** and an application acting as the **PluginComponent** [provider](#plugincomponent-provider) with the bundle name of **"com.example.provider"**. After building the application projects, perform the following steps for testing:
1. Install the HAP packages of both applications on the device.
2. Open the user application page. Both user and provider content should be displayed correctly.
3. Register listeners by clicking the **Register Push Listener** button on the user side and the **Register Request Listener** button on the provider side.
4. Send a request from the user to the provider by clicking the **Request** button. The log should print information related to **onRequestListener**.
5. Send a push event from the provider to the user by clicking the **Push** button. The log should print information related to **onPushListener**.

### PluginComponent User

The user application has a bundle name of **"com.example.user"** and contains one page.
- The EntryAbility (UIAbility) loads the entry page file **ets/pages/Index.ets**, which contains the following code:
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
          // Provider
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
- Copy the [PluginComponent manager code](#plugincomponent-manager) corresponding to your project model type to the **ets/pages/plugin_component.js** file.
- Add the **requestPermissions** tag in the **module.json5** file to allow the user application to query information from other applications:
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

### PluginComponent Provider

The provider application has a bundle name of **"com.example.provider"** and contains one page.
- The EntryAbility (UIAbility) loads the entry page file **ets/pages/Index.ets**, which contains the following code:
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
- Copy the [PluginComponent manager code](#plugincomponent-manager) corresponding to your project model type to the **ets/pages/plugin_component.js** file.

### PluginComponent Manager

The **PluginComponent** manager is used for communication between the user and provider. You need to select the corresponding code based on the model type and copy it into your project.

### FA Model
```js
// This example code is only applicable to the FA model.
import pluginComponentManager from '@ohos.pluginComponent'

var providerBundleName = 'com.example.provider'
var providerAbilityName = 'com.example.provider.EntryAbility'
var providerName = 'Index'

// Push event listener
function onPushListener(source, template, data, extraData) {
    console.info("onPushListener template.source=" + template.source)
    console.info("onPushListener template.ability=" + template.ability)
    console.info("onPushListener data=" + JSON.stringify(data))
    console.info("onPushListener extraData=" + JSON.stringify(extraData))
}

// Request event listener
function onRequestListener(source, name, data)
{
    console.info("onRequestListener name=" + name);
    console.info("onRequestListener data=" + JSON.stringify(data));
    return {template:"pluginTemplate", data:data};
}

export default {
    // Register event listeners.
    onListener() {
        pluginComponentManager.on("push", onPushListener)
        pluginComponentManager.on("request", onRequestListener)
    },
    Push() {
        // The provider proactively sends an event, want: provider information.
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
        // The user proactively sends an event, want: provider information.
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

### Stage Model
```js
// This example code is only applicable to the stage model.
import pluginComponentManager from '@ohos.pluginComponent'

var userBundleName = 'com.example.user'
var userAbilityName = 'com.example.user.EntryAbility'
var providerBundleName = 'com.example.provider'
var providerAbilityName = 'com.example.provider.EntryAbility'
var providerName = 'Index'

// Push event listener
function onPushListener(source, template, data, extraData) {
    console.info("onPushListener template.source=" + template.source)
    console.info("onPushListener template.ability=" + template.ability)
    console.info("onPushListener data=" + JSON.stringify(data))
    console.info("onPushListener extraData=" + JSON.stringify(extraData))
}

// Request event listener
function onRequestListener(source, name, data) {
    console.info("onRequestListener name=" + name)
    console.info("onRequestListener data=" + JSON.stringify(data))
    return { template: "pluginTemplate", data: data }
}

export default {
    // Register event listeners.
    onListener() {
        pluginComponentManager.on("push", onPushListener)
        pluginComponentManager.on("request", onRequestListener)
    },
    Push() {
        // The provider proactively sends an event, owner: user, target: provider.
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
        // The user proactively sends an event, owner: user, target: provider.
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

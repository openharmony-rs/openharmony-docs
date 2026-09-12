# @ohos.pluginComponent (PluginComponentManager) (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @dutie123-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9b1b6fae0e5d6eff2af82615c4a9d4858b3a4a63 translatedAt=2026-09-01T03:25:26.884Z pushedAt=2026-09-02T02:24:40.270Z -->

The **PluginComponentManager** module provides APIs for the **PluginComponent** user to request components and data and send component templates and data. This module is applicable to cross-Ability or cross-application component display based on plug-ins, enabling dynamic distribution and loading of component templates and service data, and supporting decoupling between component providers and users. For details about how to display the **PluginComponent** template, see [PluginComponent](arkui-ts/ts-basic-components-plugincomponent-sys.md).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only the system APIs of this module. For details about other public APIs, see [@ohos.pluginComponent (PluginComponentManager)](js-apis-plugincomponent.md).

## Modules to Import

```ts
import { pluginComponentManager } from '@kit.ArkUI';
```

### PushParameterForStage<sup>9+</sup>

Sets the parameters to be passed in the **pluginComponentManager.push** API in the stage model.

**System API:** This is a system API.

**Model restriction**: This API can be used only in the [stage model](arkui-ts/ts-basic-components-plugincomponent-sys.md#stage-model).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Type                                 | Read-Only| Optional  | Description                                      |
| --------- | ----------------------------------- | ---- | ---- | ---------------------------------------- |
| owner     | [Want](../apis-ability-kit/js-apis-application-want.md) | No| No   | Ability information of the component provider.                         |
| target    | [Want](../apis-ability-kit/js-apis-application-want.md) | No| No   | Ability information of the component user.                         |
| name      | string                              | No | No    | Component name. When **jsonPath** is not empty, the component name must be consistent with the key name in the [external.json](#about-the-externaljson-file) file.                                    |
| data      | [KVObject](js-apis-plugincomponent.md#kvobject)      |     No     | No    | Component data, stored in key-value pairs. It is used to transfer service data to the component user, such as the page path (if **key** is **'js'**, **value** is the template path string) and custom data fields.                                   |
| extraData | [KVObject](js-apis-plugincomponent.md#kvobject)          | No    | No    | Extra data used to transfer additional custom data when sending a component. It is distinguished from component data (**data**) and can be set based on service requirements.                                   |
| jsonPath  | string                         |  No   | Yes    | Path of the [external.json](#about-the-externaljson-file) file that stores the template path. When **jsonPath** is not empty, Push communication is not triggered, and the component template path is read from the **external.json** file. When **jsonPath** is empty (default), the component template is sent to the component user through Push communication. |

### RequestParameterForStage<sup>9+</sup>

Sets the parameters to be passed in the **pluginComponentManager.request** API in the stage model.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the [stage model](arkui-ts/ts-basic-components-plugincomponent-sys.md#stage-model).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Type                          |   Read-Only   | Optional  | Description                                      |
| -------- | ----------------------------------- | ---- | ---- | ---------------------------------------- |
| owner    | [Want](../apis-ability-kit/js-apis-application-want.md)| No| No   | Ability information of the component user.                         |
| target   | [Want](../apis-ability-kit/js-apis-application-want.md) | No| No   | Ability information of the component provider.                         |
| name     | string                         | No   | No    | Name of the requested component. When **jsonPath** is not empty, it must be consistent with the key name in the [external.json](#about-the-externaljson-file) file.                                  |
| data     | [KVObject](js-apis-plugincomponent.md#kvobject)        | No    | No    | Extra data stored in key-value pairs, used to transfer custom service parameters to the component provider during a request, so that the provider can return an appropriate component template based on the data.                                    |
| jsonPath | string | No | Yes | Path of the [external.json](#about-the-externaljson-file) file that stores the template path. This parameter is passed when the template path needs to be loaded from the **external.json** file instead of being obtained through Request communication. When **jsonPath** is not empty, Request communication is not triggered. When **jsonPath** is empty (default), the component template is requested from the component provider through Request communication. |

### push<sup>9+</sup>

push(param: PushParameterForStage, callback: AsyncCallback&lt;void&gt;): void

Proactively pushes the component and data to the component user. This API applies to scenarios where the plug-in component template needs to be proactively pushed, for example, cross-application content sharing and proactive refresh of home screen cards. **push** is proactively initiated by the component provider, while **request** is proactively initiated by the component user. Note that the two have similar parameter structures but opposite meanings of **owner** and **target**, so do not confuse them. The component user must listen for the received data through the **onPush** event. For details about the event listener API, see [@ohos.pluginComponent (PluginComponentManager)](js-apis-plugincomponent.md#plugincomponentmanageron).

**System API**: This is a system API.

**Model restriction**: This API can be used only in the [stage model](arkui-ts/ts-basic-components-plugincomponent-sys.md#stage-model).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**
| Name     | Type                                      | Mandatory  | Description          |
| -------- | ---------------------------------------- | ---- | ------------ |
| param    | [PushParameterForStage](#pushparameterforstage9) | Yes   | Parameters to be sent by the component provider. |
| callback | AsyncCallback&lt;void&gt;                | Yes   | Asynchronous callback used to return the result.|

**Example**

```ts
import { pluginComponentManager } from '@kit.ArkUI';

pluginComponentManager.push(
  {
    owner: {
      bundleName: "com.example.provider",
      abilityName: "com.example.provider.MainAbility",
    },
    target: {
      bundleName: "com.example.user",
      abilityName: "com.example.user.MainAbility",
    },
    name: "ets/pages/plugin2.js",
    data: {
      "js": "ets/pages/plugin.js",
      "key1": 1111,
    },
    extraData: {
      "extraStr": "this is push event"
    },
    jsonPath: "",
  },
  (err, data) => {
    if (err) {
      console.error(`Failed to push. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info("push_callback:data: ", JSON.stringify(data));
    console.info("push_callback: push ok!");
  }
);
```

### request<sup>9+</sup>

request(param: RequestParameterForStage, callback: AsyncCallback&lt;RequestCallbackParameters&gt;): void

Requests the component from the component provider. This API applies to scenarios where the component user needs to dynamically obtain the plug-in component template on demand, for example, dynamically loading plug-in content provided by other applications and displaying cross-application components on demand. The component provider must listen for the request response through the **onRequest** event, and return the component template information through a callback. For details about the event listener API, see [@ohos.pluginComponent (PluginComponentManager)](js-apis-plugincomponent.md#plugincomponentmanageron).

**System API**: This is a system API.

**Model restriction**: This API can be used only in the [stage model](arkui-ts/ts-basic-components-plugincomponent-sys.md#stage-model).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type                                      | Mandatory  | Description                                 |
| -------- | ---------------------------------------- | ---- | ----------------------------------- |
| param    | [RequestParameterForStage](#requestparameterforstage9) | Yes    | Details about the component template request.                        |
| callback | AsyncCallback&lt;[RequestCallbackParameters](js-apis-plugincomponent.md#requestcallbackparameters)&gt; | Yes | Asynchronous callback for this request, which returns the request response data through the parameter of the callback. |

**Example**

```ts
import { pluginComponentManager } from '@kit.ArkUI';

pluginComponentManager.request(
  {
    owner: {
      bundleName: "com.example.user",
      abilityName: "com.example.user.MainAbility",
    },
    target: {
      bundleName: "com.example.provider",
      abilityName: "com.example.provider.MainAbility",
    },
    name: "plugintemplate",
    data: {
      "key1": "myapplication plugin component test",
    },
    jsonPath: "",
  },
  (err, data) => {
    if (err) {
      console.error(`Failed to request. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    if (!data) {
      return;
    }
    console.info("request_callback: componentTemplate.ability=" + data.componentTemplate.ability);
    console.info("request_callback: componentTemplate.source=" + data.componentTemplate.source);
  }
);
```

## About the external.json File

The **external.json** file is created by developers. It stores component names and template paths in key-value pairs. The component name is used as the keyword, and the corresponding template path is used as the value.

**Example**

```json
{
  "PluginProviderExample": "ets/pages/PluginProviderExample.js",
  "plugintemplate2": "ets/pages/plugintemplate2.js"
}

```
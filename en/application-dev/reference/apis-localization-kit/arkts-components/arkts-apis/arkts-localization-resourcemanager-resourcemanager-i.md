# ResourceManager

```TypeScript
export interface ResourceManager
```

Provides the capability of accessing application resources and system resources. The accessible resources include the resources in the HAP/HSP module corresponding to the current context and all system resources.

> **NOTE:** 
> 
> - The methods involved in **ResourceManager** are applicable only to the TypeScript-based declarative development paradigm.
> 
> - Resource files are defined in the **resources** directory of the project. You can obtain resource values such as strings, string arrays, and colors based on the specified **resName**, **resId**, or **Resource** object.
> **resName** indicates the resource name, **resId** indicates the resource ID, which can be obtained through
> `$r(*resource-address*).id`, for example, `$r('app.string.test').id`.
> 
> - No matter whether resources are in the same HAP or different HAPs or HSPs, you are advised to use the API with
> **resName** or **resId** specified. Using the **Resource** object will take a longer time. If the resources are
> in different HAPs or HSPs, you first need to use
> [createModuleContext](../../apis-ability-kit/arkts-apis/arkts-ability-application-createmodulecontext-f.md) to create the context
> of the corresponding module and then call the API with **resName** or **resId** specified. For more information,
> see [Accessing Resources](../../../quick-start/resource-categories-and-access.md#accessing-resources).
> 
> - In API version 22 and earlier versions, an exception is thrown due to an invalid ID when the intermediate-code HAR or bytecode HAR accesses resources through resource ID-related APIs. From API version 23, the intermediate-code HAR or bytecode HAR can properly access resources through resource ID-related APIs. For details, see [Accessing Resources](../../../quick-start/resource-categories-and-access.md#accessing-resources).

**Since:** 6

**System capability:** SystemCapability.Global.ResourceManager

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
```

## addResource

```TypeScript
addResource(path: string) : void
```

Loads the specified overlay resource during application runtime to implement theme switching or resource overriding.

> **NOTE:** 
> 
> Resource overwriting is not supported for the **rawfile** and **resfile** directories.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Absolute path of the HSP or HAP resource package to be loaded. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001010](../errorcode-resource-manager.md#9001010-invalid-overlay-path) | Invalid overlay path. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // Replace "/library1-default-signed.hsp" with the actual file path.
        let path = this.context.bundleCodeDir + "/library1-default-signed.hsp";
        try {
            this.context.resourceManager.addResource(path);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`addResource failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## closeRawFd

```TypeScript
closeRawFd(path: string, callback: _AsyncCallback<void>): void
```

Closes the file descriptor (fd) of the HAP where a specific rawfile in the **resources/rawfile** directory is located. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | rawfile path relative to the **resources/rawfile** directory, such as **test.txt** or **subdir/test.txt**. The path must not start with a slash (/). |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-invalid-relative-path) | Invalid relative path. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      // Replace "test.txt" with the actual resource.
      let rawfile = this.context.resourceManager.getRawFdSync("test.txt");
      // Use rawfile resources based on the actual service scenario.
      this.context.resourceManager.closeRawFd("test.txt", (error: BusinessError) => {
        if (error != null) {
          console.error("error is " + error);
          return;
        }
        console.info('closeRawFd success.');
      });
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`callback closeRawFd failed, error code: ${code}, message: ${message}.`);
    }
  }
}
```

<a id="closerawfd-1"></a>

## closeRawFd

```TypeScript
closeRawFd(path: string): Promise<void>
```

Closes the file descriptor (fd) of the HAP where a specific rawfile in the **resources/rawfile** directory is located. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | rawfile path relative to the **resources/rawfile** directory, such as **test.txt** or **subdir/test.txt**. The path must not start with a slash (/). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-invalid-relative-path) | Invalid relative path. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      // Replace "test.txt" with the actual resource.
      let rawfile = this.context.resourceManager.getRawFdSync("test.txt");
      // Use rawfile resources based on the actual service scenario.
      this.context.resourceManager.closeRawFd("test.txt");
      console.info(`closeRawFd test success.`);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`promise closeRawFd failed, error code: ${code}, message: ${message}.`);
    }
  }
}
```

## closeRawFdSync

```TypeScript
closeRawFdSync(path: string): void
```

Closes the file descriptor (fd) of the HAP where the **rawfile** file in the **resources/rawfile** directory is located. This API returns the result synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | rawfile path relative to the **resources/rawfile** directory, such as **test.txt** or **subdir/test.txt**. The path must not start with a slash (/). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-invalid-relative-path) | Invalid relative path. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      // Replace "test.txt" with the actual resource.
      let rawfile = this.context.resourceManager.getRawFdSync("test.txt");
      // Use rawfile resources based on the actual service scenario.

      this.context.resourceManager.closeRawFdSync("test.txt");
      console.info(`closeRawFdSync test success.`);
    } catch (error) {
      let code = (error as BusinessError).code;
      let message = (error as BusinessError).message;
      console.error(`closeRawFdSync test failed, error code: ${code}, message: ${message}.`);
    }
  }
}
```

## closeRawFileDescriptor

```TypeScript
closeRawFileDescriptor(path: string, callback: AsyncCallback<void>): void
```

Closes the file descriptor (fd) of a specific rawfile in the **resources/rawfile** directory. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [closeRawFd](#closerawfd)(path: string, callback: _AsyncCallback&lt;void&gt;)

**System capability:** SystemCapability.Global.ResourceManager

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | rawfile path relative to the **resources/rawfile** directory, such as **test.txt** or **subdir/test.txt**. The path must not start with a slash (/). |
| callback | [AsyncCallback](arkts-localization-resourcemanager-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.closeRawFileDescriptor("test.txt", (error: Error) => {
        if (error != null) {
            console.error("error is " + error);
        }
    });
});
```

<a id="closerawfiledescriptor-1"></a>

## closeRawFileDescriptor

```TypeScript
closeRawFileDescriptor(path: string): Promise<void>
```

Closes the file descriptor (fd) of a specific rawfile in the **resources/rawfile** directory. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [closeRawFd](#closerawfd-1)(path: string)

**System capability:** SystemCapability.Global.ResourceManager

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | rawfile path relative to the **resources/rawfile** directory, such as **test.txt** or **subdir/test.txt**. The path must not start with a slash (/). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.closeRawFileDescriptor("test.txt");
});
```

## getBoolean

```TypeScript
getBoolean(resId: number): boolean
```

Obtains a Boolean value based on the specified resource ID. This API returns the result synchronously.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Boolean value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/boolean.json
{
  "boolean": [
    {
      "name": "boolean_test",
      "value": true
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace 'app.boolean.boolean_test' with the actual resource.
            let boolTest = this.context.resourceManager.getBoolean($r('app.boolean.boolean_test').id);
            console.info(`getBoolean, result: ${boolTest}`);
            // Print the output result: getBoolean, result: true
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getBoolean failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getboolean-1"></a>

## getBoolean

```TypeScript
getBoolean(resource: Resource): boolean
```

Obtains a Boolean value based on the specified resource object. This API returns the result synchronously.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** [getBoolean](#getboolean)(resId: number)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Boolean value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/boolean.json
{
  "boolean": [
    {
      "name": "boolean_test",
      "value": true
    }
  ]
}
```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.boolean.boolean_test').id
};
try {
  let boolTest = this.context.resourceManager.getBoolean(resource);
  console.info(`getBoolean, result: ${boolTest}`);
  // Print the output result: getBoolean, result: true
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getBoolean failed, error code: ${code}, message: ${message}.`);
}
```

## getBooleanByName

```TypeScript
getBooleanByName(resName: string): boolean
```

Obtains a Boolean value based on the specified resource name. This API returns the result synchronously.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Boolean value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/boolean.json
{
  "boolean": [
    {
      "name": "boolean_test",
      "value": true
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "boolean_test" with the actual resource.
            let boolTest = this.context.resourceManager.getBooleanByName("boolean_test");
            console.info(`getBooleanByName, result: ${boolTest}`);
            // Print the output result: getBooleanByName, result: true
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getBooleanByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getColor

```TypeScript
getColor(resId: number, callback: _AsyncCallback<number>): void
```

Obtains the color value corresponding to the specified resource ID. This API uses an asynchronous callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;number&gt; | Yes | Callback used to return the color value (decimal). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/color.json
{
  "color": [
    {
      "name": "test",
      "value": "#FFFFFF"
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // Replace 'app.color.test' with the actual resource.
        this.context.resourceManager.getColor($r('app.color.test').id)
            .then((value: number) => {
                console.info(`getColor, result: ${value}`);
                // Print the output result: getColor, result: 4294967295
            })
            .catch((error: BusinessError) => {
                console.error(`promise getColor failed, error code: ${error.code}, message: ${error.message}.`);
            });
    }
}
```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.color.test').id
};
this.context.resourceManager.getColor(resource, (error: BusinessError, value: number) => {
  if (error != null) {
    console.error(`callback getColor failed, error code: ${error.code}, message: ${error.message}.`);
  } else {
    console.info(`getColor, result: ${value}`);
    // Print the output result: getColor, result: 4294967295
  }
});
```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.color.test').id
};
this.context.resourceManager.getColor(resource)
  .then((value: number) => {
    console.info(`getColor, result: ${value}`);
    // Print the output result: getColor, result: 4294967295
  })
  .catch((error: BusinessError) => {
    console.error(`promise getColor failed, error code: ${error.code}, message: ${error.message}.`);
  });
```

<a id="getcolor-1"></a>

## getColor

```TypeScript
getColor(resId: number): Promise<number>
```

Obtains the color value corresponding to the specified resource ID. This API uses a promise to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the color value (decimal). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/color.json
{
  "color": [
    {
      "name": "test",
      "value": "#FFFFFF"
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // Replace 'app.color.test' with the actual resource.
        this.context.resourceManager.getColor($r('app.color.test').id)
            .then((value: number) => {
                console.info(`getColor, result: ${value}`);
                // Print the output result: getColor, result: 4294967295
            })
            .catch((error: BusinessError) => {
                console.error(`promise getColor failed, error code: ${error.code}, message: ${error.message}.`);
            });
    }
}
```

<a id="getcolor-2"></a>

## getColor

```TypeScript
getColor(resource: Resource, callback: _AsyncCallback<number>): void
```

Obtains the color value corresponding to the specified resource object. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 20

**Substitutes:** [getColor](#getcolor)(resId: number, callback: _AsyncCallback&lt;number&gt;)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;number&gt; | Yes | Callback used to return the color value (decimal). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/color.json
{
  "color": [
    {
      "name": "test",
      "value": "#FFFFFF"
    }
  ]
}
```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.color.test').id
};
this.context.resourceManager.getColor(resource, (error: BusinessError, value: number) => {
  if (error != null) {
    console.error(`callback getColor failed, error code: ${error.code}, message: ${error.message}.`);
  } else {
    console.info(`getColor, result: ${value}`);
    // Print the output result: getColor, result: 4294967295
  }
});
```

<a id="getcolor-3"></a>

## getColor

```TypeScript
getColor(resource: Resource): Promise<number>
```

Obtains the color value corresponding to the specified resource object. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 20

**Substitutes:** [getColor](#getcolor)(resId: number)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the color value (decimal). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/color.json
{
  "color": [
    {
      "name": "test",
      "value": "#FFFFFF"
    }
  ]
}
```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.color.test').id
};
this.context.resourceManager.getColor(resource)
  .then((value: number) => {
    console.info(`getColor, result: ${value}`);
    // Print the output result: getColor, result: 4294967295
  })
  .catch((error: BusinessError) => {
    console.error(`promise getColor failed, error code: ${error.code}, message: ${error.message}.`);
  });
```

## getColorByName

```TypeScript
getColorByName(resName: string, callback: _AsyncCallback<number>): void
```

Obtains the color value corresponding to the specified resource name. This API uses an asynchronous callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;number&gt; | Yes | Callback used to return the color value (decimal). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/color.json
{
  "color": [
    {
      "name": "test",
      "value": "#FFFFFF"
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // Replace "test" with the actual resource.
        this.context.resourceManager.getColorByName("test", (error: BusinessError, value: number) => {
            if (error != null) {
                console.error(`callback getColorByName failed, error code: ${error.code}, message: ${error.message}.`);
            } else {
                console.info(`getColorByName, result: ${value}`);
                // Print the output result: getColorByName, result: 4294967295
            }
        });
    }
}
```

<a id="getcolorbyname-1"></a>

## getColorByName

```TypeScript
getColorByName(resName: string): Promise<number>
```

Obtains the color value corresponding to the specified resource name. This API uses a promise to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the color value (decimal). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/color.json
{
  "color": [
    {
      "name": "test",
      "value": "#FFFFFF"
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // Replace "test" with the actual resource.
        this.context.resourceManager.getColorByName("test")
            .then((value: number) => {
                console.info(`getColorByName, result: ${value}`);
                // Print the output result: getColorByName, result: 4294967295
            })
            .catch((error: BusinessError) => {
                console.error(`promise getColorByName failed, error code: ${error.code}, message: ${error.message}.`);
            });
    }
}
```

## getColorByNameSync

```TypeScript
getColorByNameSync(resName: string) : number
```

Obtains a color value based on the specified resource name. This API returns the result synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Color value (decimal) corresponding to the specified resource name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/color.json
{
  "color": [
    {
      "name": "test",
      "value": "#FFFFFF"
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "test" with the actual resource.
            let colorValue = this.context.resourceManager.getColorByNameSync("test");
            console.info(`getColorByNameSync, result: ${colorValue}`);
            // Print the output result: getColorByNameSync, result: 4294967295
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getColorByNameSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getColorSync

```TypeScript
getColorSync(resId: number) : number
```

Obtains a color value based on the specified resource ID. This API returns the result synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Color value (decimal) corresponding to the specified resource ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/color.json
{
  "color": [
    {
      "name": "test",
      "value": "#FFFFFF"
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace 'app.color.test' with the actual resource.
            let colorValue = this.context.resourceManager.getColorSync($r('app.color.test').id);
            console.info(`getColorSync, result: ${colorValue}`);
            // Print the output result: getColorSync, result: 4294967295
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getColorSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getcolorsync-1"></a>

## getColorSync

```TypeScript
getColorSync(resource: Resource) : number
```

Obtains a color value based on the specified resource object. This API returns the result synchronously.

**Since:** 10

**Deprecated since:** 20

**Substitutes:** [getColorSync](#getcolorsync)(resId: number)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Color value (decimal) corresponding to the specified resource object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/color.json
{
  "color": [
    {
      "name": "test",
      "value": "#FFFFFF"
    }
  ]
}
```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.color.test').id
};
try {
  let colorValue = this.context.resourceManager.getColorSync(resource);
  console.info(`getColorSync, result: ${colorValue}`);
  // Print the output result: getColorSync, result: 4294967295
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getColorSync failed, error code: ${code}, message: ${message}.`);
}
```

## getConfiguration

```TypeScript
getConfiguration(callback: _AsyncCallback<Configuration>): void
```

Obtains the configuration of a device. This API uses an asynchronous callback to return the result.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;[Configuration](arkts-localization-resourcemanager-configuration-c.md)&gt; | Yes | Callback used to return the device configuration. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            this.context.resourceManager.getConfiguration((error: BusinessError, config: resourceManager.Configuration) => {
                if (error != null) {
                    console.error("getConfiguration callback error is " + error);
                } else {
                    let direction = config.direction;
                    let locale = config.locale;
                }
            });
        } catch (error) {
            console.error("getConfiguration callback error is " + error);
        }
    }
}
```

<a id="getconfiguration-1"></a>

## getConfiguration

```TypeScript
getConfiguration(): Promise<Configuration>
```

Obtains the configuration of a device. This API uses a promise to return the result.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Configuration](arkts-localization-resourcemanager-configuration-c.md)&gt; | Promise used to return the device configuration. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            this.context.resourceManager.getConfiguration().then((config: resourceManager.Configuration) => {
                let direction = config.direction;
                let locale = config.locale;
            }).catch((error: BusinessError) => {
                console.error("getConfiguration promise error is " + error);
            });
        } catch (error) {
            console.error("getConfiguration promise error is " + error);
        }
    }
}
```

## getConfigurationSync

```TypeScript
getConfigurationSync(): Configuration
```

Obtains the device configuration. This API returns the result synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Return value:**

| Type | Description |
| --- | --- |
| [Configuration](arkts-localization-resourcemanager-configuration-c.md) | Device configuration. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            let value = this.context.resourceManager.getConfigurationSync();
            let direction = value.direction;
            let locale = value.locale;
        } catch (error) {
            console.error("getConfigurationSync error is " + error);
        }
    }
}
```

## getDeviceCapability

```TypeScript
getDeviceCapability(callback: _AsyncCallback<DeviceCapability>): void
```

Obtains the device capabilities of a device. This API uses an asynchronous callback to return the result.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;[DeviceCapability](arkts-localization-resourcemanager-devicecapability-c.md)&gt; | Yes | Callback used to return the device capability. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            this.context.resourceManager.getDeviceCapability((error: BusinessError, value: resourceManager.DeviceCapability) => {
                if (error != null) {
                    console.error("getDeviceCapability callback error is " + error);
                } else {
                    let screenDensity = value.screenDensity;
                    let deviceType = value.deviceType;
                }
            });
        } catch (error) {
            console.error("getDeviceCapability callback error is " + error);
        }
    }
}
```

<a id="getdevicecapability-1"></a>

## getDeviceCapability

```TypeScript
getDeviceCapability(): Promise<DeviceCapability>
```

Obtains the device capabilities of a device. This API uses a promise to return the result.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DeviceCapability](arkts-localization-resourcemanager-devicecapability-c.md)&gt; | Promise used to return the device capability. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            this.context.resourceManager.getDeviceCapability().then((value: resourceManager.DeviceCapability) => {
                let screenDensity = value.screenDensity;
                let deviceType = value.deviceType;
            }).catch((error: BusinessError) => {
                console.error("getDeviceCapability promise error is " + error);
            });
        } catch (error) {
            console.error("getDeviceCapability promise error is " + error);
        }
    }
}
```

## getDeviceCapabilitySync

```TypeScript
getDeviceCapabilitySync(): DeviceCapability
```

Obtains the device capability. This API returns the result synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Return value:**

| Type | Description |
| --- | --- |
| [DeviceCapability](arkts-localization-resourcemanager-devicecapability-c.md) | Device capability. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            let value = this.context.resourceManager.getDeviceCapabilitySync();
            let screenDensity = value.screenDensity;
            let deviceType = value.deviceType;
        } catch (error) {
            console.error("getDeviceCapabilitySync error is " + error);
        }
    }
}
```

## getDoublePluralStringByNameSync

```TypeScript
getDoublePluralStringByNameSync(resName: string, num: number, ...args: Array<string | number>): string
```

Obtains the [plural](../../../internationalization/l10n-singular-plural.md) string corresponding to the specified resource name, and replaces the format placeholders in the string in sequence using the **args** parameters. This API returns the result synchronously.

> **NOTE:** 
> 
> - Strings distinguish between singular and plural forms in all languages except Chinese. For details, see [Language Plural Rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).
> 
> - In languages such as English and German, singular/plural numbers are classified into cardinal numbers (for example, 1, 2, 3) and ordinal numbers (for example, 1st, 2nd, 3rd). This API applies only to cardinal numbers.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |
| num | number | Yes | Quantity value (a floating point number), used to obtain the corresponding string representation based on the current language's [plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html). |
| args | Array&lt;string &#124; number&gt; | Yes | Parameters for the formatted string resource. Supported parameter types include `%d`, `%f`, `%s`, `%%`, `%number$d`, `%number$f`, and `%number$s`. <br>**NOTE:** <br>- `%%` is escaped as `%`. For example, `%%d` is formatted as `%d`. <br>- In `%number$d`, `number` indicates the parameter index, starting from `1`. For example, `%1$d` uses `args[0]` for formatting, `%2$d` uses `args[1]`, and so on. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Formatted string corresponding to the specified resource name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |
| [9001008](../errorcode-resource-manager.md#9001008-failed-to-format-the-resource-obtained-based-on-resname) | Failed to format the resource obtained based on the resource name. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "format_test",
      "value": [
        {
          "quantity": "one",
          "value": "There is %d apple in the %s, the total amount is %f kg."
        },
        {
          "quantity": "other",
          "value": "There are %d apples in the %s, the total amount is %f kg."
        }
      ]
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // If num is 2.1, the single/plural type is other in the English environment.
            // The quantity field in the resource file indicates the single/plural type. Therefore, the string whose quantity is other is obtained.
            // Replace "format_test" with the actual resource.
            let pluralStr = this.context.resourceManager.getDoublePluralStringByNameSync("format_test", 2.1, 2, "basket", 0.6);
            console.info(`getDoublePluralStringByNameSync, result: ${pluralStr}`);
            // Print the output result: getDoublePluralStringByNameSync, result: There are 2 apples in the basket, the total amount is 0.6 kg.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getDoublePluralStringByNameSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getDoublePluralStringValueSync

```TypeScript
getDoublePluralStringValueSync(resId: number, num: number, ...args: Array<string | number>): string
```

Obtains the [plural](../../../internationalization/l10n-singular-plural.md) string corresponding to the specified resource ID, and replaces the format placeholders in the string in sequence using the **args** parameters. This API returns the result synchronously.

> **NOTE:** 
> 
> - Strings distinguish between singular and plural forms in all languages except Chinese. For details, see [Language Plural Rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).
> 
> - In languages such as English and German, singular/plural numbers are classified into cardinal numbers (for example, 1, 2, 3) and ordinal numbers (for example, 1st, 2nd, 3rd). This API applies only to cardinal numbers.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| num | number | Yes | Quantity value (a floating point number), used to obtain the corresponding string representation based on the current language's [plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html). |
| args | Array&lt;string &#124; number&gt; | Yes | Parameters for the formatted string resource. Supported parameter types include `%d`, `%f`, `%s`, `%%`, `%number$d`, `%number$f`, and `%number$s`. <br>**NOTE:** <br>- `%%` is escaped as `%`. For example, `%%d` is formatted as `%d`. <br>- In `%number$d`, `number` indicates the parameter index, starting from `1`. For example, `%1$d` uses `args[0]` for formatting, `%2$d` uses `args[1]`, and so on. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Formatted string corresponding to the specified resource ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |
| [9001007](../errorcode-resource-manager.md#9001007-failed-to-format-the-resource-obtained-based-on-the-current-id) | Failed to format the resource obtained based on the resource ID. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "format_test",
      "value": [
        {
          "quantity": "one",
          "value": "There is %d apple in the %s, the total amount is %f kg."
        },
        {
          "quantity": "other",
          "value": "There are %d apples in the %s, the total amount is %f kg."
        }
      ]
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // If num is 2.1, the single/plural type is other in the English environment.
            // The quantity field in the resource file indicates the single/plural type. Therefore, the string whose quantity is other is obtained.
            // Replace 'app.plural.format_test' with the actual resource.
            let pluralStr = this.context.resourceManager.getDoublePluralStringValueSync($r('app.plural.format_test').id, 2.1, 2, "basket", 0.6);
            console.info(`getDoublePluralStringValueSync, result: ${pluralStr}`);
            // Print the output result: getDoublePluralStringValueSync, result: There are 2 apples in the basket, the total amount is 0.6 kg.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getDoublePluralStringValueSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getdoublepluralstringvaluesync-2"></a>

## getDoublePluralStringValueSync

```TypeScript
getDoublePluralStringValueSync(resource: Resource, num: number, ...args: Array<string | number>): string
```

Obtains the [plural](../../../internationalization/l10n-singular-plural.md) string corresponding to the specified resource object, and replaces the format placeholders in the string in sequence using the **args** parameters. This API returns the result synchronously.

> **NOTE:** 
> 
> - Strings distinguish between singular and plural forms in all languages except Chinese. For details, see [Language Plural Rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).

**Since:** 18

**Deprecated since:** 20

**Substitutes:** [getDoublePluralStringValueSync](#getdoublepluralstringvaluesync)(resId: number, num: number, ...args: Array&lt;string | number&gt;)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |
| num | number | Yes | Quantity value (a floating point number), used to obtain the corresponding string representation based on the current language's [plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html). |
| args | Array&lt;string &#124; number&gt; | Yes | Parameters for the formatted string resource. Supported parameter types include `%d`, `%f`, `%s`, `%%`, `%number$d`, `%number$f`, and `%number$s`. <br>**NOTE:** <br>- `%%` is escaped as `%`. For example, `%%d` is formatted as `%d`. <br>- In `%number$d`, `number` indicates the parameter index, starting from `1`. For example, `%1$d` uses `args[0]` for formatting, `%2$d` uses `args[1]`, and so on. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Formatted string corresponding to the specified resource object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |
| [9001007](../errorcode-resource-manager.md#9001007-failed-to-format-the-resource-obtained-based-on-the-current-id) | Failed to format the resource obtained based on the resource ID. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "format_test",
      "value": [
        {
          "quantity": "one",
          "value": "There is %d apple in the %s, the total amount is %f kg."
        },
        {
          "quantity": "other",
          "value": "There are %d apples in the %s, the total amount is %f kg."
        }
      ]
    }
  ]
}
```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.plural.format_test').id
};

try {
  // If num is 2.1, the single/plural type is other in the English environment.
  // The quantity field in the resource file indicates the single/plural type. Therefore, the string whose quantity is other is obtained.
  let pluralStr = this.context.resourceManager.getDoublePluralStringValueSync(resource, 2.1, 2, "basket", 0.6);
  console.info(`getDoublePluralStringValueSync, result: ${pluralStr}`);
  // Print the output result: getIntPluralStringValueSync, result: There are 2 apples in the basket, the total amount is 0.6 kg.
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getDoublePluralStringValueSync failed, error code: ${code}, message: ${message}.`);
}
```

## getDrawableDescriptor

```TypeScript
getDrawableDescriptor(resId: number, density?: number, type?: number): DrawableDescriptor
```

Obtains the **DrawableDescriptor** object for icon display corresponding to the specified resource ID. This API returns the result synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| density | number | No | Screen density. The default value or value **0** indicates the default screen density. For details about the values, see [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md). |
| type | number | No | Icon type. The default value is **0**.<br>**0**: Icon resource of the application. <br>**1**: Layered icon resource of the application in the theme resource package. |

**Return value:**

| Type | Description |
| --- | --- |
| [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | **DrawableDescriptor** object corresponding to the specified resource ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { DrawableDescriptor } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace 'app.media.icon' with the actual resource.
            let drawableDescriptor:DrawableDescriptor = this.context.resourceManager.getDrawableDescriptor($r('app.media.icon').id);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getDrawableDescriptor failed, error code: ${code}, message: ${message}.`);
        }
        try {
            // Replace 'app.media.icon' with the actual resource.
            let drawableDescriptor:DrawableDescriptor = this.context.resourceManager.getDrawableDescriptor($r('app.media.icon').id, 120);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getDrawableDescriptor failed, error code: ${code}, message: ${message}.`);
        }
        try {
            // Replace 'app.media.icon' with the actual resource.
            let drawableDescriptor:DrawableDescriptor = this.context.resourceManager.getDrawableDescriptor($r('app.media.icon').id, 0, 1);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getDrawableDescriptor failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getdrawabledescriptor-1"></a>

## getDrawableDescriptor

```TypeScript
getDrawableDescriptor(resource: Resource, density?: number, type?: number): DrawableDescriptor
```

Obtains a **DrawableDescriptor** object for icon display based on the specified resource object. This API returns the result synchronously.

**Since:** 10

**Deprecated since:** 20

**Substitutes:** [getDrawableDescriptor](#getdrawabledescriptor)(resId: number, density?: number, type?: number)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |
| density | number | No | Screen density. The default value or value **0** indicates the default screen density. For details about the values, see [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md). |
| type | number | No | Icon type. The default value is **0**.<br>**0**: Icon resource of the application. <br>**1**: Layered icon resource of the application in the theme resource package. |

**Return value:**

| Type | Description |
| --- | --- |
| [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | **DrawableDescriptor** object corresponding to the specified resource ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { DrawableDescriptor } from '@kit.ArkUI';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.icon').id
};
try {
  let drawableDescriptor:DrawableDescriptor = this.context.resourceManager.getDrawableDescriptor(resource);
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getDrawableDescriptor failed, error code: ${code}, message: ${message}.`);
}
try {
  let drawableDescriptor:DrawableDescriptor = this.context.resourceManager.getDrawableDescriptor(resource, 120);
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getDrawableDescriptor failed, error code: ${code}, message: ${message}.`);
}
try {
  let drawableDescriptor:DrawableDescriptor = this.context.resourceManager.getDrawableDescriptor(resource, 0, 1);
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getDrawableDescriptor failed, error code: ${code}, message: ${message}.`);
}
```

## getDrawableDescriptorByName

```TypeScript
getDrawableDescriptorByName(resName: string, density?: number, type?: number): DrawableDescriptor
```

Obtains the **DrawableDescriptor** object for icon display corresponding to the specified resource name. This API returns the result synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |
| density | number | No | Screen density. The default value or value **0** indicates the default screen density. For details about the values, see [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md). |
| type | number | No | Icon type. The default value is **0**.<br>**0**: Icon resource of the application. <br>**1**: Layered icon resource of the application in the theme resource package. |

**Return value:**

| Type | Description |
| --- | --- |
| [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) | **DrawableDescriptor** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { DrawableDescriptor } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "icon" with the actual resource.
            let drawableDescriptor:DrawableDescriptor = this.context.resourceManager.getDrawableDescriptorByName('icon');
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getDrawableDescriptorByName failed, error code: ${code}, message: ${message}.`);
        }
        try {
            // Replace "icon" with the actual resource.
            let drawableDescriptor:DrawableDescriptor = this.context.resourceManager.getDrawableDescriptorByName('icon', 120);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getDrawableDescriptorByName failed, error code: ${code}, message: ${message}.`);
        }
        try {
            // Replace "icon" with the actual resource.
            let drawableDescriptor:DrawableDescriptor = this.context.resourceManager.getDrawableDescriptorByName('icon', 0, 1);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getDrawableDescriptorByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getIntPluralStringByNameSync

```TypeScript
getIntPluralStringByNameSync(resName: string, num: number, ...args: Array<string | number>): string
```

Obtains the [plural](../../../internationalization/l10n-singular-plural.md) string corresponding to the specified resource name, and replaces the format placeholders in the string in sequence using the **args** parameters. This API returns the result synchronously.

> **NOTE:** 
> 
> - Strings distinguish between singular and plural forms in all languages except Chinese. For details, see [Language Plural Rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).
> 
> - In languages such as English and German, singular/plural numbers are classified into cardinal numbers (for example, 1, 2, 3) and ordinal numbers (for example, 1st, 2nd, 3rd). This API applies only to cardinal numbers.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |
| num | number | Yes | Integer number used to obtain the corresponding string representation based on the current language's [plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html). |
| args | Array&lt;string &#124; number&gt; | Yes | Parameters for the formatted string resource. Supported parameter types include `%d`, `%f`, `%s`, `%%`, `%number$d`, `%number$f`, and `%number$s`. <br>**NOTE:** <br>- `%%` is escaped as `%`. For example, `%%d` is formatted as `%d`. <br>- In `%number$d`, `number` indicates the parameter index, starting from `1`. For example, `%1$d` uses `args[0]` for formatting, `%2$d` uses `args[1]`, and so on. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Formatted string corresponding to the specified resource name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |
| [9001008](../errorcode-resource-manager.md#9001008-failed-to-format-the-resource-obtained-based-on-resname) | Failed to format the resource obtained based on the resource name. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "format_test",
      "value": [
        {
          "quantity": "one",
          "value": "There is %d apple in the %s, the total amount is %f kg."
        },
        {
          "quantity": "other",
          "value": "There are %d apples in the %s, the total amount is %f kg."
        }
      ]
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // If num is 1, the single/plural type is one in the English environment.
            // The quantity field in the resource file indicates the single/plural type. Therefore, the string whose quantity is one is obtained.
            // Replace "format_test" with the actual resource.
            let pluralStr = this.context.resourceManager.getIntPluralStringByNameSync("format_test", 1, 1, "basket", 0.3);
            console.info(`getIntPluralStringByNameSync, result: ${pluralStr}`);
            // Print the output result: getIntPluralStringByNameSync, result: There is 1 apple in the basket, the total amount is 0.3 kg.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getIntPluralStringByNameSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getIntPluralStringValueSync

```TypeScript
getIntPluralStringValueSync(resId: number, num: number,...args: Array<string | number>): string
```

Obtains the [plural](../../../internationalization/l10n-singular-plural.md) string corresponding to the specified resource ID, and replaces the format placeholders in the string in sequence using the **args** parameters. This API returns the result synchronously.

> **NOTE:** 
> 
> - Strings distinguish between singular and plural forms in all languages except Chinese. For details, see [Language Plural Rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).
> 
> - In languages such as English and German, singular/plural numbers are classified into cardinal numbers (for example, 1, 2, 3) and ordinal numbers (for example, 1st, 2nd, 3rd). This API applies only to cardinal numbers.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| num | number | Yes | Integer number used to obtain the corresponding string representation based on the current language's [plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html). |
| args | Array&lt;string &#124; number&gt; | Yes | Parameters for the formatted string resource. Supported parameter types include `%d`, `%f`, `%s`, `%%`, `%number$d`, `%number$f`, and `%number$s`. <br>**NOTE:** <br>- `%%` is escaped as `%`. For example, `%%d` is formatted as `%d`. <br>- In `%number$d`, `number` indicates the parameter index, starting from `1`. For example, `%1$d` uses `args[0]` for formatting, `%2$d` uses `args[1]`, and so on. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Formatted string corresponding to the specified resource ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |
| [9001007](../errorcode-resource-manager.md#9001007-failed-to-format-the-resource-obtained-based-on-the-current-id) | Failed to format the resource obtained based on the resource ID. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "format_test",
      "value": [
        {
          "quantity": "one",
          "value": "There is %d apple in the %s, the total amount is %f kg."
        },
        {
          "quantity": "other",
          "value": "There are %d apples in the %s, the total amount is %f kg."
        }
      ]
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // If num is 1, the single/plural type is one in the English environment.
            // The quantity field in the resource file indicates the single/plural type. Therefore, the string whose quantity is one is obtained.
            // Replace 'app.plural.format_test' with the actual resource.
            let pluralStr = this.context.resourceManager.getIntPluralStringValueSync($r('app.plural.format_test').id, 1, 1, "basket", 0.3);
            console.info(`getIntPluralStringValueSync, result: ${pluralStr}`);
            // Print the output result: getIntPluralStringValueSync, result: There is 1 apple in the basket, the total amount is 0.3 kg.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getIntPluralStringValueSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getintpluralstringvaluesync-2"></a>

## getIntPluralStringValueSync

```TypeScript
getIntPluralStringValueSync(resource: Resource, num: number, ...args: Array<string | number>): string
```

Obtains the [plural](../../../internationalization/l10n-singular-plural.md) string corresponding to the specified resource object, and replaces the format placeholders in the string in sequence using the **args** parameters. This API returns the result synchronously.

> **NOTE:** 
> 
> - Strings distinguish between singular and plural forms in all languages except Chinese. For details, see [Language Plural Rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).

**Since:** 18

**Deprecated since:** 20

**Substitutes:** [getIntPluralStringValueSync](#getintpluralstringvaluesync)(resId: number, num: number,...args: Array&lt;string | number&gt;)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |
| num | number | Yes | Integer number used to obtain the corresponding string representation based on the current language's [plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html). |
| args | Array&lt;string &#124; number&gt; | Yes | Parameters for the formatted string resource. Supported parameter types include `%d`, `%f`, `%s`, `%%`, `%number$d`, `%number$f`, and `%number$s`. <br>**NOTE:** <br>- `%%` is escaped as `%`. For example, `%%d` is formatted as `%d`. <br>- In `%number$d`, `number` indicates the parameter index, starting from `1`. For example, `%1$d` uses `args[0]` for formatting, `%2$d` uses `args[1]`, and so on. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Formatted string corresponding to the specified resource object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |
| [9001007](../errorcode-resource-manager.md#9001007-failed-to-format-the-resource-obtained-based-on-the-current-id) | Failed to format the resource obtained based on the resource ID. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "format_test",
      "value": [
        {
          "quantity": "one",
          "value": "There is %d apple in the %s, the total amount is %f kg."
        },
        {
          "quantity": "other",
          "value": "There are %d apples in the %s, the total amount is %f kg."
        }
      ]
    }
  ]
}
```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.plural.format_test').id
};

try {
  // If num is 1, the single/plural type is one in the English environment.
  // The quantity field in the resource file indicates the single/plural type. Therefore, the string whose quantity is one is obtained.
  let pluralStr = this.context.resourceManager.getIntPluralStringValueSync(resource, 1, 1, "basket", 0.3);
  console.info(`getIntPluralStringValueSync, result: ${pluralStr}`);
  // Print the output result: getIntPluralStringValueSync, result: There is 1 apple in the basket, the total amount is 0.3 kg.
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getIntPluralStringValueSync failed, error code: ${code}, message: ${message}.`);
}
```

## getLocales

```TypeScript
getLocales(includeSystem?: boolean): Array<string>
```

Obtains the language list of an application.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| includeSystem | boolean | No | Whether system resources are included. The default value is **false**.<br> - **false**: Only application resources are included. <br> - **true**: Both system and application resources are included. <br>If the value of **includeSystem** is invalid, the language list of system resources will be returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Language list. The strings in the list are comprised of the language, script (optional), and region (optional), which are connected by a hyphen (-). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            this.context.resourceManager.getLocales(); // Obtain only the language list of application resources.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getLocales failed, error code: ${code}, message: ${message}.`);
        }

        try {
            resourceManager.getSysResourceManager().getLocales(); // Obtain only the language list of system resources.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getLocales failed, error code: ${code}, message: ${message}.`);
        }

        try {
            this.context.resourceManager.getLocales(true); // Obtain the language list of application resources and resources.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getLocales failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getMedia

```TypeScript
getMedia(resId: number, callback: AsyncCallback<Uint8Array>): void
```

Obtains the content of the media file corresponding to the specified resource ID. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [getMediaContent](#getmediacontent)(resId: number, callback: _AsyncCallback&lt;Uint8Array&gt;)

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| callback | [AsyncCallback](arkts-localization-resourcemanager-asynccallback-i.md)&lt;Uint8Array&gt; | Yes | Callback used to return the media file content. |

**Examples**

```TypeScript
resourceManager.getResourceManager((error, mgr) => {
    mgr.getMedia($r('app.media.test').id, (error: Error, value: Uint8Array) => {
        if (error != null) {
            console.error("error is " + error);
        } else {
            let media = value;
        }
    });
});
```

<a id="getmedia-1"></a>

## getMedia

```TypeScript
getMedia(resId: number): Promise<Uint8Array>
```

Obtains the content of the media file corresponding to the specified resource ID. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [getMediaContent](#getmediacontent)(resId: number)

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise used to return the media file content. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.getMedia($r('app.media.test').id).then((value: Uint8Array) => {
        let media = value;
    }).catch((error: BusinessError) => {
        console.error("getMedia promise error is " + error);
    });
});
```

## getMediaBase64

```TypeScript
getMediaBase64(resId: number, callback: AsyncCallback<string>): void
```

Obtains the Base64 encoding of the image resource corresponding to the specified resource ID. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [getMediaContentBase64](#getmediacontentbase64)(resId: number, callback: _AsyncCallback&lt;string&gt;)

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| callback | [AsyncCallback](arkts-localization-resourcemanager-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the Base64 encoding of the image. |

**Examples**

```TypeScript
resourceManager.getResourceManager((error, mgr) => {
    mgr.getMediaBase64($r('app.media.test').id, ((error: Error, value: string) => {
        if (error != null) {
            console.error("error is " + error);
        } else {
            let media = value;
        }
    });
});
```

<a id="getmediabase64-1"></a>

## getMediaBase64

```TypeScript
getMediaBase64(resId: number): Promise<string>
```

Obtains the Base64 encoding of the image resource corresponding to the specified resource ID. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [getMediaContentBase64](#getmediacontentbase64)(resId: number)

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the Base64 encoding of the image. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.getMediaBase64($r('app.media.test').id).then((value: string) => {
        let media = value;
    }).catch((error: BusinessError) => {
        console.error("getMediaBase64 promise error is " + error);
    });
});
```

## getMediaBase64ByName

```TypeScript
getMediaBase64ByName(resName: string, callback: _AsyncCallback<string>): void
```

Obtains the Base64 encoding of the image resource corresponding to the specified resource name. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;string&gt; | Yes | Callback used to return the Base64 encoding of the image. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "test" with the actual resource.
            this.context.resourceManager.getMediaBase64ByName("test", (error: BusinessError, value: string) => {
                if (error != null) {
                    console.error("error is " + error);
                } else {
                    let media = value;
                }
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`callback getMediaBase64ByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getmediabase64byname-1"></a>

## getMediaBase64ByName

```TypeScript
getMediaBase64ByName(resName: string, density: number, callback: _AsyncCallback<string>): void
```

Obtains the Base64 encoding of the image resource for the specified screen density corresponding to the specified resource name. This API uses an asynchronous callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |
| density | number | Yes | Screen density. The value **0** indicates the default screen density. For details about the values, see [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md). |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;string&gt; | Yes | Callback used to return the Base64 encoding of the image. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "test" with the actual resource.
            this.context.resourceManager.getMediaBase64ByName("test", 120, (error: BusinessError, value: string) => {
                if (error != null) {
                    console.error(`callback getMediaBase64ByName failed, error code: ${error.code}, message: ${error.message}.`);
                } else {
                    let media = value;
                }
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`callback getMediaBase64ByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getmediabase64byname-2"></a>

## getMediaBase64ByName

```TypeScript
getMediaBase64ByName(resName: string): Promise<string>
```

Obtains the Base64 encoding of the image resource corresponding to the specified resource name. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the Base64 encoding of the image. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "test" with the actual resource.
            this.context.resourceManager.getMediaBase64ByName("test").then((value: string) => {
                let media = value;
            }).catch((error: BusinessError) => {
                console.error("getMediaBase64ByName promise error is " + error);
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`promise getMediaBase64ByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getmediabase64byname-3"></a>

## getMediaBase64ByName

```TypeScript
getMediaBase64ByName(resName: string, density: number): Promise<string>
```

Obtains the Base64 encoding of the image resource for the specified screen density corresponding to the specified resource name. This API uses a promise to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |
| density | number | Yes | Screen density. The value **0** indicates the default screen density. For details about the values, see [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the Base64 encoding of the image. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "test" with the actual resource.
            this.context.resourceManager.getMediaBase64ByName("test", 120).then((value: string) => {
                let media = value;
            }).catch((error: BusinessError) => {
                console.error(`promise getMediaBase64ByName failed, error code: ${error.code}, message: ${error.message}.`);
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`promise getMediaBase64ByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getMediaBase64ByNameSync

```TypeScript
getMediaBase64ByNameSync(resName: string, density?: number): string
```

Obtains an image's Base64 encoding for the default or specified screen density based on the specified resource name. This API returns the result synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |
| density | number | No | Screen density. The default value or value **0** indicates the default screen density. For details about the values, see [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| string | Base64 encoding of the image corresponding to the specified resource name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "test" with the actual resource.
            this.context.resourceManager.getMediaBase64ByNameSync("test"); // Default screen density
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getMediaBase64ByNameSync failed, error code: ${code}, message: ${message}.`);
        }

        try {
            // Replace "test" with the actual resource.
            this.context.resourceManager.getMediaBase64ByNameSync("test", 120); // Specified screen density
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getMediaBase64ByNameSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getMediaByName

```TypeScript
getMediaByName(resName: string, callback: _AsyncCallback<Uint8Array>): void
```

Obtains the content of the media file corresponding to the specified resource name. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;Uint8Array&gt; | Yes | Callback used to return the media file content. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "test" with the actual resource.
            this.context.resourceManager.getMediaByName("test", (error: BusinessError, value: Uint8Array) => {
                if (error != null) {
                    console.error("error is " + error);
                } else {
                    let media = value;
                }
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`callback getMediaByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getmediabyname-1"></a>

## getMediaByName

```TypeScript
getMediaByName(resName: string, density: number, callback: _AsyncCallback<Uint8Array>): void
```

Obtains the media file content for the specified screen density based on the specified resource name. This API uses an asynchronous callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |
| density | number | Yes | Screen density. The value **0** indicates the default screen density. For details about the values, see [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md). |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;Uint8Array&gt; | Yes | Callback used to return the media file content. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "test" with the actual resource.
            this.context.resourceManager.getMediaByName("test", 120, (error: BusinessError, value: Uint8Array) => {
                if (error != null) {
                    console.error(`callback getMediaByName failed, error code: ${error.code}, message: ${error.message}.`);
                } else {
                    let media = value;
                }
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`callback getMediaByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getmediabyname-2"></a>

## getMediaByName

```TypeScript
getMediaByName(resName: string): Promise<Uint8Array>
```

Obtains the content of the media file corresponding to the specified resource name. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise used to return the media file content. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "test" with the actual resource.
            this.context.resourceManager.getMediaByName("test").then((value: Uint8Array) => {
                let media = value;
            }).catch((error: BusinessError) => {
                console.error("getMediaByName promise error is " + error);
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`promise getMediaByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getmediabyname-3"></a>

## getMediaByName

```TypeScript
getMediaByName(resName: string, density: number): Promise<Uint8Array>
```

Obtains the media file content for the specified screen density based on the specified resource name. This API uses a promise to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |
| density | number | Yes | Screen density. The value **0** indicates the default screen density. For details about the values, see [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise used to return the media file content. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "test" with the actual resource.
            this.context.resourceManager.getMediaByName("test", 120).then((value: Uint8Array) => {
                let media = value;
            }).catch((error: BusinessError) => {
                console.error(`promise getMediaByName failed, error code: ${error.code}, message: ${error.message}.`);
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`promise getMediaByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getMediaByNameSync

```TypeScript
getMediaByNameSync(resName: string, density?: number): Uint8Array
```

Obtains the media file content for the default or specified screen density based on the specified resource name. This API returns the result synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |
| density | number | No | Screen density. The default value or value **0** indicates the default screen density. For details about the values, see [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | Promise used to return the result, which is the content of the media file corresponding to the specified resource name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "test" with the actual resource.
            this.context.resourceManager.getMediaByNameSync("test"); // Default screen density
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getMediaByNameSync failed, error code: ${code}, message: ${message}.`);
        }

        try {
            // Replace "test" with the actual resource.
            this.context.resourceManager.getMediaByNameSync("test", 120); // Specified screen density
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getMediaByNameSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getMediaContent

```TypeScript
getMediaContent(resource: Resource, callback: _AsyncCallback<Uint8Array>): void
```

Obtains the content of the media file corresponding to the specified resource object. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** [getMediaContent](#getmediacontent)(resId: number, callback: _AsyncCallback&lt;Uint8Array&gt;)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;Uint8Array&gt; | Yes | Callback used to return the media file content. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.test').id
};
try {
  this.context.resourceManager.getMediaContent(resource, (error: BusinessError, value: Uint8Array) => {
    if (error != null) {
      console.error("error is " + error);
    } else {
      let media = value;
    }
  });
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`callback getMediaContent failed, error code: ${code}, message: ${message}.`);
}
```

<a id="getmediacontent-1"></a>

## getMediaContent

```TypeScript
getMediaContent(resource: Resource, density: number, callback: _AsyncCallback<Uint8Array>): void
```

Obtains the media file content for the specified screen density based on the specified resource object. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 20

**Substitutes:** [getMediaContent](#getmediacontent)(resId: number, density: number, callback: _AsyncCallback&lt;Uint8Array&gt;)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |
| density | number | Yes | Screen density. The value **0** indicates the default screen density. For details about the values, see [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md). |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;Uint8Array&gt; | Yes | Callback used to return the media file content. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.test').id
};
try {
  this.context.resourceManager.getMediaContent(resource, 120, (error: BusinessError, value: Uint8Array) => {
    if (error != null) {
      console.error(`callback getMediaContent failed, error code: ${error.code}, message: ${error.message}.`);
    } else {
      let media = value;
    }
  });
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`callback getMediaContent failed, error code: ${code}, message: ${message}.`);
}
```

<a id="getmediacontent-2"></a>

## getMediaContent

```TypeScript
getMediaContent(resource: Resource): Promise<Uint8Array>
```

Obtains the content of the media file corresponding to the specified resource object. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** [getMediaContent](#getmediacontent)(resId: number)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise used to return the media file content. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.test').id
};
try {
  this.context.resourceManager.getMediaContent(resource).then((value: Uint8Array) => {
    let media = value;
  }).catch((error: BusinessError) => {
    console.error("getMediaContent promise error is " + error);
  });
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`promise getMediaContent failed, error code: ${code}, message: ${message}.`);
}
```

<a id="getmediacontent-3"></a>

## getMediaContent

```TypeScript
getMediaContent(resource: Resource, density: number): Promise<Uint8Array>
```

Obtains the media file content for the specified screen density based on the specified resource object. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 20

**Substitutes:** [getMediaContent](#getmediacontent)(resId: number, density: number)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |
| density | number | Yes | Screen density. The value **0** indicates the default screen density. For details about the values, see [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise used to return the media file content. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.test').id
};
try {
  this.context.resourceManager.getMediaContent(resource, 120).then((value: Uint8Array) => {
    let media = value;
  }).catch((error: BusinessError) => {
    console.error(`promise getMediaContent failed, error code: ${error.code}, message: ${error.message}.`);
  });
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`promise getMediaContent failed, error code: ${code}, message: ${message}.`);
}
```

<a id="getmediacontent-4"></a>

## getMediaContent

```TypeScript
getMediaContent(resId: number, callback: _AsyncCallback<Uint8Array>): void
```

Obtains the content of the media file corresponding to the specified resource ID. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;Uint8Array&gt; | Yes | Callback used to return the media file content. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace 'app.media.test' with the actual resource.
            this.context.resourceManager.getMediaContent($r('app.media.test').id,
                (error: BusinessError, value: Uint8Array) => {
                    if (error != null) {
                        console.error("error is " + error);
                    } else {
                        let media = value;
                    }
                });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`callback getMediaContent failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getmediacontent-5"></a>

## getMediaContent

```TypeScript
getMediaContent(resId: number, density: number, callback: _AsyncCallback<Uint8Array>): void
```

Obtains the media file content for the specified screen density based on the specified resource ID. This API uses an asynchronous callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| density | number | Yes | Screen density. The value **0** indicates the default screen density. For details about the values, see [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md). |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;Uint8Array&gt; | Yes | Callback used to return the media file content. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace 'app.media.test' with the actual resource.
            this.context.resourceManager.getMediaContent($r('app.media.test').id, 120, (error: BusinessError, value: Uint8Array) => {
                if (error != null) {
                    console.error(`callback getMediaContent failed, error code: ${error.code}, message: ${error.message}.`);
                } else {
                    let media = value;
                }
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`callback getMediaContent failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getmediacontent-6"></a>

## getMediaContent

```TypeScript
getMediaContent(resId: number): Promise<Uint8Array>
```

Obtains the content of the media file corresponding to the specified resource ID. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise used to return the media file content. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace 'app.media.test' with the actual resource.
            this.context.resourceManager.getMediaContent($r('app.media.test').id).then((value: Uint8Array) => {
                let media = value;
            }).catch((error: BusinessError) => {
                console.error("getMediaContent promise error is " + error);
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`promise getMediaContent failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getmediacontent-7"></a>

## getMediaContent

```TypeScript
getMediaContent(resId: number, density: number): Promise<Uint8Array>
```

Obtains the media file content for the specified screen density based on the specified resource ID. This API uses a promise to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| density | number | Yes | Screen density. The value **0** indicates the default screen density. For details about the values, see [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise used to return the media file content. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace 'app.media.test' with the actual resource.
            this.context.resourceManager.getMediaContent($r('app.media.test').id, 120).then((value: Uint8Array) => {
                let media = value;
            }).catch((error: BusinessError) => {
                console.error(`promise getMediaContent failed, error code: ${error.code}, message: ${error.message}.`);
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`promise getMediaContent failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getMediaContentBase64

```TypeScript
getMediaContentBase64(resource: Resource, callback: _AsyncCallback<string>): void
```

Obtains the Base64 encoding of the image resource corresponding to the specified resource object. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** [getMediaContentBase64](#getmediacontentbase64)(resId: number, callback: _AsyncCallback&lt;string&gt;)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;string&gt; | Yes | Callback used to return the Base64 encoding of the image. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.test').id
};
try {
  this.context.resourceManager.getMediaContentBase64(resource, (error: BusinessError, value: string) => {
    if (error != null) {
      console.error("error is " + error);
    } else {
      let media = value;
    }
  });
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`callback getMediaContentBase64 failed, error code: ${code}, message: ${message}.`);
}
```

<a id="getmediacontentbase64-1"></a>

## getMediaContentBase64

```TypeScript
getMediaContentBase64(resource: Resource, density: number, callback: _AsyncCallback<string>): void
```

Obtains the Base64 encoding of the image resource corresponding to the specified resource object and the specified screen density. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 20

**Substitutes:** [getMediaContentBase64](#getmediacontentbase64)(resId: number, density: number, callback: _AsyncCallback&lt;string&gt;)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |
| density | number | Yes | Screen density. The value **0** indicates the default screen density. For details about the values, see [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md). |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;string&gt; | Yes | Callback used to return the Base64 encoding of the image. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.test').id
};
try {
  this.context.resourceManager.getMediaContentBase64(resource, 120, (error: BusinessError, value: string) => {
    if (error != null) {
      console.error(`callback getMediaContentBase64 failed, error code: ${error.code}, message: ${error.message}.`);
    } else {
      let media = value;
    }
  });
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`callback getMediaContentBase64 failed, error code: ${code}, message: ${message}.`);
}
```

<a id="getmediacontentbase64-2"></a>

## getMediaContentBase64

```TypeScript
getMediaContentBase64(resource: Resource): Promise<string>
```

Obtains the Base64 encoding of the image resource corresponding to the specified resource object. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** [getMediaContentBase64](#getmediacontentbase64)(resId: number)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the Base64 encoding of the image. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.test').id
};
try {
  this.context.resourceManager.getMediaContentBase64(resource).then((value: string) => {
    let media = value;
  }).catch((error: BusinessError) => {
    console.error("getMediaContentBase64 promise error is " + error);
  });
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`promise getMediaContentBase64 failed, error code: ${code}, message: ${message}.`);
}
```

<a id="getmediacontentbase64-3"></a>

## getMediaContentBase64

```TypeScript
getMediaContentBase64(resource: Resource, density: number): Promise<string>
```

Obtains the Base64 encoding of the image resource corresponding to the specified resource object and the specified screen density. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 20

**Substitutes:** [getMediaContentBase64](#getmediacontentbase64)(resId: number, density: number)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |
| density | number | Yes | Screen density. The value **0** indicates the default screen density. For details about the values, see [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the Base64 encoding of the image. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.test').id
};
try {
  this.context.resourceManager.getMediaContentBase64(resource, 120).then((value: string) => {
    let media = value;
  }).catch((error: BusinessError) => {
    console.error(`promise getMediaContentBase64 failed, error code: ${error.code}, message: ${error.message}.`);
  });
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`promise getMediaContentBase64 failed, error code: ${code}, message: ${message}.`);
}
```

<a id="getmediacontentbase64-4"></a>

## getMediaContentBase64

```TypeScript
getMediaContentBase64(resId: number, callback: _AsyncCallback<string>): void
```

Obtains the Base64 encoding of the image resource corresponding to the specified resource ID. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;string&gt; | Yes | Callback used to return the Base64 encoding of the image. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace 'app.media.test' with the actual resource.
            this.context.resourceManager.getMediaContentBase64($r('app.media.test').id, (error: BusinessError, value: string) => {
                if (error != null) {
                    console.error("error is " + error);
                } else {
                    let media = value;
                }
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`callback getMediaContentBase64 failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getmediacontentbase64-5"></a>

## getMediaContentBase64

```TypeScript
getMediaContentBase64(resId: number, density: number, callback: _AsyncCallback<string>): void
```

Obtains the Base64 encoding of the image resource corresponding to the specified resource ID and the specified screen density. This API uses an asynchronous callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| density | number | Yes | Screen density. The value **0** indicates the default screen density. For details about the values, see [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md). |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;string&gt; | Yes | Callback used to return the Base64 encoding of the image. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace 'app.media.test' with the actual resource.
            this.context.resourceManager.getMediaContentBase64($r('app.media.test').id, 120, (error: BusinessError, value: string) => {
                if (error != null) {
                    console.error(`callback getMediaContentBase64 failed, error code: ${error.code}, message: ${error.message}.`);
                } else {
                    let media = value;
                }
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`callback getMediaContentBase64 failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getmediacontentbase64-6"></a>

## getMediaContentBase64

```TypeScript
getMediaContentBase64(resId: number): Promise<string>
```

Obtains the Base64 encoding of the image resource corresponding to the specified resource ID. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the Base64 encoding of the image. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace 'app.media.test' with the actual resource.
            this.context.resourceManager.getMediaContentBase64($r('app.media.test').id).then((value: string) => {
                let media = value;
            }).catch((error: BusinessError) => {
                console.error("getMediaContentBase64 promise error is " + error);
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`promise getMediaContentBase64 failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getmediacontentbase64-7"></a>

## getMediaContentBase64

```TypeScript
getMediaContentBase64(resId: number, density: number): Promise<string>
```

Obtains the Base64 encoding of the image resource corresponding to the specified resource ID and the specified screen density. This API uses a promise to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| density | number | Yes | Screen density. The value **0** indicates the default screen density. For details about the values, see [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the Base64 encoding of the image. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace 'app.media.test' with the actual resource.
            this.context.resourceManager.getMediaContentBase64($r('app.media.test').id, 120).then((value: string) => {
                let media = value;
            }).catch((error: BusinessError) => {
                console.error(`promise getMediaContentBase64 failed, error code: ${error.code}, message: ${error.message}.`);
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`promise getMediaContentBase64 failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getMediaContentBase64Sync

```TypeScript
getMediaContentBase64Sync(resId: number, density?: number): string
```

Obtains an image's Base64 encoding for the default or specified screen density based on the specified resource ID. This API returns the result synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| density | number | No | Screen density. The default value or value **0** indicates the default screen density. For details about the values, see [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| string | Base64 encoding of the image corresponding to the specified resource ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace 'app.media.test' with the actual resource.
            this.context.resourceManager.getMediaContentBase64Sync($r('app.media.test').id); // Default screen density
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getMediaContentBase64Sync failed, error code: ${code}, message: ${message}.`);
        }

        try {
            // Replace 'app.media.test' with the actual resource.
            this.context.resourceManager.getMediaContentBase64Sync($r('app.media.test').id, 120); // Specified screen density
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getMediaContentBase64Sync failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getmediacontentbase64sync-1"></a>

## getMediaContentBase64Sync

```TypeScript
getMediaContentBase64Sync(resource: Resource, density?: number): string
```

Obtains an image's Base64 encoding for the default or specified screen density based on the specified resource object. This API returns the result synchronously.

**Since:** 10

**Deprecated since:** 20

**Substitutes:** [getMediaContentBase64Sync](#getmediacontentbase64sync)(resId: number, density?: number)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |
| density | number | No | Screen density. The default value or value **0** indicates the default screen density. For details about the values, see [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| string | Base64 encoding of the image corresponding to the specified resource object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.test').id
};
try {
  this.context.resourceManager.getMediaContentBase64Sync(resource); // Default screen density
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getMediaContentBase64Sync failed, error code: ${code}, message: ${message}.`);
}

try {
  this.context.resourceManager.getMediaContentBase64Sync(resource, 120); // Specified screen density
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getMediaContentBase64Sync failed, error code: ${code}, message: ${message}.`);
}
```

## getMediaContentSync

```TypeScript
getMediaContentSync(resId: number, density?: number): Uint8Array
```

Obtains the media file content for the default or specified screen density based on the specified resource ID. This API returns the result synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| density | number | No | Screen density. The default value or value **0** indicates the default screen density. For details about the values, see [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | Content of the media file corresponding to the specified resource ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace 'app.media.test' with the actual resource.
            this.context.resourceManager.getMediaContentSync($r('app.media.test').id); // Default screen density
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getMediaContentSync failed, error code: ${code}, message: ${message}.`);
        }

        try {
            // Replace 'app.media.test' with the actual resource.
            this.context.resourceManager.getMediaContentSync($r('app.media.test').id, 120); // Specified screen density
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getMediaContentSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getmediacontentsync-1"></a>

## getMediaContentSync

```TypeScript
getMediaContentSync(resource: Resource, density?: number): Uint8Array
```

Obtains the media file content for the default or specified screen density based on the specified resource object. This API returns the result synchronously.

**Since:** 10

**Deprecated since:** 20

**Substitutes:** [getMediaContentSync](#getmediacontentsync)(resId: number, density?: number)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |
| density | number | No | Screen density. The default value or value **0** indicates the default screen density. For details about the values, see [ScreenDensity](arkts-localization-resourcemanager-screendensity-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | Content of the media file corresponding to the specified resource object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |

**Examples**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.media.test').id
};
try {
  this.context.resourceManager.getMediaContentSync(resource); // Default screen density
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getMediaContentSync failed, error code: ${code}, message: ${message}.`);
}

try {
  this.context.resourceManager.getMediaContentSync(resource, 120); // Specified screen density
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getMediaContentSync failed, error code: ${code}, message: ${message}.`);
}
```

## getNumber

```TypeScript
getNumber(resId: number): number
```

Obtains an integer or float number based on the specified resource ID. This API returns the result synchronously.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Integer or float value corresponding to the specified resource ID. <br>For resources of the integer type, the original value defined in the resource file is returned. <br>For resources of the float type, the original value defined in the resource file is returned if no unit is specified. If the unit is vp or fp, the converted pixel (px) value is returned. The conversion formula is: Pixel value = Original value × `densityPixels`. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/integer.json
{
  "integer": [
    {
      "name": "integer_test",
      "value": 100
    }
  ]
}
```

```TypeScript
// Resource file path: src/main/resources/base/element/float.json
{
  "float": [
    {
      "name": "float_test",
      "value": "30.6vp"
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { display } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // An integer refers to the original value.
            // Replace 'app.integer.integer_test' with the actual resource.
            let intValue = this.context.resourceManager.getNumber($r('app.integer.integer_test').id);
            console.info(`getNumber, int value: ${intValue}`);
            // Print the output result: getNumber, int value: 100
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getNumber failed, error code: ${code}, message: ${message}.`);
        }

        try {
            // A float number without a unit indicates the original value, and a float number with the unit of vp or fp indicates the px value (float number with the unit of vp or fp = original value x densityPixels).
            // Replace 'app.float.float_test' with the actual resource.
            let floatValue = this.context.resourceManager.getNumber($r('app.float.float_test').id);
            console.info(`getNumber, densityPixels: ${display.getDefaultDisplaySync().densityPixels}, float value: ${floatValue}`);
            // Print the output result: getNumber, densityPixels: 3.25, float value: 99.45000457763672
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getNumber failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getnumber-1"></a>

## getNumber

```TypeScript
getNumber(resource: Resource): number
```

Obtains an integer or float number based on the specified resource object. This API returns the result synchronously.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** [getNumber](#getnumber)(resId: number)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Integer or float number. <br>For resources of the integer type, the original value defined in the resource file is returned. <br>For resources of the float type, the original value defined in the resource file is returned if no unit is specified. If the unit is vp or fp, the converted pixel (px) value is returned. The conversion formula is: Pixel value = Original value × `densityPixels`. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/integer.json
{
  "integer": [
    {
      "name": "integer_test",
      "value": 100
    }
  ]
}
```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.integer.integer_test').id
};

try {
  let intValue = this.context.resourceManager.getNumber(resource);
  console.info(`getNumber, int value: ${intValue}`);
  // Print the output result: getNumber, int value: 100
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getNumber failed, error code: ${code}, message: ${message}.`);
}
```

## getNumberByName

```TypeScript
getNumberByName(resName: string): number
```

Obtains an integer or float number based on the specified resource name. This API returns the result synchronously.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Integer or float value corresponding to the specified resource name. <br>For resources of the integer type, the original value defined in the resource file is returned. <br>For resources of the float type, the original value defined in the resource file is returned if no unit is specified. If the unit is vp or fp, the converted pixel (px) value is returned. The conversion formula is: Pixel value = Original value × `densityPixels`. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/integer.json
{
  "integer": [
    {
      "name": "integer_test",
      "value": 100
    }
  ]
}
```

```TypeScript
// Resource file path: src/main/resources/base/element/float.json
{
  "float": [
    {
      "name": "float_test",
      "value": "30.6vp"
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { display } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // An integer refers to the original value.
            // Replace "integer_test" with the actual resource.
            let intValue = this.context.resourceManager.getNumberByName("integer_test");
            console.info(`getNumberByName, int value: ${intValue}`);
            // Print the output result: getNumberByName, int value: 100
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getNumberByName failed, error code: ${code}, message: ${message}.`);
        }

        try {
            // A float number without a unit indicates the original value, and a float number with the unit of vp or fp indicates the px value (float number with the unit of vp or fp = original value x densityPixels).
            // Replace "float_test" with the actual resource.
            let floatValue = this.context.resourceManager.getNumberByName("float_test");
            console.info(`getNumberByName, densityPixels: ${display.getDefaultDisplaySync().densityPixels}, float value: ${floatValue}`);
            // Print the output result: getNumberByName, densityPixels: 3.25, float value: 99.45000457763672
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getNumberByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getOverrideConfiguration

```TypeScript
getOverrideConfiguration(): Configuration
```

Obtains the configuration of differentiated resources. This API returns the result synchronously.

For both the common resource management object and the differentiated resource management object obtained through the [getOverrideResourceManager](#getoverrideresourcemanager) API, this API returns the same configuration information.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.ResourceManager

**Return value:**

| Type | Description |
| --- | --- |
| [Configuration](arkts-localization-resourcemanager-configuration-c.md) | Configuration of differentiated resources. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            let resMgr = this.context.resourceManager;
            let overrideConfig = resMgr.getOverrideConfiguration();
            overrideConfig.colorMode = resourceManager.ColorMode.DARK;
            let overrideResMgr = resMgr.getOverrideResourceManager(overrideConfig);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getOverrideResourceManager failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getOverrideResourceManager

```TypeScript
getOverrideResourceManager(configuration?: Configuration): ResourceManager
```

Obtains a **ResourceManager** object for loading differentiated resources. This API returns the result synchronously.

The resource configuration (including the language, color mode, resolution, and orientation) obtained by a common **ResourceManager** object is determined by the system. With this API, an application can obtain resources of the specified configuration (that is, differentiated resources), for example, dark color resources in light color mode.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| configuration | [Configuration](arkts-localization-resourcemanager-configuration-c.md) | No | Resource configuration. <br>After obtaining the configuration of differentiated resources through [getOverrideConfiguration](#getoverrideconfiguration), modify the configuration items as required, and then pass these items as input parameters to the API. <br>If no configuration is specified, the current system configuration is used. |

**Return value:**

| Type | Description |
| --- | --- |
| [ResourceManager](arkts-localization-resourcemanager-resourcemanager-i.md) | **ResourceManager** object for loading differentiated resources. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            let resMgr = this.context.resourceManager;
            let overrideConfig = resMgr.getOverrideConfiguration();
            overrideConfig.colorMode = resourceManager.ColorMode.DARK;
            let overrideResMgr = resMgr.getOverrideResourceManager(overrideConfig);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getOverrideResourceManager failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getPluralString

```TypeScript
getPluralString(resId: number, num: number, callback: AsyncCallback<string>): void
```

Obtains the plural string based on the specified resource ID and the specified resource quantity. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Strings distinguish between singular and plural forms in all languages except Chinese. For details, see
> [Language Plural Rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [getPluralStringValue](#getpluralstringvalue-2)(resId: number, num: number, callback: _AsyncCallback&lt;string&gt;)

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| num | number | Yes | Quantity value, used to obtain the corresponding string representation based on the current language's [plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html). |
| callback | [AsyncCallback](arkts-localization-resourcemanager-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the obtained singular/plural string. |

**Examples**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.getPluralString($r("app.plural.test").id, 1, (error: Error, value: string) => {
        if (error != null) {
            console.error("error is " + error);
        } else {
            let str = value;
        }
    });
});
```

<a id="getpluralstring-1"></a>

## getPluralString

```TypeScript
getPluralString(resId: number, num: number): Promise<string>
```

Obtains the plural string based on the specified resource ID and the specified resource quantity. This API uses a promise to return the result.

> **NOTE:** 
> 
> Strings distinguish between singular and plural forms in all languages except Chinese. For details, see
> [Language Plural Rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [getPluralStringValue](#getpluralstringvalue-3)(resId: number, num: number)

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| num | number | Yes | Quantity value, used to obtain the corresponding string representation based on the current language's [plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the obtained singular/plural string. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.getPluralString($r("app.plural.test").id, 1).then((value: string) => {
        let str = value;
    }).catch((error: BusinessError) => {
        console.error("getPluralString promise error is " + error);
    });
});
```

## getPluralStringByName

```TypeScript
getPluralStringByName(resName: string, num: number, callback: _AsyncCallback<string>): void
```

Obtains the plural string based on the specified resource name and the specified resource quantity. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Strings distinguish between singular and plural forms in all languages except Chinese. For details, see
> [Language Plural Rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [getIntPluralStringByNameSync](#getintpluralstringbynamesync)(resName: string, num: number, ...args: Array&lt;string | number&gt;)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |
| num | number | Yes | Quantity value, used to obtain the corresponding string representation based on the current language's [plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html). |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;string&gt; | Yes | Callback used to return the obtained singular/plural string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "test",
      "value": [
        {
          "quantity": "one",
          "value": "%d apple"
        },
        {
          "quantity": "other",
          "value": "%d apples"
        }
      ]
    }
  ]
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// If num is 1, the single/plural type is one in the English environment.
// The quantity field in the resource file indicates the single/plural type. Therefore, the string whose quantity is one is obtained.
this.context.resourceManager.getPluralStringByName("test", 1, (error: BusinessError, value: string) => {
  if (error != null) {
    console.error(`callback getPluralStringByName failed, error code: ${error.code}, message: ${error.message}.`);
  } else {
    console.info(`getPluralStringByName, result: ${value}`);
    // Print the output result: getPluralStringByName, result: 1 apple
  }
});
```

<a id="getpluralstringbyname-1"></a>

## getPluralStringByName

```TypeScript
getPluralStringByName(resName: string, num: number): Promise<string>
```

Obtains the plural string based on the specified resource name and the specified resource quantity. This API uses a promise to return the result.

> **NOTE:** 
> 
> Strings distinguish between singular and plural forms in all languages except Chinese. For details, see
> [Language Plural Rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [getIntPluralStringByNameSync](#getintpluralstringbynamesync)(resName: string, num: number, ...args: Array&lt;string | number&gt;)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |
| num | number | Yes | Quantity value, used to obtain the corresponding string representation based on the current language's [plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the result, which is the singular/plural string corresponding to the specified resource name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "test",
      "value": [
        {
          "quantity": "one",
          "value": "%d apple"
        },
        {
          "quantity": "other",
          "value": "%d apples"
        }
      ]
    }
  ]
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// If num is 1, the single/plural type is one in the English environment.
// The quantity field in the resource file indicates the single/plural type. Therefore, the string whose quantity is one is obtained.
this.context.resourceManager.getPluralStringByName("test", 1)
  .then((value: string) => {
    console.info(`getPluralStringByName, result: ${value}`);
    // Print the output result: getPluralStringByName, result: 1 apple
  })
  .catch((error: BusinessError) => {
    console.error(`promise getPluralStringByName failed, error code: ${error.code}, message: ${error.message}.`);
  });
```

## getPluralStringByNameSync

```TypeScript
getPluralStringByNameSync(resName: string, num: number): string
```

Obtains singular/plural strings based on the specified quantity and resource name. This API returns the result synchronously.

> **NOTE:** 
> 
> Strings distinguish between singular and plural forms in all languages except Chinese. For details, see
> [Language Plural Rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).

**Since:** 10

**Deprecated since:** 18

**Substitutes:** [getIntPluralStringByNameSync](#getintpluralstringbynamesync)(resName: string, num: number, ...args: Array&lt;string | number&gt;)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |
| num | number | Yes | Quantity value, used to obtain the corresponding string representation based on the current language's [plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html). |

**Return value:**

| Type | Description |
| --- | --- |
| string | Singular/plural string corresponding to the specified quantity and resource name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "test",
      "value": [
        {
          "quantity": "one",
          "value": "%d apple"
        },
        {
          "quantity": "other",
          "value": "%d apples"
        }
      ]
    }
  ]
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // If num is 1, the single/plural type is one in the English environment.
  // The quantity field in the resource file indicates the single/plural type. Therefore, the string whose quantity is one is obtained.
  let pluralValue = this.context.resourceManager.getPluralStringByNameSync("test", 1);
  console.info(`getPluralStringByNameSync, result: ${pluralValue}`);
  // Print the output result: getPluralStringByNameSync, result: 1 apple
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getPluralStringByNameSync failed, error code: ${code}, message: ${message}.`);
}
```

## getPluralStringValue

```TypeScript
getPluralStringValue(resource: Resource, num: number, callback: _AsyncCallback<string>): void
```

Obtains the plural string based on the specified resource information and the specified resource quantity. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Strings distinguish between singular and plural forms in all languages except Chinese. For details, see
> [Language Plural Rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [getIntPluralStringValueSync](#getintpluralstringvaluesync)(resId: number, num: number,...args: Array&lt;string | number&gt;)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |
| num | number | Yes | Quantity value, used to obtain the corresponding string representation based on the current language's [plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html). |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;string&gt; | Yes | Callback used to return the obtained singular/plural string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "test",
      "value": [
        {
          "quantity": "one",
          "value": "%d apple"
        },
        {
          "quantity": "other",
          "value": "%d apples"
        }
      ]
    }
  ]
}
```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.plural.test').id
};
// If num is 1, the single/plural type is one in the English environment.
// The quantity field in the resource file indicates the single/plural type. Therefore, the string whose quantity is one is obtained.
this.context.resourceManager.getPluralStringValue(resource, 1,
  (error: BusinessError, value: string) => {
    if (error != null) {
      console.error(`callback getPluralStringValue failed, error code: ${error.code}, message: ${error.message}.`);
    } else {
      console.info(`getPluralStringValue, result: ${value}`);
      // Print the output result: getPluralStringValue, result: 1 apple
    }
  });
```

<a id="getpluralstringvalue-1"></a>

## getPluralStringValue

```TypeScript
getPluralStringValue(resource: Resource, num: number): Promise<string>
```

Obtains the plural string based on the specified resource information and the specified resource quantity. This API uses a promise to return the result.

> **NOTE:** 
> 
> Strings distinguish between singular and plural forms in all languages except Chinese. For details, see
> [Language Plural Rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [getIntPluralStringValueSync](#getintpluralstringvaluesync)(resId: number, num: number,...args: Array&lt;string | number&gt;)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |
| num | number | Yes | Quantity value, used to obtain the corresponding string representation based on the current language's [plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the obtained singular/plural string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "test",
      "value": [
        {
          "quantity": "one",
          "value": "%d apple"
        },
        {
          "quantity": "other",
          "value": "%d apples"
        }
      ]
    }
  ]
}
```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.plural.test').id
};
// If num is 1, the single/plural type is one in the English environment.
// The quantity field in the resource file indicates the single/plural type. Therefore, the string whose quantity is one is obtained.
this.context.resourceManager.getPluralStringValue(resource, 1)
  .then((value: string) => {
    console.info(`getPluralStringValue, result: ${value}`);
    // Print the output result: getPluralStringValue, result: 1 apple
  })
  .catch((error: BusinessError) => {
    console.error(`promise getPluralStringValue failed, error code: ${error.code}, message: ${error.message}.`);
  });
```

<a id="getpluralstringvalue-2"></a>

## getPluralStringValue

```TypeScript
getPluralStringValue(resId: number, num: number, callback: _AsyncCallback<string>): void
```

Obtains the plural string based on the specified resource ID and the specified resource quantity. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Strings distinguish between singular and plural forms in all languages except Chinese. For details, see
> [Language Plural Rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [getIntPluralStringValueSync](#getintpluralstringvaluesync)(resId: number, num: number,...args: Array&lt;string | number&gt;)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| num | number | Yes | Quantity value, used to obtain the corresponding string representation based on the current language's [plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html). |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;string&gt; | Yes | Callback used to return the obtained singular/plural string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "test",
      "value": [
        {
          "quantity": "one",
          "value": "%d apple"
        },
        {
          "quantity": "other",
          "value": "%d apples"
        }
      ]
    }
  ]
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// If num is 1, the single/plural type is one in the English environment.
// The quantity field in the resource file indicates the single/plural type. Therefore, the string whose quantity is one is obtained.
this.context.resourceManager.getPluralStringValue($r("app.plural.test").id, 1,
  (error: BusinessError, value: string) => {
    if (error != null) {
      console.error(`callback getPluralStringValue failed, error code: ${error.code}, message: ${error.message}.`);
    } else {
      console.info(`getPluralStringValue, result: ${value}`);
      // Print the output result: getPluralStringValue, result: 1 apple
    }
  });
```

<a id="getpluralstringvalue-3"></a>

## getPluralStringValue

```TypeScript
getPluralStringValue(resId: number, num: number): Promise<string>
```

Obtains the plural string based on the specified resource ID and the specified resource quantity. This API uses a promise to return the result.

> **NOTE:** 
> 
> Strings distinguish between singular and plural forms in all languages except Chinese. For details, see
> [Language Plural Rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [getIntPluralStringValueSync](#getintpluralstringvaluesync)(resId: number, num: number,...args: Array&lt;string | number&gt;)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| num | number | Yes | Quantity value, used to obtain the corresponding string representation based on the current language's [plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the obtained singular/plural string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "test",
      "value": [
        {
          "quantity": "one",
          "value": "%d apple"
        },
        {
          "quantity": "other",
          "value": "%d apples"
        }
      ]
    }
  ]
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// If num is 1, the single/plural type is one in the English environment.
// The quantity field in the resource file indicates the single/plural type. Therefore, the string whose quantity is one is obtained.
this.context.resourceManager.getPluralStringValue($r("app.plural.test").id, 1)
  .then((value: string) => {
    console.info(`getPluralStringValue, result: ${value}`);
    // Print the output result: getPluralStringValue, result: 1 apple
  })
  .catch((error: BusinessError) => {
    console.error(`promise getPluralStringValue failed, error code: ${error.code}, message: ${error.message}.`);
  });
```

## getPluralStringValueSync

```TypeScript
getPluralStringValueSync(resId: number, num: number): string
```

Obtains singular/plural strings based on the specified resource ID and quantity. This API returns the result synchronously.

> **NOTE:** 
> 
> Strings distinguish between singular and plural forms in all languages except Chinese. For details, see
> [Language Plural Rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).

**Since:** 10

**Deprecated since:** 18

**Substitutes:** [getIntPluralStringValueSync](#getintpluralstringvaluesync)(resId: number, num: number,...args: Array&lt;string | number&gt;)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| num | number | Yes | Quantity value, used to obtain the corresponding string representation based on the current language's [plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html). |

**Return value:**

| Type | Description |
| --- | --- |
| string | Singular/plural string corresponding to the specified quantity and resource ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "test",
      "value": [
        {
          "quantity": "one",
          "value": "%d apple"
        },
        {
          "quantity": "other",
          "value": "%d apples"
        }
      ]
    }
  ]
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // If num is 1, the single/plural type is one in the English environment.
  // The quantity field in the resource file indicates the single/plural type. Therefore, the string whose quantity is one is obtained.
  let pluralValue = this.context.resourceManager.getPluralStringValueSync($r('app.plural.test').id, 1);
  console.info(`getPluralStringValueSync, result: ${pluralValue}`);
  // Print the output result: getPluralStringValueSync, result: 1 apple
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getPluralStringValueSync failed, error code: ${code}, message: ${message}.`);
}
```

<a id="getpluralstringvaluesync-1"></a>

## getPluralStringValueSync

```TypeScript
getPluralStringValueSync(resource: Resource, num: number): string
```

Obtains singular/plural strings based on the specified quantity and resource object. This API returns the result synchronously.

> **NOTE:** 
> 
> Strings distinguish between singular and plural forms in all languages except Chinese. For details, see
> [Language Plural Rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html).

**Since:** 10

**Deprecated since:** 18

**Substitutes:** [getIntPluralStringValueSync](#getintpluralstringvaluesync)(resId: number, num: number,...args: Array&lt;string | number&gt;)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |
| num | number | Yes | Quantity value, used to obtain the corresponding string representation based on the current language's [plural rules](https://www.unicode.org/cldr/charts/45/supplemental/language_plural_rules.html). |

**Return value:**

| Type | Description |
| --- | --- |
| string | Singular/plural string corresponding to the specified quantity and resource object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/plural.json
{
  "plural": [
    {
      "name": "test",
      "value": [
        {
          "quantity": "one",
          "value": "%d apple"
        },
        {
          "quantity": "other",
          "value": "%d apples"
        }
      ]
    }
  ]
}
```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.plural.test').id
};
try {
  // If num is 1, the single/plural type is one in the English environment.
  // The quantity field in the resource file indicates the single/plural type. Therefore, the string whose quantity is one is obtained.
  let pluralValue = this.context.resourceManager.getPluralStringValueSync(resource, 1);
  console.info(`getPluralStringValueSync, result: ${pluralValue}`);
  // Print the output result: getPluralStringValueSync, result: 1 apple
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getPluralStringValueSync failed, error code: ${code}, message: ${message}.`);
}
```

## getRawFd

```TypeScript
getRawFd(path: string, callback: _AsyncCallback<RawFileDescriptor>): void
```

Obtains the file descriptor (fd) of the HAP where a specific rawfile in the **resources/rawfile** directory is located. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> To prevent resource leakage, call [closeRawFdSync](#closerawfdsync) or
> [closeRawFd](#closerawfd)
> to close the fd after use.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | rawfile path relative to the **resources/rawfile** directory, such as **test.txt** or **subdir/test.txt**. The path must not start with a slash (/). |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;[RawFileDescriptor](arkts-localization-resourcemanager-rawfiledescriptor-t.md)&gt; | Yes | Callback used to return the fd of the HAP. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-invalid-relative-path) | Invalid relative path. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "test.txt" with the actual resource.
            this.context.resourceManager.getRawFd("test.txt", (error: BusinessError, value: resourceManager.RawFileDescriptor) => {
                if (error != null) {
                    console.error(`callback getRawFd failed error code: ${error.code}, message: ${error.message}.`);
                } else {
                    let fd = value.fd;
                    let offset = value.offset;
                    let length = value.length;
                }
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`callback getRawFd failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getrawfd-1"></a>

## getRawFd

```TypeScript
getRawFd(path: string): Promise<RawFileDescriptor>
```

Obtains the file descriptor (fd) of the HAP where a specific rawfile in the **resources/rawfile** directory is located. This API uses a promise to return the result.

> **NOTE:** 
> 
> To prevent resource leakage, call [closeRawFdSync](#closerawfdsync) or
> [closeRawFd](#closerawfd)
> to close the fd after use.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | rawfile path relative to the **resources/rawfile** directory, such as **test.txt** or **subdir/test.txt**. The path must not start with a slash (/). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RawFileDescriptor](arkts-localization-resourcemanager-rawfiledescriptor-t.md)&gt; | Promise used to return the fd of the HAP. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-invalid-relative-path) | Invalid relative path. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "test.txt" with the actual resource.
            this.context.resourceManager.getRawFd("test.txt").then((value: resourceManager.RawFileDescriptor) => {
                let fd = value.fd;
                let offset = value.offset;
                let length = value.length;
            }).catch((error: BusinessError) => {
                console.error(`promise getRawFd error error code: ${error.code}, message: ${error.message}.`);
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`promise getRawFd failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getRawFdSync

```TypeScript
getRawFdSync(path: string): RawFileDescriptor
```

Obtains the file descriptor (fd) of the HAP where the rawfile file in the resources/rawfile directory is located. This API is called in synchronous mode.

> **NOTE:** 
> 
> To prevent resource leakage, call [closeRawFdSync](#closerawfdsync) or
> [closeRawFd](#closerawfd)
> to close the fd after use.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | rawfile path relative to the **resources/rawfile** directory, such as **test.txt** or **subdir/test.txt**. The path must not start with a slash (/). |

**Return value:**

| Type | Description |
| --- | --- |
| [RawFileDescriptor](arkts-localization-resourcemanager-rawfiledescriptor-t.md) | fd of the HAP where the rawfile is located. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-invalid-relative-path) | Invalid relative path. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "test.txt" with the actual resource.
            this.context.resourceManager.getRawFdSync("test.txt");
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getRawFdSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getRawFile

```TypeScript
getRawFile(path: string, callback: AsyncCallback<Uint8Array>): void
```

Obtain the content of a rawfile in the **resources/rawfile** directory. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getRawFileContent](#getrawfilecontent)(path: string, callback: _AsyncCallback&lt;Uint8Array&gt;)

**System capability:** SystemCapability.Global.ResourceManager

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | rawfile path relative to the **resources/rawfile** directory, such as **test.txt** or **subdir/test.txt**. The path must not start with a slash (/). |
| callback | [AsyncCallback](arkts-localization-resourcemanager-asynccallback-i.md)&lt;Uint8Array&gt; | Yes | Callback used to return the rawfile content. |

**Examples**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.getRawFile("test.txt", (error: Error, value: Uint8Array) => {
        if (error != null) {
            console.error("error is " + error);
        } else {
            let rawFile = value;
        }
    });
});
```

<a id="getrawfile-1"></a>

## getRawFile

```TypeScript
getRawFile(path: string): Promise<Uint8Array>
```

Obtain the content of a rawfile in the **resources/rawfile** directory. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getRawFileContent](#getrawfilecontent-1)(path: string)

**System capability:** SystemCapability.Global.ResourceManager

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | rawfile path relative to the **resources/rawfile** directory, such as **test.txt** or **subdir/test.txt**. The path must not start with a slash (/). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise used to return the rawfile content. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.getRawFile("test.txt").then((value: Uint8Array) => {
        let rawFile = value;
    }).catch((error: BusinessError) => {
        console.error("getRawFile promise error is " + error);
    });
});
```

## getRawFileContent

```TypeScript
getRawFileContent(path: string, callback: _AsyncCallback<Uint8Array>): void
```

Obtain the content of a rawfile in the **resources/rawfile** directory. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | rawfile path relative to the **resources/rawfile** directory, such as **test.txt** or **subdir/test.txt**. The path must not start with a slash (/). |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;Uint8Array&gt; | Yes | Callback used to return the content of the rawfile. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-invalid-relative-path) | Invalid relative path. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "test.txt" with the actual resource.
            this.context.resourceManager.getRawFileContent("test.txt", (error: BusinessError, value: Uint8Array) => {
                if (error != null) {
                    console.error("error is " + error);
                } else {
                    let rawFile = value;
                }
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`callback getRawFileContent failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getrawfilecontent-1"></a>

## getRawFileContent

```TypeScript
getRawFileContent(path: string): Promise<Uint8Array>
```

Obtain the content of a rawfile in the **resources/rawfile** directory. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | rawfile path relative to the **resources/rawfile** directory, such as **test.txt** or **subdir/test.txt**. The path must not start with a slash (/). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Uint8Array&gt; | Promise used to return the content of the rawfile. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-invalid-relative-path) | Invalid relative path. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "test.txt" with the actual resource.
            this.context.resourceManager.getRawFileContent("test.txt").then((value: Uint8Array) => {
                let rawFile = value;
            }).catch((error: BusinessError) => {
                console.error("getRawFileContent promise error is " + error);
            });
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`promise getRawFileContent failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getRawFileContentSync

```TypeScript
getRawFileContentSync(path: string): Uint8Array
```

Obtains the content of a rawfile in the **resources/rawfile** directory. This API returns the result synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | rawfile path relative to the **resources/rawfile** directory, such as **test.txt** or **subdir/test.txt**. The path must not start with a slash (/). |

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | Content of the rawfile. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-invalid-relative-path) | Invalid relative path. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "test.txt" with the actual resource.
            this.context.resourceManager.getRawFileContentSync("test.txt");
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getRawFileContentSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getRawFileDescriptor

```TypeScript
getRawFileDescriptor(path: string, callback: AsyncCallback<RawFileDescriptor>): void
```

Obtains the file descriptor (fd) of a specific rawfile in the **resources/rawfile** directory. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getRawFd](#getrawfd)(path: string, callback: _AsyncCallback&lt;RawFileDescriptor&gt;)

**System capability:** SystemCapability.Global.ResourceManager

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | rawfile path relative to the **resources/rawfile** directory, such as **test.txt** or **subdir/test.txt**. The path must not start with a slash (/). |
| callback | [AsyncCallback](arkts-localization-resourcemanager-asynccallback-i.md)&lt;[RawFileDescriptor](arkts-localization-resourcemanager-rawfiledescriptor-t.md)&gt; | Yes | Callback used to return the obtained fd. |

**Examples**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.getRawFileDescriptor("test.txt", (error: Error, value: resourceManager.RawFileDescriptor) => {
        if (error != null) {
            console.error("error is " + error);
        } else {
            let fd = value.fd;
            let offset = value.offset;
            let length = value.length;
        }
    });
});
```

<a id="getrawfiledescriptor-1"></a>

## getRawFileDescriptor

```TypeScript
getRawFileDescriptor(path: string): Promise<RawFileDescriptor>
```

Obtains the file descriptor (fd) of a specific rawfile in the **resources/rawfile** directory. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getRawFd](#getrawfd-1)(path: string)

**System capability:** SystemCapability.Global.ResourceManager

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | rawfile path relative to the **resources/rawfile** directory, such as **test.txt** or **subdir/test.txt**. The path must not start with a slash (/). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RawFileDescriptor](arkts-localization-resourcemanager-rawfiledescriptor-t.md)&gt; | Promise used to return the obtained fd. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.getRawFileDescriptor("test.txt").then((value: resourceManager.RawFileDescriptor) => {
        let fd = value.fd;
        let offset = value.offset;
        let length = value.length;
    }).catch((error: BusinessError) => {
        console.error("getRawFileDescriptor promise error is " + error);
    });
});
```

## getRawFileList

```TypeScript
getRawFileList(path: string, callback: _AsyncCallback<Array<string>>): void
```

Obtains the list of directories and files in the specified subdirectory under **resources/rawfile**. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> If there is no folder or file in the directory, an exception is thrown. If there are folders and files in the
> directory, the list of the folders and files is returned.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | rawfile subdirectory path relative to the **resources/rawfile** directory, such as **subdir**. The path must not start with a slash (/).<br>An empty string **""** indicates that the list of directories and files in the **rawfile** root directory is obtained. |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback used to return the list of directories and files in a rawfile subdirectory. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-invalid-relative-path) | Invalid relative path. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // Passing "" means to obtain the list of files in the root directory (that is, /rawfile). Assume that the test.txt file exists in the root directory.
        // Replace "" with the actual file path in the rawfile directory.
        this.context.resourceManager.getRawFileList("", (error: BusinessError, value: Array<string>) => {
            if (error != null) {
                console.error(`callback getRawFileList failed, error code: ${error.code}, message: ${error.message}.`);
            } else {
                console.info(`getRawFileList, result: ${JSON.stringify(value)}`);
                // Print the output result: getRawFileList, result: ["test.txt"].
            }
        });
    }
}
```

<a id="getrawfilelist-1"></a>

## getRawFileList

```TypeScript
getRawFileList(path: string): Promise<Array<string>>
```

Obtains the list of directories and files in the specified subdirectory under **resources/rawfile**. This API uses a promise to return the result.

> **NOTE:** 
> 
> If there is no folder or file in the directory, an exception is thrown. If there are folders and files in the
> directory, the list of the folders and files is returned.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | rawfile subdirectory path relative to the **resources/rawfile** directory, such as **subdir**. The path must not start with a slash (/).<br>An empty string **""** indicates that the list of directories and files in the **rawfile** root directory is obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the list of directories and files in a rawfile subdirectory. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-invalid-relative-path) | Invalid relative path. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // Passing "" means to obtain the list of files in the root directory (that is, /rawfile). Assume that the test.txt file exists in the root directory.
        // Replace "" with the actual file path in the rawfile directory.
        this.context.resourceManager.getRawFileList("")
            .then((value: Array<string>) => {
                console.info(`getRawFileList, result: ${JSON.stringify(value)}`);
                // Print the output result: getRawFileList, result: ["test.txt"].
            })
            .catch((error: BusinessError) => {
                console.error(`promise getRawFileList failed, error code: ${error.code}, message: ${error.message}.`);
            });
    }
}
```

## getRawFileListSync

```TypeScript
getRawFileListSync(path: string): Array<string>
```

Obtains the list of directories and files in the specified subdirectory under **resources/rawfile**. This API returns the result synchronously.

> **NOTE:** 
> 
> If there is no folder or file in the directory, an exception is thrown. If there are folders and files in the
> directory, the list of the folders and files is returned.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | rawfile subdirectory path relative to the **resources/rawfile** directory, such as **subdir**. The path must not start with a slash (/).<br>An empty string **""** indicates that the list of directories and files in the **rawfile** root directory is obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | List of folders and files in the **rawfile** directory. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-invalid-relative-path) | Invalid relative path. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Passing "" means to obtain the list of files in the root directory (that is, /rawfile). Assume that the test.txt file exists in the root directory.
            // Replace "" with the actual file path in the rawfile directory.
            let fileList: Array<string> = this.context.resourceManager.getRawFileListSync("");
            console.info(`getRawFileListSync, result: ${JSON.stringify(fileList)}`);
            // Print the output result: getRawFileListSync, result: ["test.txt"]
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getRawFileListSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getResourceName

```TypeScript
getResourceName(resId: number): string
```

Obtains the resource name corresponding to the specified resource ID.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Resource name corresponding to the resource ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a test string resource."
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace 'app.string.test' with the actual resource.
            let resName: string = this.context.resourceManager.getResourceName($r('app.string.test').id);
            console.info(`getResourceName, result: ${resName}`);
            // Print the output result: getResourceName, result: test
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getResourceName failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getString

```TypeScript
getString(resId: number, callback: AsyncCallback<string>): void
```

Obtains the string corresponding to the specified resource ID. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [getStringValue](#getstringvalue)(resId: number, callback: _AsyncCallback&lt;string&gt;)

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| callback | [AsyncCallback](arkts-localization-resourcemanager-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the obtained string. |

**Examples**

```TypeScript
resourceManager.getResourceManager((error, mgr) => {
    mgr.getString($r('app.string.test').id, (error: Error, value: string) => {
        if (error != null) {
            console.error("error is " + error);
        } else {
            let str = value;
        }
    });
});
```

<a id="getstring-1"></a>

## getString

```TypeScript
getString(resId: number): Promise<string>
```

Obtains the string corresponding to the specified resource ID. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [getStringValue](#getstringvalue)(resId: number)

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the obtained string. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

resourceManager.getResourceManager((error, mgr) => {
    mgr.getString($r('app.string.test').id).then((value: string) => {
        let str = value;
    }).catch((error: BusinessError) => {
        console.error("getstring promise error is " + error);
    });
});
```

## getStringArray

```TypeScript
getStringArray(resId: number, callback: AsyncCallback<Array<string>>): void
```

Obtains the string array corresponding to the specified resource ID. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [getStringArrayValue](#getstringarrayvalue)(resId: number, callback: _AsyncCallback&lt;Array&lt;string&gt;&gt;)

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| callback | [AsyncCallback](arkts-localization-resourcemanager-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback used to return the obtained string array. |

**Examples**

```TypeScript
resourceManager.getResourceManager((error, mgr) => {
    mgr.getStringArray($r('app.strarray.test').id, (error: Error, value: Array<string>) => {
        if (error != null) {
            console.error("error is " + error);
        } else {
            let strArray = value;
        }
    });
});
```

<a id="getstringarray-1"></a>

## getStringArray

```TypeScript
getStringArray(resId: number): Promise<Array<string>>
```

Obtains the string array corresponding to the specified resource ID. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [getStringArrayValue](#getstringarrayvalue)(resId: number)

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the obtained string array. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

resourceManager.getResourceManager((error, mgr) => {
      mgr.getStringArray($r('app.strarray.test').id).then((value: Array<string>) => {
        let strArray = value;
    }).catch((error: BusinessError) => {
        console.error("getStringArray promise error is " + error);
    });
});
```

## getStringArrayByName

```TypeScript
getStringArrayByName(resName: string, callback: _AsyncCallback<Array<string>>): void
```

Obtains the string array corresponding to the specified resource name. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback used to return the obtained string array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/strarray.json
{
  "strarray": [
    {
      "name": "test",
      "value": [
        {
          "value": "I'm one of the array's values."
        }
      ]
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // Replace "test" with the actual resource.
        this.context.resourceManager.getStringArrayByName("test", (error: BusinessError, value: Array<string>) => {
            if (error != null) {
                console.error(`callback getStringArrayByName failed, error code: ${error.code}, message: ${error.message}.`);
            } else {
                let strArray = value;
                console.info(`getStringArrayByName, result: ${value[0]}`);
                // Print the output result: getStringArrayByName, result: I'm one of the array's values.
            }
        });
    }
}
```

<a id="getstringarraybyname-1"></a>

## getStringArrayByName

```TypeScript
getStringArrayByName(resName: string): Promise<Array<string>>
```

Obtains the string array corresponding to the specified resource name. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the obtained string array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/strarray.json
{
  "strarray": [
    {
      "name": "test",
      "value": [
        {
          "value": "I'm one of the array's values."
        }
      ]
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // Replace "test" with the actual resource.
        this.context.resourceManager.getStringArrayByName("test")
            .then((value: Array<string>) => {
                console.info(`getStringArrayByName, result: ${value[0]}`);
                // Print the output result: getStringArrayByName, result: I'm one of the array's values.
            })
            .catch((error: BusinessError) => {
                console.error(`promise getStringArrayByName failed, error code: ${error.code}, message: ${error.message}.`);
            });
    }
}
```

## getStringArrayByNameSync

```TypeScript
getStringArrayByNameSync(resName: string): Array<string>
```

Obtains the string array corresponding to the specified resource name. This API returns the result synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | String array corresponding to the specified resource name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/strarray.json
{
  "strarray": [
    {
      "name": "test",
      "value": [
        {
          "value": "I'm one of the array's values."
        }
      ]
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "test" with the actual resource.
            let strArray: Array<string> = this.context.resourceManager.getStringArrayByNameSync("test");
            console.info(`getStringArrayByNameSync, result: ${strArray[0]}`);
            // Print the output result: getStringArrayByNameSync, result: I'm one of the array's values.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getStringArrayByNameSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getStringArrayValue

```TypeScript
getStringArrayValue(resource: Resource, callback: _AsyncCallback<Array<string>>): void
```

Obtains the string array corresponding to the specified resource object. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** [getStringArrayValue](#getstringarrayvalue)(resId: number, callback: _AsyncCallback&lt;Array&lt;string&gt;&gt;)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback used to return the obtained string array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/strarray.json
{
  "strarray": [
    {
      "name": "test",
      "value": [
        {
          "value": "I'm one of the array's values."
        }
      ]
    }
  ]
}
```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.strarray.test').id
};
this.context.resourceManager.getStringArrayValue(resource, (error: BusinessError, value: Array<string>) => {
  if (error != null) {
    console.error(`callback getStringArrayValue failed, error code: ${error.code}, message: ${error.message}.`);
  } else {
    console.info(`getStringArrayValue, result: ${value[0]}`);
    // Print the output result: getStringArrayValue, result: I'm one of the array's values.
  }
});
```

<a id="getstringarrayvalue-1"></a>

## getStringArrayValue

```TypeScript
getStringArrayValue(resource: Resource): Promise<Array<string>>
```

Obtains the string array corresponding to the specified resource object. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** [getStringArrayValue](#getstringarrayvalue)(resId: number)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the obtained string array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/strarray.json
{
  "strarray": [
    {
      "name": "test",
      "value": [
        {
          "value": "I'm one of the array's values."
        }
      ]
    }
  ]
}
```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.strarray.test').id
};
this.context.resourceManager.getStringArrayValue(resource)
  .then((value: Array<string>) => {
    console.info(`getStringArrayValue, result: ${value[0]}`);
    // Print the output result: getStringArrayValue, result: I'm one of the array's values.
  })
  .catch((error: BusinessError) => {
    console.error(`promise getStringArrayValue failed, error code: ${error.code}, message: ${error.message}.`);
  });
```

<a id="getstringarrayvalue-2"></a>

## getStringArrayValue

```TypeScript
getStringArrayValue(resId: number, callback: _AsyncCallback<Array<string>>): void
```

Obtains the string array corresponding to the specified resource ID. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback used to return the obtained string array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/strarray.json
{
  "strarray": [
    {
      "name": "test",
      "value": [
        {
          "value": "I'm one of the array's values."
        }
      ]
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // Replace 'app.strarray.test' with the actual resource.
        this.context.resourceManager.getStringArrayValue($r('app.strarray.test').id,
            (error: BusinessError, value: Array<string>) => {
                if (error != null) {
                    console.error(`callback getStringArrayValue failed, error code: ${error.code}, message: ${error.message}.`);
                } else {
                    console.info(`getStringArrayValue, result: ${value[0]}`);
                    // Print the output result: getStringArrayValue, result: I'm one of the array's values.
                }
            });
    }
}
```

<a id="getstringarrayvalue-3"></a>

## getStringArrayValue

```TypeScript
getStringArrayValue(resId: number): Promise<Array<string>>
```

Obtains the string array corresponding to the specified resource ID. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the obtained string array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/strarray.json
{
  "strarray": [
    {
      "name": "test",
      "value": [
        {
          "value": "I'm one of the array's values."
        }
      ]
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // Replace 'app.strarray.test' with the actual resource.
        this.context.resourceManager.getStringArrayValue($r('app.strarray.test').id)
            .then((value: Array<string>) => {
                console.info(`getStringArrayValue, result: ${value[0]}`);
                // Print the output result: getStringArrayValue, result: I'm one of the array's values.
            })
            .catch((error: BusinessError) => {
                console.error(`promise getStringArrayValue failed, error code: ${error.code}, message: ${error.message}.`);
            });
    }
}
```

## getStringArrayValueSync

```TypeScript
getStringArrayValueSync(resId: number): Array<string>
```

Obtains the string array corresponding to the specified resource ID. This API returns the result synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | String array corresponding to the specified resource ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/strarray.json
{
  "strarray": [
    {
      "name": "test",
      "value": [
        {
          "value": "I'm one of the array's values."
        }
      ]
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace 'app.strarray.test' with the actual resource.
            let strArray: Array<string> = this.context.resourceManager.getStringArrayValueSync($r('app.strarray.test').id);
            console.info(`getStringArrayValueSync, result: ${strArray[0]}`);
            // Print the output result: getStringArrayValueSync, result: I'm one of the array's values.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getStringArrayValueSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getstringarrayvaluesync-1"></a>

## getStringArrayValueSync

```TypeScript
getStringArrayValueSync(resource: Resource): Array<string>
```

Obtains a string array based on the specified resource object. This API returns the result synchronously.

**Since:** 10

**Deprecated since:** 20

**Substitutes:** [getStringArrayValueSync](#getstringarrayvaluesync)(resId: number)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | String array corresponding to the specified resource object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/strarray.json
{
  "strarray": [
    {
      "name": "test",
      "value": [
        {
          "value": "I'm one of the array's values."
        }
      ]
    }
  ]
}
```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.strarray.test').id
};
try {
  let strArray: Array<string> = this.context.resourceManager.getStringArrayValueSync(resource);
  console.info(`getStringArrayValueSync, result: ${strArray[0]}`);
  // Print the output result: getStringArrayValueSync, result: I'm one of the array's values.
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getStringArrayValueSync failed, error code: ${code}, message: ${message}.`);
}
```

## getStringByName

```TypeScript
getStringByName(resName: string, callback: _AsyncCallback<string>): void
```

Obtains the string corresponding to the specified resource name. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;string&gt; | Yes | Callback used to return the obtained string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a test string resource."
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // Replace "test" with the actual resource.
        this.context.resourceManager.getStringByName("test", (error: BusinessError, value: string) => {
            if (error != null) {
                console.error(`callback getStringByName failed, error code: ${error.code}, message: ${error.message}.`);
            } else {
                console.info(`getStringByName, result: ${value}`);
                // Print the output result: getStringByName, result: I'm a test string resource.
            }
        });
    }
}
```

<a id="getstringbyname-1"></a>

## getStringByName

```TypeScript
getStringByName(resName: string): Promise<string>
```

Obtains the string corresponding to the specified resource name. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the obtained string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a test string resource."
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // Replace "test" with the actual resource.
        this.context.resourceManager.getStringByName("test").then((value: string) => {
            console.info(`getStringByName, result: ${value}`);
            // Print the output result: getStringByName, result: I'm a test string resource.
        }).catch((error: BusinessError) => {
            console.error(`promise getStringByName failed, error code: ${error.code}, message: ${error.message}.`);
        });
    }
}
```

## getStringByNameSync

```TypeScript
getStringByNameSync(resName: string): string
```

Obtains the string corresponding to the specified resource name. This API returns the result synchronously.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |

**Return value:**

| Type | Description |
| --- | --- |
| string | String corresponding to the specified resource name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a test string resource."
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "test" with the actual resource.
            let testStr = this.context.resourceManager.getStringByNameSync("test");
            console.info(`getStringByNameSync, result: ${testStr}`);
            // Print the output result: getStringByNameSync, result: I'm a test string resource.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getStringByNameSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getstringbynamesync-1"></a>

## getStringByNameSync

```TypeScript
getStringByNameSync(resName: string, ...args: Array<string | number>): string
```

Obtains the string corresponding to the specified resource name, and replaces the format placeholders in the string in sequence using the **args** parameter. This API returns the result synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |
| args | Array&lt;string &#124; number&gt; | Yes | Parameters for the formatted string resource. Supported parameter types include `%d`, `%f`, `%s`, `%%`, `%number$d`, `%number$f`, and `%number$s`. <br>**NOTE:** <br>- `%%` is escaped as `%`. For example, `%%d` is formatted as `%d`. <br>- In `%number$d`, `number` indicates the parameter index, starting from `1`. For example, `%1$d` uses `args[0]` for formatting, `%2$d` uses `args[1]`, and so on. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Formatted string corresponding to the specified resource name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |
| [9001008](../errorcode-resource-manager.md#9001008-failed-to-format-the-resource-obtained-based-on-resname) | Failed to format the resource obtained based on the resource name. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a %1$s, format int: %2$d, format float: %3$f."
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "test" with the actual resource.
            let testStr = this.context.resourceManager.getStringByNameSync("test", "format string", 10, 98.78);
            console.info(`getStringByNameSync, result: ${testStr}`);
            // Print the output result: getStringByNameSync, result: I'm a format string, format int: 10, format float: 98.78.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getStringByNameSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## getStringSync

```TypeScript
getStringSync(resId: number): string
```

Obtains the string corresponding to the specified resource ID. This API returns the result synchronously.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |

**Return value:**

| Type | Description |
| --- | --- |
| string | String corresponding to the specified resource ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a test string resource."
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace 'app.string.test' with the actual resource.
            let testStr = this.context.resourceManager.getStringSync($r('app.string.test').id);
            console.info(`getStringSync, result: ${testStr}`);
            // Print the output result: getStringSync, result: I'm a test string resource.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getStringSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getstringsync-1"></a>

## getStringSync

```TypeScript
getStringSync(resId: number, ...args: Array<string | number>): string
```

Obtains the string corresponding to the specified resource ID, and replaces the format placeholders in the string in sequence using the **args** parameter. This API returns the result synchronously.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| args | Array&lt;string &#124; number&gt; | Yes | Parameters for the formatted string resource. Supported parameter types include `%d`, `%f`, `%s`, `%%`, `%number$d`, `%number$f`, and `%number$s`. <br>**NOTE:** <br>- `%%` is escaped as `%`. For example, `%%d` is formatted as `%d`. <br>- In `%number$d`, `number` indicates the parameter index, starting from `1`. For example, `%1$d` uses `args[0]` for formatting, `%2$d` uses `args[1]`, and so on. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Formatted string corresponding to the specified resource ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |
| [9001007](../errorcode-resource-manager.md#9001007-failed-to-format-the-resource-obtained-based-on-the-current-id) | Failed to format the resource obtained based on the resource ID. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a %1$s, format int: %2$d, format float: %3$f."
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace 'app.string.test' with the actual resource.
            let testStr = this.context.resourceManager.getStringSync($r('app.string.test').id, "format string", 10, 98.78);
            console.info(`getStringSync, result: ${testStr}`);
            // Print the output result: getStringSync, result: I'm a format string, format int: 10, format float: 98.78.
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getStringSync failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getstringsync-3"></a>

## getStringSync

```TypeScript
getStringSync(resource: Resource): string
```

Obtains a string based on the specified resource object. This API returns the result synchronously.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** [getStringSync](#getstringsync)(resId: number)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |

**Return value:**

| Type | Description |
| --- | --- |
| string | String corresponding to the specified resource object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a test string resource."
    }
  ]
}
```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.string.test').id
};
try {
  let testStr = this.context.resourceManager.getStringSync(resource);
  console.info(`getStringSync, result: ${testStr}`);
  // Print the output result: getStringSync, result: I'm a test string resource.
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getStringSync failed, error code: ${code}, message: ${message}.`);
}
```

<a id="getstringsync-4"></a>

## getStringSync

```TypeScript
getStringSync(resource: Resource, ...args: Array<string | number>): string
```

Obtains the string corresponding to the specified resource object, and replaces the format placeholders in the string in sequence using the **args** parameter. This API returns the result synchronously.

**Since:** 10

**Deprecated since:** 20

**Substitutes:** [getStringSync](#getstringsync-1)(resId: number, ...args: Array&lt;string | number&gt;)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |
| args | Array&lt;string &#124; number&gt; | Yes | Parameters for the formatted string resource. Supported parameter types include `%d`, `%f`, `%s`, `%%`, `%number$d`, `%number$f`, and `%number$s`. <br>**NOTE:** <br>- `%%` is escaped as `%`. For example, `%%d` is formatted as `%d`. <br>- In `%number$d`, `number` indicates the parameter index, starting from `1`. For example, `%1$d` uses `args[0]` for formatting, `%2$d` uses `args[1]`, and so on. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Formatted string corresponding to the specified resource object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |
| [9001007](../errorcode-resource-manager.md#9001007-failed-to-format-the-resource-obtained-based-on-the-current-id) | Failed to format the resource obtained based on the resource ID. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a %1$s, format int: %2$d, format float: %3$f."
    }
  ]
}
```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.string.test').id
};
try {
  let testStr = this.context.resourceManager.getStringSync(resource, "format string", 10, 98.78);
  console.info(`getStringSync, result: ${testStr}`);
  // Print the output result: getStringSync, result: I'm a format string, format int: 10, format float: 98.78.
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getStringSync failed, error code: ${code}, message: ${message}.`);
}
```

## getStringValue

```TypeScript
getStringValue(resource: Resource, callback: _AsyncCallback<string>): void
```

Obtains the string corresponding to the specified resource object. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** [getStringValue](#getstringvalue)(resId: number, callback: _AsyncCallback&lt;string&gt;)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;string&gt; | Yes | Callback used to return the obtained string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a test string resource."
    }
  ]
}
```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.string.test').id
};
this.context.resourceManager.getStringValue(resource, (error: BusinessError, value: string) => {
  if (error != null) {
    console.error(`callback getStringValue failed, error code: ${error.code}, message: ${error.message}.`);
  } else {
    console.info(`getStringValue, result: ${value}`);
    // Print the output result: getStringValue, result: I'm a test string resource.
  }
});
```

<a id="getstringvalue-1"></a>

## getStringValue

```TypeScript
getStringValue(resource: Resource): Promise<string>
```

Obtains the string corresponding to the specified resource object. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 20

**Substitutes:** [getStringValue](#getstringvalue)(resId: number)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the obtained string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.string.test').id
};
this.context.resourceManager.getStringValue(resource, (error: BusinessError, value: string) => {
  if (error != null) {
    console.error(`callback getStringValue failed, error code: ${error.code}, message: ${error.message}.`);
  } else {
    console.info(`getStringValue, result: ${value}`);
    // Print the output result: getStringValue, result: I'm a test string resource.
  }
});
```

<a id="getstringvalue-2"></a>

## getStringValue

```TypeScript
getStringValue(resId: number, callback: _AsyncCallback<string>): void
```

Obtains the string corresponding to the specified resource ID. This API uses an asynchronous callback to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |
| callback | [_AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basic-services-base.md)&lt;string&gt; | Yes | Callback used to return the obtained string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a test string resource."
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // Replace 'app.string.test' with the actual resource.
        this.context.resourceManager.getStringValue($r('app.string.test').id).then((value: string) => {
            console.info(`getStringValue, result: ${value}`);
            // Print the output result: getStringValue, result: I'm a test string resource.
        }).catch((error: BusinessError) => {
            console.error(`promise getStringValue failed, error code: ${error.code}, message: ${error.message}.`);
        });
    }
}
```

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('app.string.test').id
};
this.context.resourceManager.getStringValue(resource, (error: BusinessError, value: string) => {
  if (error != null) {
    console.error(`callback getStringValue failed, error code: ${error.code}, message: ${error.message}.`);
  } else {
    console.info(`getStringValue, result: ${value}`);
    // Print the output result: getStringValue, result: I'm a test string resource.
  }
});
```

<a id="getstringvalue-3"></a>

## getStringValue

```TypeScript
getStringValue(resId: number): Promise<string>
```

Obtains the string corresponding to the specified resource ID. This API uses a promise to return the result.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the obtained string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
// Resource file path: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a test string resource."
    }
  ]
}
```

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // Replace 'app.string.test' with the actual resource.
        this.context.resourceManager.getStringValue($r('app.string.test').id).then((value: string) => {
            console.info(`getStringValue, result: ${value}`);
            // Print the output result: getStringValue, result: I'm a test string resource.
        }).catch((error: BusinessError) => {
            console.error(`promise getStringValue failed, error code: ${error.code}, message: ${error.message}.`);
        });
    }
}
```

## getSymbol

```TypeScript
getSymbol(resId: number) : number
```

Obtains the Unicode of a [symbol](https://developer.huawei.com/consumer/en/design/harmonyos-symbol) based on the specified resource ID. This API returns the result synchronously.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resId | number | Yes | Resource ID. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Unicode code (decimal) of the symbol. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace 'sys.symbol.message' with the actual resource.
            let symbolValue = this.context.resourceManager.getSymbol($r('sys.symbol.message').id);
            console.info(`getSymbol, result: ${symbolValue}`);
            // Print the output result: getSymbol, result: 983183
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getSymbol failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

<a id="getsymbol-1"></a>

## getSymbol

```TypeScript
getSymbol(resource: Resource) : number
```

Obtains the Unicode of a [symbol](https://developer.huawei.com/consumer/en/design/harmonyos-symbol) based on the specified resource object. This API returns the result synchronously.

**Since:** 11

**Deprecated since:** 20

**Substitutes:** [getSymbol](#getsymbol)(resId: number)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resource | [Resource](arkts-localization-resourcemanager-resource-t.md) | Yes | Resource object. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Unicode code (decimal) of the symbol. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001001](../errorcode-resource-manager.md#9001001-invalid-resource-id) | Invalid resource ID. |
| [9001002](../errorcode-resource-manager.md#9001002-matching-resource-not-found-based-on-the-current-resource-id) | No matching resource is found based on the resource ID. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let resource: resourceManager.Resource = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  id: $r('sys.symbol.message').id
};
try {
  let symbolValue = this.context.resourceManager.getSymbol(resource);
  console.info(`getSymbol, result: ${symbolValue}`);
  // Print the output result: getSymbol, result: 983183
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`getSymbol failed, error code: ${code}, message: ${message}.`);
}
```

## getSymbolByName

```TypeScript
getSymbolByName(resName: string) : number
```

Obtains the Unicode of a [symbol](https://developer.huawei.com/consumer/en/design/harmonyos-symbol) based on the specified resource name. This API returns the result synchronously.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resName | string | Yes | Resource name. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Unicode code (decimal) of the symbol. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001003](../errorcode-resource-manager.md#9001003-invalid-resource-name) | Invalid resource name. |
| [9001004](../errorcode-resource-manager.md#9001004-matching-resource-not-found-based-on-the-passed-resource-name) | No matching resource is found based on the resource name. |
| [9001006](../errorcode-resource-manager.md#9001006-circular-reference-in-resources) | The resource is referenced cyclically. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Replace "message" with the actual resource.
            let symbolValue = this.context.resourceManager.getSymbolByName("message");
            console.info(`getSymbolByName, result: ${symbolValue}`);
            // Print the output result: getSymbolByName, result: 983183
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`getSymbolByName failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## isRawDir

```TypeScript
isRawDir(path: string): boolean
```

Checks whether a path is a subdirectory in the **rawfile** directory. This API returns the result synchronously.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.ResourceManager

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | rawfile or subdirectory path relative to the **resources/rawfile** directory, such as **test.txt** or **subdir**. The path must not start with a slash (/). |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the path is a subdirectory in the **rawfile** directory.<br> - **true**: The path is a subdirectory in the **rawfile** directory. <br> - **false**: The path is not a subdirectory in the **rawfile** directory. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001005](../errorcode-resource-manager.md#9001005-invalid-relative-path) | Invalid relative path. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            // Assume that a non-empty folder named sub exists in the root directory (that is, /rawfile). The value of isRawDir is true in the return result.
            // Replace "sub" with the actual directory.
            let isRawDir = this.context.resourceManager.isRawDir("sub");
            // Print the output result: sub isRawDir, result: true
            console.info(`sub isRawDir, result: ${isRawDir}`);

            // If the test.txt file exists in the rawfile root directory, the value of isRawDir is false.
            // Replace "test.txt" with the actual resource.
            isRawDir = this.context.resourceManager.isRawDir("test.txt");
            // Print the output result: test.txt isRawDir, result: false
            console.info(`test.txt isRawDir, result: ${isRawDir}`);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`isRawDir failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## release

```TypeScript
release()
```

Releases an **resourceManager **object. This API is not supported currently. Calling this API does not have any effect.

**Since:** 7

**Deprecated since:** 12

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Examples**

```TypeScript
try {
  this.context.resourceManager.release();
} catch (error) {
  console.error("release error is " + error);
}
```

## removeResource

```TypeScript
removeResource(path: string) : void
```

Removes the specified overlay resource during application runtime and restores the original resource before the override.

> **NOTE:** 
> 
> Resource overwriting is not supported for the **rawfile** and **resfile** directories.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Absolute path of the HSP or HAP resource package to be removed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |
| [9001010](../errorcode-resource-manager.md#9001010-invalid-overlay-path) | Invalid overlay path. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        // Replace "/library1-default-signed.hsp" with the actual file path.
        let path = this.context.bundleCodeDir + "/library1-default-signed.hsp";
        try {
            this.context.resourceManager.removeResource(path);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`removeResource failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

## updateOverrideConfiguration

```TypeScript
updateOverrideConfiguration(configuration: Configuration): void
```

Updates the configuration of a differentiated resource management object.

This API updates the configuration of the differentiated resource management object, regardless of whether it is called on the common resource management object or on the differentiated one obtained via [getOverrideResourceManager](#getoverrideresourcemanager).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| configuration | [Configuration](arkts-localization-resourcemanager-configuration-c.md) | Yes | Configuration of differentiated resources. After obtaining the configuration of differentiated resources through [getOverrideConfiguration](#getoverrideconfiguration), modify the configuration items as required, and then pass these items as input parameters to the API. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: Incorrect parameter types. |

**Examples**

```TypeScript
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
        try {
            let resMgr = this.context.resourceManager;
            let overrideConfig = resMgr.getOverrideConfiguration();
            overrideConfig.colorMode = resourceManager.ColorMode.DARK;
            let overrideResMgr = resMgr.updateOverrideConfiguration(overrideConfig);
        } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`updateOverrideConfiguration failed, error code: ${code}, message: ${message}.`);
        }
    }
}
```

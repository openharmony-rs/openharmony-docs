# getResourceManager

## Modules to Import

```TypeScript
import { resourceManager } from '@kit.LocalizationKit';
```

## getResourceManager

```TypeScript
export function getResourceManager(callback: AsyncCallback<ResourceManager>): void
```

Obtains the **ResourceManager** object of the current application. This API uses an asynchronous callback to return the result.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-localization-resourcemanager-asynccallback-i.md)&lt;[ResourceManager](arkts-localization-resourcemanager-resourcemanager-i.md)&gt; | Yes | Callback used to return the **ResourceManager** object. |

**Examples**

```TypeScript
import resourceManager from '@ohos.resourceManager';
// Use this method to import the module in the FA model.

export default {
    onCreate() {
        resourceManager.getResourceManager((error, mgr) => {
            if (error != null) {
                console.error("error is " + error);
                return;
            }
            // Replace "test" with the actual resource name.
            mgr.getStringByName('test', (error, value) => {
                if (error) {
                    console.error("error is " + JSON.stringify(error));
                } else {
                    console.info("success is " + value);
                }

            });
        });
    }
};
```


<a id="getresourcemanager-1"></a>

## getResourceManager

```TypeScript
export function getResourceManager(bundleName: string, callback: AsyncCallback<ResourceManager>): void
```

Obtains the **ResourceManager** object of the specified application. This API uses an asynchronous callback to return the result.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application. |
| callback | [AsyncCallback](arkts-localization-resourcemanager-asynccallback-i.md)&lt;[ResourceManager](arkts-localization-resourcemanager-resourcemanager-i.md)&gt; | Yes | Callback used to return the **ResourceManager** object. |

**Examples**

```TypeScript
import resourceManager from '@ohos.resourceManager';
// Use this method to import the module in the FA model.

// Replace 'com.example.testapp' with the actual application package name.
const BUNDLE_NAME = 'com.example.testapp';

export default {
    onCreate() {
        resourceManager.getResourceManager(BUNDLE_NAME, (error, mgr) => {
            if (error != null) {
                console.error("getResourceManager error is " + error);
                return;
            }
            // Replace "test" with the actual resource name.
            mgr.getStringByName('test', (error, value) => {
                if (error) {
                    console.error("getResourceManager error is " + JSON.stringify(error));
                } else {
                    console.info("getResourceManager success is " + value);
                }
            });
        });
    }
};
```


<a id="getresourcemanager-2"></a>

## getResourceManager

```TypeScript
export function getResourceManager(): Promise<ResourceManager>
```

Obtains the **ResourceManager** object of the current application. This API uses a promise to return the result.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Global.ResourceManager

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ResourceManager](arkts-localization-resourcemanager-resourcemanager-i.md)&gt; | Promise used to return the **ResourceManager** object. |

**Examples**

```TypeScript
import resourceManager from '@ohos.resourceManager';
// Use this method to import the module in the FA model.

export default {
    onCreate() {
        resourceManager.getResourceManager().then(resMgr => {
            try {
                // Replace "test" with the actual resource name.
                let testStr = resMgr.getStringByNameSync('test')
                console.info("getResourceManager success is " + testStr);
            } catch (error) {
                console.error("getResourceManager error is " + JSON.stringify(error));
            }
        }).catch(error => {
            console.error("getResourceManager error is " + error);
        });
    }
};
```


<a id="getresourcemanager-3"></a>

## getResourceManager

```TypeScript
export function getResourceManager(bundleName: string): Promise<ResourceManager>
```

Obtains the **ResourceManager** object of the specified application. This API uses a promise to return the result.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Global.ResourceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ResourceManager](arkts-localization-resourcemanager-resourcemanager-i.md)&gt; | Promise used to return the **ResourceManager** object. |

**Examples**

```TypeScript
import resourceManager from '@ohos.resourceManager';
// Use this method to import the module in the FA model.

// Replace 'com.example.testapp' with the actual application package name.
const BUNDLE_NAME = 'com.example.testapp';

export default {
    onCreate() {
        resourceManager.getResourceManager(BUNDLE_NAME).then(resMgr => {
            try {
                // Replace "test" with the actual resource name.
                let testStr = resMgr.getStringByNameSync('test')
                console.info("getResourceManager success is " + testStr);
            } catch (error) {
                console.error("getResourceManager error is " + JSON.stringify(error));
            }
        }).catch(error => {
            console.error("getResourceManager error is " + error);
        });
    }
};
```

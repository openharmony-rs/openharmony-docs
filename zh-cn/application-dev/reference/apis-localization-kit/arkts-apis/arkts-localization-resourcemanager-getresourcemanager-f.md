# getResourceManager

## getResourceManager

```TypeScript
export function getResourceManager(callback: AsyncCallback<ResourceManager>): void
```

获取当前应用的资源管理对象，使用callback异步回调。

**起始版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;ResourceManager&gt; | 是 | 回调函数，返回资源管理ResourceManager对象。 |

**示例：**

```TypeScript
import resourceManager from '@ohos.resourceManager';
// FA模型请使用上述方式导入模块

export default {
    onCreate() {
        resourceManager.getResourceManager((error, mgr) => {
            if (error != null) {
                console.error("error is " + error);
                return;
            }
            // 'test'仅作示例，请替换为实际使用的资源名称
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


## getResourceManager

```TypeScript
export function getResourceManager(bundleName: string, callback: AsyncCallback<ResourceManager>): void
```

获取指定应用的资源管理对象，使用callback异步回调。

**起始版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用包名。 |
| callback | AsyncCallback&lt;ResourceManager&gt; | 是 | 回调函数，返回应用包名对应的资源管理ResourceManager对象。 |

**示例：**

```TypeScript
import resourceManager from '@ohos.resourceManager';
// FA模型请使用上述方式导入模块

// 'com.example.testapp'仅作示例，请替换为实际应用包名
const BUNDLE_NAME = 'com.example.testapp';

export default {
    onCreate() {
        resourceManager.getResourceManager(BUNDLE_NAME, (error, mgr) => {
            if (error != null) {
                console.error("getResourceManager error is " + error);
                return;
            }
            // 'test'仅作示例，请替换为实际使用的资源名称
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


## getResourceManager

```TypeScript
export function getResourceManager(): Promise<ResourceManager>
```

获取当前应用的资源管理对象，使用Promise异步回调。

**起始版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Global.ResourceManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ResourceManager&gt; | Promise对象，返回资源管理ResourceManager对象。 |

**示例：**

```TypeScript
import resourceManager from '@ohos.resourceManager';
// FA模型请使用上述方式导入模块

export default {
    onCreate() {
        resourceManager.getResourceManager().then(resMgr => {
            try {
                // 'test'仅作示例，请替换为实际使用的资源名称
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


## getResourceManager

```TypeScript
export function getResourceManager(bundleName: string): Promise<ResourceManager>
```

获取指定应用的资源管理对象，使用Promise异步回调。

**起始版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ResourceManager&gt; | Promise对象，返回应用包名对应的资源管理ResourceManager对象。 |

**示例：**

```TypeScript
import resourceManager from '@ohos.resourceManager';
// FA模型请使用上述方式导入模块

// 'com.example.testapp'仅作示例，请替换为实际应用包名
const BUNDLE_NAME = 'com.example.testapp';

export default {
    onCreate() {
        resourceManager.getResourceManager(BUNDLE_NAME).then(resMgr => {
            try {
                // 'test'仅作示例，请替换为实际使用的资源名称
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


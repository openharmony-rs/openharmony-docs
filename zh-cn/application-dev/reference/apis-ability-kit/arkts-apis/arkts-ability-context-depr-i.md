# Context

Context模块提供了Ability或Application的上下文的基础能力，包括允许访问特定于应用程序的资源、请求和验证权限等。

**继承/实现关系：** Context extends [BaseContext](arkts-ability-basecontext-c.md)

**起始版本：** 6

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## getAbilityInfo

```TypeScript
getAbilityInfo(callback: AsyncCallback<AbilityInfo>): void
```

检查此能力的配置是否正在更改。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;AbilityInfo&gt; | 是 | 回调函数，返回true表示该Ability的配置正在更改，否则返回false。 |

## getAbilityInfo

```TypeScript
getAbilityInfo(): Promise<AbilityInfo>
```

查询当前归属Ability详细信息。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AbilityInfo&gt; | Promise对象，返回当前归属Ability详细信息。 |

## getAppType

```TypeScript
getAppType(callback: AsyncCallback<string>): void
```

获取此应用的类型。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数，返回此应用程序的类型。 |

## getAppType

```TypeScript
getAppType(): Promise<string>
```

获取此应用的类型。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回此应用的类型。 |

## getAppVersionInfo

```TypeScript
getAppVersionInfo(callback: AsyncCallback<AppVersionInfo>): void
```

获取应用的版本信息。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;AppVersionInfo&gt; | 是 | 回调函数，返回应用版本信息。 |

## getAppVersionInfo

```TypeScript
getAppVersionInfo(): Promise<AppVersionInfo>
```

获取应用的版本信息。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AppVersionInfo&gt; | Promise对象，返回应用版本信息。 |

## getApplicationContext

```TypeScript
getApplicationContext(): Context
```

获取应用上下文信息。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Context | 返回应用上下文信息。 |

## getApplicationInfo

```TypeScript
getApplicationInfo(callback: AsyncCallback<ApplicationInfo>): void
```

获取有关当前应用程序的信息。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;ApplicationInfo&gt; | 是 | 回调函数，返回当前应用程序的信息。 |

## getApplicationInfo

```TypeScript
getApplicationInfo(): Promise<ApplicationInfo>
```

获取有关当前应用程序的信息。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ApplicationInfo&gt; | Promise对象，返回当前应用程序的信息。 |

## getBundleName

```TypeScript
getBundleName(callback: AsyncCallback<string>): void
```

获取当前ability的Bundle名称。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数，返回当前ability的Bundle名称。 |

## getBundleName

```TypeScript
getBundleName(): Promise<string>
```

获取当前ability的Bundle名称。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回当前ability的Bundle名称。 |

## getCacheDir

```TypeScript
getCacheDir(callback: AsyncCallback<string>): void
```

获取该应用程序的内部存储目录。使用callback异步回调。

**起始版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数，返回该应用程序的内部存储目录。 |

## getCacheDir

```TypeScript
getCacheDir(): Promise<string>
```

获取该应用程序的内部存储目录。使用Promise异步回调。

**起始版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回该应用程序的内部存储目录。 |

## getCallingBundle

```TypeScript
getCallingBundle(callback: AsyncCallback<string>): void
```

获取ability调用方的Bundle名称。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数，返回ability调用方的Bundle名称。 |

## getCallingBundle

```TypeScript
getCallingBundle(): Promise<string>
```

获取ability调用方的Bundle名称。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回ability调用方的Bundle名称。 |

## getDisplayOrientation

```TypeScript
getDisplayOrientation(callback: AsyncCallback<bundle.DisplayOrientation>): void
```

获取当前ability的显示方向。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;bundle.DisplayOrientation&gt; | 是 | 回调函数，返回屏幕显示方向。 |

## getDisplayOrientation

```TypeScript
getDisplayOrientation(): Promise<bundle.DisplayOrientation>
```

获取此能力的当前显示方向。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;bundle.DisplayOrientation&gt; | Indicates the screen display direction. |

## getElementName

```TypeScript
getElementName(callback: AsyncCallback<ElementName>): void
```

获取当前ability的ohos.bundleManager.ElementName对象。使用callback异步回调。
此方法仅适用于页面功能。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;ElementName&gt; | 是 | 回调函数，返回当前ability的ohos.bundleManager.ElementName对象。 |

## getElementName

```TypeScript
getElementName(): Promise<ElementName>
```

获取当前能力的ohos.bundleManager.ElementName对象。使用Promise异步回调。
此方法仅适用于页面功能。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ElementName&gt; | Promise对象，返回当前ability的ohos.bundleManager.ElementName对象。 |

## getExternalCacheDir

```TypeScript
getExternalCacheDir(callback: AsyncCallback<string>): void
```

获取应用程序的外部缓存目录。使用callback异步回调。

**起始版本：** 6

**废弃版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数，返回应用程序的缓存目录的绝对路径。 |

## getExternalCacheDir

```TypeScript
getExternalCacheDir(): Promise<string>
```

获取应用程序的外部缓存目录。使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回应用程序的缓存目录的绝对路径。 |

## getFilesDir

```TypeScript
getFilesDir(callback: AsyncCallback<string>): void
```

获取内部存储器上此应用程序的文件目录。使用callback异步回调。

**起始版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数，返回内部存储器上此应用程序的文件目录。 |

## getFilesDir

```TypeScript
getFilesDir(): Promise<string>
```

获取内部存储器上此应用程序的文件目录。使用Promise异步回调。

**起始版本：** 6

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回内部存储器上此应用程序的文件目录。 |

## getHapModuleInfo

```TypeScript
getHapModuleInfo(callback: AsyncCallback<HapModuleInfo>): void
```

获取应用的ModuleInfo对象。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;HapModuleInfo&gt; | 是 | 回调函数，返回应用的ModuleInfo对象。 |

## getHapModuleInfo

```TypeScript
getHapModuleInfo(): Promise<HapModuleInfo>
```

获取应用的ModuleInfo对象。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;HapModuleInfo&gt; | Promise对象，返回应用的ModuleInfo对象。 |

## getOrCreateDistributedDir

```TypeScript
getOrCreateDistributedDir(): Promise<string>
```

获取Ability或应用的分布式文件路径。使用callback异步回调。
如果分布式文件路径不存在，系统将创建一个路径并返回创建的路径。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | 回调函数，返回Ability或应用的分布式文件路径。若路径不存在，系统将创建一个路径并返回创建的路径。 |

## getOrCreateDistributedDir

```TypeScript
getOrCreateDistributedDir(callback: AsyncCallback<string>): void
```

获取Ability或应用的分布式文件路径。使用Promise异步回调。
如果分布式文件路径不存在，系统将创建一个路径并返回创建的路径。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;string&gt; | 是 | Promise对象，返回Ability或应用的分布式文件路径。若为首次调用，则将创建建目录。 |

## getOrCreateLocalDir

```TypeScript
getOrCreateLocalDir(): Promise<string>
```

获取应用程序的本地根目录。使用Promise异步回调。
如果是第一次调用，将创建目录。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回应用程序的本地根目录。 |

## getOrCreateLocalDir

```TypeScript
getOrCreateLocalDir(callback: AsyncCallback<string>): void
```

获取应用程序的本地根目录。使用callback异步回调。
如果是第一次调用，将创建目录。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数，返回应用程序的本地根目录。 |

## getProcessInfo

```TypeScript
getProcessInfo(callback: AsyncCallback<ProcessInfo>): void
```

获取有关当前进程的信息，包括进程ID和名称。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;ProcessInfo&gt; | 是 | 回调函数，返回当前进程的信息。 |

## getProcessInfo

```TypeScript
getProcessInfo(): Promise<ProcessInfo>
```

获取有关当前进程的信息，包括进程id和名称。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ProcessInfo&gt; | Promise对象，返回当前进程的信息。 |

## getProcessName

```TypeScript
getProcessName(callback: AsyncCallback<string>): void
```

获取当前进程的名称。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数，返回当前进程的名称。 |

## getProcessName

```TypeScript
getProcessName(): Promise<string>
```

获取当前进程的名称。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回当前进程的名称。 |

## isUpdatingConfigurations

```TypeScript
isUpdatingConfigurations(callback: AsyncCallback<boolean>): void
```

检查此能力的配置是否正在更改。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数，返回true表示该Ability的配置正在更改，否则返回false。 |

## isUpdatingConfigurations

```TypeScript
isUpdatingConfigurations(): Promise<boolean>
```

检查此能力的配置是否正在更改。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回true表示该Ability的配置正在更改，否则返回false。 |

## printDrawnCompleted

```TypeScript
printDrawnCompleted(callback: AsyncCallback<void>): void
```

通知系统绘制此页面功能所需的时间。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当通知系统绘制此页面功能所需的时间成功，err为undefined，否则为错误对象。 |

## printDrawnCompleted

```TypeScript
printDrawnCompleted(): Promise<void>
```

通知系统绘制此页面功能所需的时间。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象 |

## requestPermissionsFromUser

```TypeScript
requestPermissionsFromUser(
    permissions: Array<string>,
    requestCode: number,
    resultCallback: AsyncCallback<PermissionRequestResult>
  ): void
```

从系统请求某些权限。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permissions | Array&lt;string&gt; | 是 | 指示要请求的权限列表。此参数不能为null。 |
| requestCode | number | 是 | 指示要传递给[PermissionRequestResult](arkts-ability-permissionrequestresult-depr-i.md)的请求代码。 |
| resultCallback | AsyncCallback&lt;PermissionRequestResult&gt; | 是 | 回调函数，返回授权结果信息。 |

## requestPermissionsFromUser

```TypeScript
requestPermissionsFromUser(permissions: Array<string>, requestCode: number): Promise<PermissionRequestResult>
```

从系统请求某些权限。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permissions | Array&lt;string&gt; | 是 | 指示要请求的权限列表。此参数不能为null。 |
| requestCode | number | 是 | 指示要传递给[PermissionRequestResult](arkts-ability-permissionrequestresult-depr-i.md)的请求代码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PermissionRequestResult&gt; | Promise对象，返回授权结果信息。 |

## setDisplayOrientation

```TypeScript
setDisplayOrientation(orientation: bundle.DisplayOrientation, callback: AsyncCallback<void>): void
```

设置当前Ability的显示方向。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| orientation | bundle.DisplayOrientation | 是 | 指示当前能力的新方向。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当设置当前Ability的显示方向成功，err为undefined，否则为错误对象。 |

## setDisplayOrientation

```TypeScript
setDisplayOrientation(orientation: bundle.DisplayOrientation): Promise<void>
```

设置当前Ability的显示方向。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| orientation | bundle.DisplayOrientation | 是 | 表示屏幕显示方向。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

## setShowOnLockScreen

```TypeScript
setShowOnLockScreen(show: boolean, callback: AsyncCallback<void>): void
```

设置每当显示锁屏时是否在锁屏顶部显示此功能，使该功能保持激活状态。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [setShowOnLockScreen](../../apis-arkui/arkts-apis/arkts-arkui-windowstage-i-sys.md#setshowonlockscreen-1)

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| show | boolean | 是 | 指定是否在锁屏顶部显示此功能。值true表示在锁屏上显示，值false表示不显示。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当设置每当显示锁屏时是否在锁屏顶部显示此功能并使该功能保持激活状态的操作成功，err为undefined，否则为错误对象。 |

## setShowOnLockScreen

```TypeScript
setShowOnLockScreen(show: boolean): Promise<void>
```

设置每当显示锁屏时是否在锁屏顶部显示此功能，使该功能保持激活状态。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [setShowOnLockScreen](../../apis-arkui/arkts-apis/arkts-arkui-windowstage-i-sys.md#setshowonlockscreen-1)

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| show | boolean | 是 | 指定是否在锁屏顶部显示此功能。值true表示在锁屏上显示，值false表示不显示。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

## setWakeUpScreen

```TypeScript
setWakeUpScreen(wakeUp: boolean, callback: AsyncCallback<void>): void
```

设置恢复此功能时是否唤醒屏幕。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 12

**替代接口：** setWakeUpScreen

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wakeUp | boolean | 是 | 指定是否唤醒屏幕。值true表示唤醒它，值false表示不唤醒它。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当设置恢复此功能时是否唤醒屏幕成功，err为undefined，否则为错误对象。 |

## setWakeUpScreen

```TypeScript
setWakeUpScreen(wakeUp: boolean): Promise<void>
```

设置恢复此功能时是否唤醒屏幕。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 12

**替代接口：** setWakeUpScreen

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wakeUp | boolean | 是 | 指定是否唤醒屏幕。值true表示唤醒它，值false表示不唤醒它。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

## verifyPermission

```TypeScript
verifyPermission(permission: string, options?: PermissionOptions): Promise<number>
```

验证系统中运行的特定pid和uid是否具有指定的权限。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permission | string | 是 | 指定权限的名称。 |
| options | PermissionOptions | 否 | 权限选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，如果pid和uid具有权限，则使用0进行异步回调；否则使用-1回调。 |

## verifyPermission

```TypeScript
verifyPermission(permission: string, options: PermissionOptions, callback: AsyncCallback<number>): void
```

验证系统中运行的特定pid和uid是否允许指定的权限。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permission | string | 是 | 指定权限的名称。 |
| options | PermissionOptions | 是 | 权限选项。 |
| callback | AsyncCallback&lt;number&gt; | 是 | 回调函数，返回权限验证结果，0有权限，-1无权限。 |

## verifyPermission

```TypeScript
verifyPermission(permission: string, callback: AsyncCallback<number>): void
```

验证系统中运行的当前pid和uid是否具有指定的权限。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permission | string | 是 | 指定权限的名称。 |
| callback | AsyncCallback&lt;number&gt; | 是 | 回调函数，返回权限验证结果，0有权限，-1无权限。 |


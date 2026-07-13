# getLaunchWantForBundle

## getLaunchWantForBundle

```TypeScript
function getLaunchWantForBundle(bundleName: string, callback: AsyncCallback<Want>): void
```

查询拉起指定应用的want对象，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要查询的应用Bundle名称。 |
| callback | AsyncCallback&lt;Want&gt; | 是 | 程序启动作为入参的回调函数，返回拉起指定应用的want对象。 |


## getLaunchWantForBundle

```TypeScript
function getLaunchWantForBundle(bundleName: string): Promise<Want>
```

查询拉起指定应用的want对象，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要查询的应用Bundle名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Want&gt; | Returns the Want for starting the application's main ability if any. |


# getNameForUid

## getNameForUid

```TypeScript
function getNameForUid(uid: number, callback: AsyncCallback<string>): void
```

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getBundleNameByUid

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | number | 是 | @param { AsyncCallback&lt;string&gt; } callback |
| callback | AsyncCallback&lt;string&gt; | 是 |  |


## getNameForUid

```TypeScript
function getNameForUid(uid: number): Promise<string>
```

通过uid获取对应的Bundle名称，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | number | 是 | 要查询的uid。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Returns the bundle name. |


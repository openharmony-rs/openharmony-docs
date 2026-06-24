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
| uid | number | 是 | @param { AsyncCallback } callback |
| callback | AsyncCallback&lt;string&gt; | 是 |  |


## getNameForUid

```TypeScript
function getNameForUid(uid: number): Promise<string>
```

ͨ��uid��ȡ��Ӧ��Bundle���ƣ�ʹ��Promise�첽�ص���

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | number | 是 | Ҫ��ѯ��uid�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Returns the bundle name. |


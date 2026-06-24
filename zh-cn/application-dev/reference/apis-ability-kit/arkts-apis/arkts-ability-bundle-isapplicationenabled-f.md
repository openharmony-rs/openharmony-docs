# isApplicationEnabled

## isApplicationEnabled

```TypeScript
function isApplicationEnabled(bundleName: string, callback: AsyncCallback<boolean>): void
```

���ݸ�����bundleName��ѯָ��Ӧ�ó����Ƿ��Ѿ����ã�ʹ��callback�첽�ص���

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ��ѯ��Ӧ��Bundle���ơ� |
| callback | AsyncCallback&lt;boolean&gt; | 是 | �ص�����������boolean�����Ƿ����á� |


## isApplicationEnabled

```TypeScript
function isApplicationEnabled(bundleName: string): Promise<boolean>
```

���ݸ�����bundleName��ѯָ��Ӧ�ó����Ƿ��Ѿ����ã�ʹ��Promise�첽�ص���

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ��ѯ��Ӧ��Bundle���ơ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise��ʽ����boolean�����Ƿ����á� |


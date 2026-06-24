# cleanBundleCacheFiles（系统接口）

## cleanBundleCacheFiles

```TypeScript
function cleanBundleCacheFiles(bundleName: string, callback: AsyncCallback<void>): void
```

���ָ��Ӧ�ó���Ļ������ݣ�ʹ��callback�첽�ص���

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.REMOVE_CACHE_FILES

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ָʾҪ����仺�����ݵ�Ӧ��Bundle���ơ� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص������� |


## cleanBundleCacheFiles

```TypeScript
function cleanBundleCacheFiles(bundleName: string): Promise<void>
```

���ָ��Ӧ�ó���Ļ������ݣ�ʹ��Promise�첽�ص���

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.REMOVE_CACHE_FILES

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ָʾҪ����仺�����ݵ�Ӧ��Bundle���ơ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ����Promise���� |


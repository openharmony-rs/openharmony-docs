# getLaunchWantForBundle

## getLaunchWantForBundle

```TypeScript
function getLaunchWantForBundle(bundleName: string, callback: AsyncCallback<Want>): void
```

��ѯ����ָ��Ӧ�õ�want����ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ��ѯ��Ӧ��Bundle���ơ� |
| callback | AsyncCallback&lt;Want&gt; | 是 | ����������Ϊ��εĻص���������������ָ��Ӧ�õ�want���� |


## getLaunchWantForBundle

```TypeScript
function getLaunchWantForBundle(bundleName: string): Promise<Want>
```

��ѯ����ָ��Ӧ�õ�want����ʹ��Promise�첽�ص���

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ��ѯ��Ӧ��Bundle���ơ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Want&gt; | Returns the Want for starting the application's main ability if any. |


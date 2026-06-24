# getApplicationInfo

## getApplicationInfo

```TypeScript
function getApplicationInfo(bundleName: string,
    bundleFlags: number, userId: number, callback: AsyncCallback<ApplicationInfo>): void
```

���ݸ�����Bundle���ƻ�ȡָ���û��µ�ApplicationInfo��ʹ��callback�첽�ص���

��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ��ѯ��Ӧ��Bundle���ơ� |
| bundleFlags | number | 是 | ����ָ�����ص�Ӧ����Ϣ�����а�����Ϣ�ı�ǡ�ȡֵ��Χ���ο�[BundleFlag˵��](arkts-ability-bundle-bundleflag-e.md#BundleFlag)��Ӧ����Ϣ���flag�� |
| userId | number | 是 | �û�ID��ȡֵ��Χ�����ڵ���0�� |
| callback | AsyncCallback&lt;ApplicationInfo&gt; | 是 | ����������Ϊ��εĻص�����������Ӧ�ó�����Ϣ�� |


## getApplicationInfo

```TypeScript
function getApplicationInfo(bundleName: string, bundleFlags: number, callback: AsyncCallback<ApplicationInfo>): void
```

���ݸ�����Bundle���ƻ�ȡApplicationInfo��ʹ��callback�첽�ص���

��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ��ѯ��Ӧ��Bundle���ơ� |
| bundleFlags | number | 是 | ����ָ�����ص�Ӧ����Ϣ�����а�����Ϣ�ı�ǡ�ȡֵ��Χ���ο�[BundleFlag˵��](arkts-ability-bundle-bundleflag-e.md#BundleFlag)��Ӧ����Ϣ���flag�� |
| callback | AsyncCallback&lt;ApplicationInfo&gt; | 是 | ����������Ϊ��εĻص�����������Ӧ�ó�����Ϣ�� |


## getApplicationInfo

```TypeScript
function getApplicationInfo(bundleName: string, bundleFlags: number, userId?: number): Promise<ApplicationInfo>
```

���ݸ�����Bundle���ƻ�ȡApplicationInfo��ʹ��Promise�첽�ص���

��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ��ѯ��Ӧ��Bundle���ơ� |
| bundleFlags | number | 是 | ����ָ�����ص�Ӧ����Ϣ�����а�����Ϣ�ı�ǡ�ȡֵ��Χ��ο�[BundleFlag˵��](arkts-ability-bundle-bundleflag-e.md#BundleFlag)��Ӧ����Ϣ���flag�� |
| userId | number | 否 | �û�ID��Ĭ��ֵ�����÷������û���ȡֵ��Χ�����ڵ���0�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ApplicationInfo&gt; | Promise��ʽ����Ӧ�ó�����Ϣ�� |


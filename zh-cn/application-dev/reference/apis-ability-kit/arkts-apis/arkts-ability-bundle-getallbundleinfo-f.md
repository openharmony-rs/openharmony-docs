# getAllBundleInfo

## getAllBundleInfo

```TypeScript
function getAllBundleInfo(bundleFlag: BundleFlag, userId: number, callback: AsyncCallback<Array<BundleInfo>>): void
```

��ȡϵͳ��ָ���û������е�BundleInfo��ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlag | BundleFlag | 是 | ����ָ�����ص�Ӧ����Ϣ�����а�����Ϣ�ı�ǡ�ȡֵ��Χ���ο�[BundleFlag˵��](arkts-ability-bundle-bundleflag-e.md#BundleFlag)�а���Ϣ���flag�� |
| userId | number | 是 | �û�ID��Ĭ��ֵ�����÷������û���ȡֵ��Χ�����ڵ���0�� |
| callback | AsyncCallback&lt;Array&lt;BundleInfo&gt;&gt; | 是 | ����������Ϊ��εĻص�����������ָ���û������а���BundleInfo�� |


## getAllBundleInfo

```TypeScript
function getAllBundleInfo(bundleFlag: BundleFlag, callback: AsyncCallback<Array<BundleInfo>>): void
```

��ȡ��ǰ�û����е�BundleInfo��ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlag | BundleFlag | 是 | ����ָ�����ص�Ӧ����Ϣ�����а�����Ϣ�ı�ǡ�ȡֵ��Χ���ο�[BundleFlag˵��](arkts-ability-bundle-bundleflag-e.md#BundleFlag)�а���Ϣ���flag�� |
| callback | AsyncCallback&lt;Array&lt;BundleInfo&gt;&gt; | 是 | ����������Ϊ��εĻص��������������п��õ�BundleInfo�� |


## getAllBundleInfo

```TypeScript
function getAllBundleInfo(bundleFlag: BundleFlag, userId?: number): Promise<Array<BundleInfo>>
```

��ȡָ���û����е�BundleInfo��ʹ��Promise��ʽ�첽�ص���

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlag | BundleFlag | 是 | ����ָ�����صİ���Ϣ�����а�����Ϣ�ı�ǡ�ȡֵ��Χ���ο�[BundleFlag˵��](arkts-ability-bundle-bundleflag-e.md#BundleFlag)�а���Ϣ���flag�� |
| userId | number | 否 | �û�ID��Ĭ��ֵ�����÷������û���ȡֵ��Χ�����ڵ���0�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;BundleInfo&gt;&gt; | Promise��ʽ�������п��õ�BundleInfo |


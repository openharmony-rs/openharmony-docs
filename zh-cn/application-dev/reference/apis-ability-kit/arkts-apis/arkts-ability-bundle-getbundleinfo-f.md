# getBundleInfo

## getBundleInfo

```TypeScript
function getBundleInfo(bundleName: string,
    bundleFlags: number, options: BundleOptions, callback: AsyncCallback<BundleInfo>): void
```

���ݸ�����Bundle���ƻ�ȡBundleInfo��ʹ��callback�첽�ص���

��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ��ѯ��Ӧ��Bundle���ơ� |
| bundleFlags | number | 是 | ����ָ�����ص�Ӧ����Ϣ�����а�����Ϣ�ı�ǡ�ȡֵ��Χ���ο�[BundleFlag˵��](arkts-ability-bundle-bundleflag-e.md#BundleFlag)�а���Ϣ���flag�� |
| options | BundleOptions | 是 | ����userid�� |
| callback | AsyncCallback&lt;BundleInfo&gt; | 是 | ����������Ϊ��εĻص����������ذ���Ϣ�� |


## getBundleInfo

```TypeScript
function getBundleInfo(bundleName: string, bundleFlags: number, callback: AsyncCallback<BundleInfo>): void
```

���ݸ�����Bundle���ƻ�ȡBundleInfo��ʹ��callback�첽�ص���

��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��Ҫ��ѯ��Ӧ��Bundle���ơ� |
| bundleFlags | number | 是 | ����ָ�����ص�Ӧ����Ϣ�����а�����Ϣ�ı�ǡ�ȡֵ��Χ���ο�[BundleFlag˵��](arkts-ability-bundle-bundleflag-e.md#BundleFlag)�а���Ϣ���flag�� |
| callback | AsyncCallback&lt;BundleInfo&gt; | 是 | ����������Ϊ��εĻص����������ذ���Ϣ�� |


## getBundleInfo

```TypeScript
function getBundleInfo(bundleName: string, bundleFlags: number, options?: BundleOptions): Promise<BundleInfo>
```

���ݸ�����Bundle���ƻ�ȡBundleInfo��ʹ��Promise�첽�ص���

��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ҫ��ѯ��Ӧ��Bundle���ơ� |
| bundleFlags | number | 是 | ����ָ�����ص�Ӧ����Ϣ�����а�����Ϣ�ı�ǡ�ȡֵ��Χ���ο�[BundleFlag˵��](arkts-ability-bundle-bundleflag-e.md#BundleFlag)�а���Ϣ���flag�� |
| options | BundleOptions | 否 | ����userid�Ĳ�ѯѡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;BundleInfo&gt; | Promise���󣬻�ȡ�ɹ�ʱ���ذ���Ϣ�� |


# getBundleArchiveInfo

## getBundleArchiveInfo

```TypeScript
function getBundleArchiveInfo(hapFilePath: string, bundleFlags: number, callback: AsyncCallback<BundleInfo>): void
```

��ȡ�й�HAP�а�����Ӧ�ó��������Ϣ��ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hapFilePath | string | 是 | HAP���·����֧�ֵ�ǰӦ�ó���ľ���·��������Ŀ¼ɳ��·���� |
| bundleFlags | number | 是 | ����ָ��Ҫ���ص�BundleInfo�����а�����Ϣ�ı�ǡ�ȡֵ��Χ���ο�[BundleFlag˵��](arkts-ability-bundle-bundleflag-e.md#BundleFlag)�а���Ϣ���<br/>flag�� |
| callback | AsyncCallback&lt;BundleInfo&gt; | 是 | ����������Ϊ��εĻص�����������HAP�а�����Ӧ�ó��������Ϣ�� |


## getBundleArchiveInfo

```TypeScript
function getBundleArchiveInfo(hapFilePath: string, bundleFlags: number): Promise<BundleInfo>
```

��ȡ�й�HAP�а�����Ӧ�ó��������Ϣ��ʹ��Promise�첽�ص���

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hapFilePath | string | 是 | HAP���·����֧�ֵ�ǰӦ�ó���ľ���·��������Ŀ¼ɳ��·���� |
| bundleFlags | number | 是 | ����ָ��Ҫ���ص�BundleInfo�����а�����Ϣ�ı�ǡ�ȡֵ��Χ���ο�[BundleFlag˵��](arkts-ability-bundle-bundleflag-e.md#BundleFlag)�а���Ϣ���<br/>flag�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;BundleInfo&gt; | - Returns the BundleInfo object. |


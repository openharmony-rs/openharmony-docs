# on（系统接口）

## on('BundleStatusChange')

```TypeScript
function on(type: 'BundleStatusChange',
    bundleStatusCallback: BundleStatusCallback, callback: AsyncCallback<string>): void
```

ע��Callback��

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [on](arkts-ability-bundlemonitor-on-f-sys.md#on-1)
> �����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'BundleStatusChange' | 是 | ָʾӦִ�����ֻ֧��BundleStatusChange�� |
| bundleStatusCallback | BundleStatusCallback | 是 | ָʾҪע��Ļص��� |
| callback | AsyncCallback&lt;string&gt; | 是 | ����������Ϊ��εĻص�������������ȷ����������Ϣ�� |


## on('BundleStatusChange')

```TypeScript
function on(type: 'BundleStatusChange', bundleStatusCallback: BundleStatusCallback): Promise<string>
```

ע��Callback��

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [on](arkts-ability-bundlemonitor-on-f-sys.md#on-1)
> �����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'BundleStatusChange' | 是 | ָʾӦִ�����ֻ֧��BundleStatusChange�� |
| bundleStatusCallback | BundleStatusCallback | 是 | ָʾҪע��Ļص��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | - Promise��ʽ������ȷ����������Ϣ�� |


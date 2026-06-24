# off（系统接口）

## off('BundleStatusChange')

```TypeScript
function off(type: 'BundleStatusChange', callback: AsyncCallback<string>): void
```

ȡ��ע��Callback��

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [off](arkts-ability-bundlemonitor-off-f-sys.md#off-1)
> �����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** off

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'BundleStatusChange' | 是 | ָʾӦִ�����ֻ֧��BundleStatusChange�� |
| callback | AsyncCallback&lt;string&gt; | 是 | ����������Ϊ��εĻص�������������ȷ����������Ϣ�� |


## off

```TypeScript
function off(type: 'BundleStatusChange'): Promise<string>
```

ȡ��ע��Callback��

> **˵����**
>
> ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��
> [off](arkts-ability-bundlemonitor-off-f-sys.md#off-1)
> �����

**起始版本：** 8

**废弃版本：** 9

**替代接口：** off

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'BundleStatusChange' | 是 | ָʾӦִ�����ֻ֧��BundleStatusChange�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise��ʽ������ȷ����������Ϣ�� |


# getRemoteAbilityInfos（系统接口）

## getRemoteAbilityInfos

```TypeScript
function getRemoteAbilityInfos(elementNames: Array<ElementName>,
    callback: AsyncCallback<Array<RemoteAbilityInfo>>): void
```

���ݸ�����ElementName��ȡ�й�Զ���豸AbilityInfos��Ϣ��ʹ��callback�첽�ص���

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementNames | Array&lt;ElementName&gt; | 是 | ElementName��Ϣ��������鳤��Ϊ10�� |
| callback | AsyncCallback&lt;Array&lt;RemoteAbilityInfo&gt;&gt; | 是 | ����������Ϊ��εĻص�����������Զ�̻���������Ϣ�� |


## getRemoteAbilityInfos

```TypeScript
function getRemoteAbilityInfos(elementNames: Array<ElementName>): Promise<Array<RemoteAbilityInfo>>
```

���ݸ�����ElementName��ȡ�й�Զ���豸AbilityInfos��Ϣ��ʹ��Promise�첽�ص���

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementNames | Array&lt;ElementName&gt; | 是 | ElementName��Ϣ��������鳤��Ϊ10�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;RemoteAbilityInfo&gt;&gt; | Promise��ʽ����Զ�̻���������Ϣ�� |


# getRemoteAbilityInfo（系统接口）

## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementName: ElementName, callback: AsyncCallback<RemoteAbilityInfo>): void
```

���ݸ�����ElementName��ȡ�й�Զ���豸AbilityInfo��Ϣ��ʹ��callback�첽�ص���

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | ElementName | 是 | ��õ�ElementName��Ϣ�� |
| callback | AsyncCallback&lt;RemoteAbilityInfo&gt; | 是 | ����������Ϊ��εĻص�����������Զ�̻���������Ϣ�� |


## getRemoteAbilityInfo

```TypeScript
function getRemoteAbilityInfo(elementName: ElementName): Promise<RemoteAbilityInfo>
```

���ݸ�����ElementName��ȡ�й�Զ���豸AbilityInfo��Ϣ��ʹ��Promise�첽�ص���

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.DistributedBundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | ElementName | 是 | ��õ�ElementName��Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RemoteAbilityInfo&gt; | Promise��ʽ����Զ�̻���������Ϣ�� |


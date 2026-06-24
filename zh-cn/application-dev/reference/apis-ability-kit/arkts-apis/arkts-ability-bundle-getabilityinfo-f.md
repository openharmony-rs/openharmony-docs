# getAbilityInfo

## getAbilityInfo

```TypeScript
function getAbilityInfo(bundleName: string, abilityName: string, callback: AsyncCallback<AbilityInfo>): void
```

ͨ��Bundle���ƺ��������ȡAbility�����Ϣ��ʹ��callback�첽�ص���

��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ӧ��Bundle���ơ� |
| abilityName | string | 是 | Ability���ơ� |
| callback | AsyncCallback&lt;AbilityInfo&gt; | 是 | ����������Ϊ��εĻص�����������Ability��Ϣ�� |


## getAbilityInfo

```TypeScript
function getAbilityInfo(bundleName: string, abilityName: string): Promise<AbilityInfo>
```

ͨ��Bundle���ƺ��������ȡAbility�����Ϣ��ʹ��Promise��ʽ�첽�ص���

��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ӧ��Bundle���ơ� |
| abilityName | string | 是 | Ability������ơ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AbilityInfo&gt; | Promise��ʽ����Ability��Ϣ�� |


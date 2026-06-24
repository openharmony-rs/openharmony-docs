# getAbilityLabel

## getAbilityLabel

```TypeScript
function getAbilityLabel(bundleName: string, abilityName: string, callback: AsyncCallback<string>): void
```

ͨ��Bundle���ƺ�Ability�������ȡӦ�����ƣ�ʹ��callback�첽�ص���

��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�

**起始版本：** 8

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ӧ��Bundle���ơ� |
| abilityName | string | 是 | Ability���ơ� |
| callback | AsyncCallback&lt;string&gt; | 是 | ����������Ϊ��εĻص�����������Ӧ��������Ϣ�� |


## getAbilityLabel

```TypeScript
function getAbilityLabel(bundleName: string, abilityName: string): Promise<string>
```

ͨ��Bundle���ƺ�ability���ƻ�ȡӦ�����ƣ�ʹ��Promise�첽�ص���

��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�

**起始版本：** 8

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ӧ��Bundle���ơ� |
| abilityName | string | 是 | Ability���ơ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise��ʽ����Ӧ��������Ϣ�� |


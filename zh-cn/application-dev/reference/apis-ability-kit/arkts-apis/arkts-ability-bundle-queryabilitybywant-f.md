# queryAbilityByWant

## queryAbilityByWant

```TypeScript
function queryAbilityByWant(want: Want,
    bundleFlags: number, userId: number, callback: AsyncCallback<Array<AbilityInfo>>): void
```

���ݸ�������ͼ��ȡָ���û���Ability��Ϣ��ʹ��callback�첽�ص���

��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | ָʾ����Ҫ��ѯ��Ӧ��Bundle���Ƶ���ͼ�� |
| bundleFlags | number | 是 | ����ָ������abilityInfo��Ϣ��ȡֵ��Χ���ο�[BundleFlag˵��](arkts-ability-bundle-bundleflag-e.md#BundleFlag)��Ability��Ϣ���flag�� |
| userId | number | 是 | �û�ID��ȡֵ��Χ�����ڵ���0�� |
| callback | AsyncCallback&lt;Array&lt;AbilityInfo&gt;&gt; | 是 | ����������Ϊ��εĻص�����������Ability��Ϣ�� |


## queryAbilityByWant

```TypeScript
function queryAbilityByWant(want: Want, bundleFlags: number, callback: AsyncCallback<Array<AbilityInfo>>): void
```

���ݸ�������ͼ��ȡAbility��Ϣ��ʹ��callback�첽�ص���

��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | ָʾ����Ҫ��ѯ��Ӧ��Bundle���Ƶ���ͼ�� |
| bundleFlags | number | 是 | ����ָ������abilityInfo��Ϣ��ȡֵ��Χ���ο�[BundleFlag˵��](arkts-ability-bundle-bundleflag-e.md#BundleFlag)��Ability��Ϣ���flag�� |
| callback | AsyncCallback&lt;Array&lt;AbilityInfo&gt;&gt; | 是 | ����������Ϊ��εĻص�����������Ability��Ϣ�� |


## queryAbilityByWant

```TypeScript
function queryAbilityByWant(want: Want, bundleFlags: number, userId?: number): Promise<Array<AbilityInfo>>
```

���ݸ�������ͼ��ȡAbility�����Ϣ��ʹ��Promise�첽�ص���

��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | ����Ҫ��ѯ��Ӧ��Bundle���Ƶ���ͼ�� |
| bundleFlags | number | 是 | ����ָ������abilityInfo��Ϣ��ȡֵ��Χ���ο�[BundleFlag˵��](arkts-ability-bundle-bundleflag-e.md#BundleFlag)��Ability��Ϣ���flag�� |
| userId | number | 否 | �û�ID��Ĭ��ֵ�����÷������û���ȡֵ��Χ�����ڵ���0�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AbilityInfo&gt;&gt; | Promise��ʽ����Ability��Ϣ�� |


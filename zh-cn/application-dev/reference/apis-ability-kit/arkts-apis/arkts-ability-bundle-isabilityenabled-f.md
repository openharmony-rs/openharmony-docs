# isAbilityEnabled

## isAbilityEnabled

```TypeScript
function isAbilityEnabled(info: AbilityInfo, callback: AsyncCallback<boolean>): void
```

���ݸ�����AbilityInfo��ѯability�Ƿ��Ѿ����ã�ʹ��callback�첽�ص���

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | AbilityInfo | 是 | Ability��������Ϣ�� |
| callback | AsyncCallback&lt;boolean&gt; | 是 | �ص�����������boolean�����Ƿ����á� |


## isAbilityEnabled

```TypeScript
function isAbilityEnabled(info: AbilityInfo): Promise<boolean>
```

���ݸ�����AbilityInfo��ѯability�Ƿ��Ѿ����ã�ʹ��Promise�첽�ص���

**起始版本：** 8

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | AbilityInfo | 是 | Ability��������Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise��ʽ����boolean�����Ƿ����á� |


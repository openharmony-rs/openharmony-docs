# setAbilityEnabled（系统接口）

## setAbilityEnabled

```TypeScript
function setAbilityEnabled(info: AbilityInfo, isEnable: boolean, callback: AsyncCallback<void>): void
```

�����Ƿ�����ָ����Ability�����ʹ��callback�첽�ص���

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | AbilityInfo | 是 | Ability��Ϣ��ָʾ��Ҫ��������״̬��Ability�� |
| isEnable | boolean | 是 | ָ���Ƿ�����Ӧ�ó���true��ʾ���ã�false���á� |
| callback | AsyncCallback&lt;void&gt; | 是 | Ϊ���ز�����������õĻص��� |


## setAbilityEnabled

```TypeScript
function setAbilityEnabled(info: AbilityInfo, isEnable: boolean): Promise<void>
```

�����Ƿ�����ָ����Ability�����ʹ��Promise�첽�ص���

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | AbilityInfo | 是 | Ability��Ϣ��ָʾ��Ҫ��������״̬��Ability�� |
| isEnable | boolean | 是 | ָ���Ƿ�����Ӧ�ó���true��ʾ���ã�false���á� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ����Promise���� |


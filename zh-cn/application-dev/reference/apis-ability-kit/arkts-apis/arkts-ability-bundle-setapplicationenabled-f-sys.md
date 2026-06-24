# setApplicationEnabled（系统接口）

## setApplicationEnabled

```TypeScript
function setApplicationEnabled(bundleName: string, isEnable: boolean, callback: AsyncCallback<void>): void
```

�����Ƿ�����ָ����Ӧ�ó���ʹ��callback�첽�ص���

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ָʾ��Ҫ���û���õ�Ӧ��Bundle���ơ� |
| isEnable | boolean | 是 | ָ���Ƿ�����Ӧ�ó���true��ʾ���ã�false��ʾ���á� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص������� |


## setApplicationEnabled

```TypeScript
function setApplicationEnabled(bundleName: string, isEnable: boolean): Promise<void>
```

�����Ƿ�����ָ����Ӧ�ó���ʹ��Promise�첽�ص���

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ָʾ��Ҫ���û���õ�Ӧ��Bundle���ơ� |
| isEnable | boolean | 是 | ָ���Ƿ�����Ӧ�ó���true��ʾ���ã�false���á� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ����Promise���� |


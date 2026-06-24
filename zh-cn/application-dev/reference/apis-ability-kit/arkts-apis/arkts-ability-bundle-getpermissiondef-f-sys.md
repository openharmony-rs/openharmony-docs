# getPermissionDef（系统接口）

## getPermissionDef

```TypeScript
function getPermissionDef(permissionName: string, callback: AsyncCallback<PermissionDef>): void
```

��Ȩ�����ƻ�ȡȨ�޵���ϸ��Ϣ��ʹ��callback�첽�ص���

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permissionName | string | 是 | ��Ҫ��ѯ��Ȩ�޵����ơ� |
| callback | AsyncCallback&lt;PermissionDef&gt; | 是 | ����������Ϊ��εĻص����������ض����Ȩ����Ϣ�� |


## getPermissionDef

```TypeScript
function getPermissionDef(permissionName: string): Promise<PermissionDef>
```

��Ȩ�����ƻ�ȡȨ�޵���ϸ��Ϣ��ʹ��promise�첽�ص���

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permissionName | string | 是 | ��Ҫ��ѯ��Ȩ�޵����ơ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PermissionDef&gt; | Promise���󣬻�ȡ�ɹ�ʱ����Ȩ����ϸ��Ϣ�� |


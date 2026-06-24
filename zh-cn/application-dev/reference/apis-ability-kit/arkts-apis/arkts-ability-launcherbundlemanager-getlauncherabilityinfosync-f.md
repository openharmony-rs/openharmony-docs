# getLauncherAbilityInfoSync

## getLauncherAbilityInfoSync

```TypeScript
function getLauncherAbilityInfoSync(bundleName: string, userId: number): Array<LauncherAbilityInfo>
```

��ѯָ��bundleName���û���[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md#LauncherAbilityInfo)��

**起始版本：** 18

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ӧ��Bundle���ơ� |
| userId | number | 是 | ����ѯ���û�ID������ͨ��<br/>[getOsAccountLocalId�ӿ�](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;LauncherAbilityInfo&gt; | Array��ʽ����bundle������<br/>[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md#LauncherAbilityInfo)��Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Verify) | Verify permission denied. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not support. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |


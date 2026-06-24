# deleteDesktopShortcutInfo（系统接口）

## deleteDesktopShortcutInfo

```TypeScript
function deleteDesktopShortcutInfo(shortcutInfo: ShortcutInfo, userId: number): Promise<void>
```

ɾ��ָ���û��Ŀ�ݷ�ʽ��Ϣ��ʹ��Promise�첽�ص���

**起始版本：** 12

**需要权限：** ohos.permission.MANAGE_SHORTCUTS

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shortcutInfo | ShortcutInfo | 是 | ��ݷ�ʽ��Ϣ�� |
| userId | number | 是 | �û�id������ͨ��<br/>[getOsAccountLocalId�ӿ�](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>��ȡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Verify) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700004](../../errorcode-universal.md#17700004-The) | The specified user ID is not found. |


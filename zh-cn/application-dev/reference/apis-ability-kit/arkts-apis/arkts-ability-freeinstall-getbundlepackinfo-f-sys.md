# getBundlePackInfo（系统接口）

## getBundlePackInfo

```TypeScript
function getBundlePackInfo(bundleName: string, 
    bundlePackFlag : BundlePackFlag, callback: AsyncCallback<BundlePackInfo>): void
```

����bundleName��bundlePackFlag����ȡbundlePackInfo��ʹ��callback�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ӧ��Bundle���ơ� |
| bundlePackFlag | BundlePackFlag | 是 | ָʾҪ��ѯ��Ӧ�ð���־�� |
| callback | AsyncCallback&lt;BundlePackInfo&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)�����������óɹ���errΪundefined��<br/>dataΪ��ȡ����BundlePackInfo��Ϣ������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |


## getBundlePackInfo

```TypeScript
function getBundlePackInfo(bundleName: string, bundlePackFlag : BundlePackFlag): Promise<BundlePackInfo>
```

����bundleName��BundlePackFlag����ȡbundlePackInfo��ʹ��Promise�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ӧ�ó���Bundle���ơ� |
| bundlePackFlag | BundlePackFlag | 是 | ָʾҪ��ѯ��Ӧ�ð���־�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;BundlePackInfo&gt; | Promise���󣬷���BundlePackInfo��Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundle name is not found. |


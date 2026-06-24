# getBundleResourceInfo（系统接口）

## getBundleResourceInfo

```TypeScript
function getBundleResourceInfo(bundleName: string, resourceFlags?: number): BundleResourceInfo
```

��ͬ���������ݸ�����bundleName��resourceFlags��ȡ��ǰӦ�õ�BundleResourceInfo��

**起始版本：** 11

**需要权限：** ohos.permission.GET_BUNDLE_RESOURCES

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ָ����ѯӦ�õİ����� |
| resourceFlags | number | 否 | ָ�����ص�BundleResourceInfo����������Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| BundleResourceInfo | ����ָ��Ӧ�õ�BundleResourceInfo�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |


## getBundleResourceInfo

```TypeScript
function getBundleResourceInfo(bundleName: string, resourceFlags?: number, appIndex?: number): BundleResourceInfo
```

��ͬ���������ݸ�����bundleName��resourceFlags��appIndex��ȡ��ǰӦ�û����Ӧ�õ�BundleResourceInfo��

**起始版本：** 12

**需要权限：** ohos.permission.GET_BUNDLE_RESOURCES

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ָ����ѯӦ�õİ����� |
| resourceFlags | number | 否 | ָ�����ص�BundleResourceInfo����������Ϣ�� |
| appIndex | number | 否 | ָ����ѯӦ�÷�����ID��Ĭ��ֵΪ0�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| BundleResourceInfo | ����ָ��Ӧ�õ�BundleResourceInfo�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |
| [17700001](../../errorcode-universal.md#17700001-The) | The specified bundleName is not found. |
| [17700061](../../errorcode-universal.md#17700061-AppIndex) | AppIndex not in valid range or not found. |


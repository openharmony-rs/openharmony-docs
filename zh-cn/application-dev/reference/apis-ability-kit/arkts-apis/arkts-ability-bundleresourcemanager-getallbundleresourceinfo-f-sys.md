# getAllBundleResourceInfo（系统接口）

## getAllBundleResourceInfo

```TypeScript
function getAllBundleResourceInfo(resourceFlags: number, callback: AsyncCallback<Array<BundleResourceInfo>>): void
```

���ݸ�����resourceFlags��ȡ����Ӧ�õ�BundleResourceInfo��ʹ��callback�첽�ص���

**起始版本：** 11

**需要权限：** ohos.permission.GET_INSTALLED_BUNDLE_LIST and ohos.permission.GET_BUNDLE_RESOURCES

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceFlags | number | 是 | ָ�����ص�BundleResourceInfo����������Ϣ�� |
| callback | AsyncCallback&lt;Array&lt;BundleResourceInfo&gt;&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������ȡ�ɹ�ʱ��errΪ<br/>undefined��dataΪ��ȡ����BundleResourceInfo���飻����Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |


## getAllBundleResourceInfo

```TypeScript
function getAllBundleResourceInfo(resourceFlags: number): Promise<Array<BundleResourceInfo>>
```

���ݸ�����resourceFlags��ȡ����Ӧ�õ�BundleResourceInfo��ʹ��Promise�첽�ص���

**起始版本：** 11

**需要权限：** ohos.permission.GET_INSTALLED_BUNDLE_LIST and ohos.permission.GET_BUNDLE_RESOURCES

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceFlags | number | 是 | ָ�����ص�BundleResourceInfo����������Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;BundleResourceInfo&gt;&gt; | Promise���󣬷���BundleResourceInfo���顣 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.<br/>Incorrect parameter types. |


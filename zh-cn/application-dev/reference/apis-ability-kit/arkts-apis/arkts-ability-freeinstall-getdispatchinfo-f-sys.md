# getDispatchInfo（系统接口）

## getDispatchInfo

```TypeScript
function getDispatchInfo(callback: AsyncCallback<DispatchInfo>): void
```

��ȡ�й�dispatch�汾����Ϣ��ʹ��callback�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;DispatchInfo&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)�����������óɹ���errΪundefined��data<br/>Ϊ��ȡ����[DispatchInfo](arkts-ability-dispatchinfo-i-sys.md#DispatchInfo)��Ϣ������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |


## getDispatchInfo

```TypeScript
function getDispatchInfo(): Promise<DispatchInfo>
```

��ȡ�й�dispatch�汾����Ϣ��ʹ��Promise�첽�ص���

**起始版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DispatchInfo&gt; | Promise���󣬷���[DispatchInfo](arkts-ability-dispatchinfo-i-sys.md#DispatchInfo)��Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied, non-system app called system api. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |


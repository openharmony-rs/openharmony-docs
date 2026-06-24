# getBundleInstaller（系统接口）

## getBundleInstaller

```TypeScript
function getBundleInstaller(callback: AsyncCallback<BundleInstaller>): void
```

��ȡBundleInstaller����ʹ��callback�첽�ص���

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;BundleInstaller&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)����ȡBundleInstaller����err<br/>Ϊundefined��dataΪ��ȡ����BundleInstaller���󣻷���Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Incorrect parameter types. |


## getBundleInstaller

```TypeScript
function getBundleInstaller(): Promise<BundleInstaller>
```

��ȡBundleInstaller����ʹ��Promise�첽�ص���

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;BundleInstaller&gt; | BundleInstaller object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |


# BundleInstaller（系统接口）

��ģ���ṩ�豸�ϰ�װ��������ж��Ӧ�õ�������

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [BundleInstaller](arkts-ability-installer-bundleinstaller-i-sys.md#BundleInstaller)

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## install

```TypeScript
install(bundleFilePaths: Array<string>, param: InstallParam, callback: AsyncCallback<InstallStatus>): void
```

��Ӧ���а�װhap��֧�ֶ�hap��װ��ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [install](arkts-ability-installer-bundleinstaller-i-sys.md#install-1)

**需要权限：** ohos.permission.INSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFilePaths | Array&lt;string&gt; | 是 | ָʾ�洢HAP��ɳ��·���� |
| param | InstallParam | 是 | ָ����װ��������������� |
| callback | AsyncCallback&lt;InstallStatus&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������<br/>������Ϊ��εĻص����������ذ�װ״̬��Ϣ�� |

## recover

```TypeScript
recover(bundleName: string, param: InstallParam, callback: AsyncCallback<InstallStatus>): void
```

�ָ�һ��Ӧ�ó���ʹ��callback�첽�ص�����Ԥ��Ӧ�ñ�ж�غ󣬿���ͨ���˽ӿڽ��лָ���

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [recover](arkts-ability-installer-bundleinstaller-i-sys.md#recover-1)

**需要权限：** ohos.permission.INSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ӧ��Bundle���ơ� |
| param | InstallParam | 是 | ָ��Ӧ�ûָ���������������� |
| callback | AsyncCallback&lt;InstallStatus&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������<br/>������Ϊ��εĻص����������ذ�װ״̬��Ϣ�� |

## uninstall

```TypeScript
uninstall(bundleName: string, param: InstallParam, callback: AsyncCallback<InstallStatus>): void
```

ж��Ӧ�ó���ʹ��callback�첽�ص������ذ�װ״̬��Ϣ��

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [uninstall](arkts-ability-installer-bundleinstaller-i-sys.md#uninstall-1)

**需要权限：** ohos.permission.INSTALL_BUNDLE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ӧ��Bundle���ơ� |
| param | InstallParam | 是 | ָ��ж����������������� |
| callback | AsyncCallback&lt;InstallStatus&gt; | 是 | [�ص�����](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-i.md#AsyncCallback)������<br/>������Ϊ��εĻص����������ذ�װ״̬��Ϣ�� |


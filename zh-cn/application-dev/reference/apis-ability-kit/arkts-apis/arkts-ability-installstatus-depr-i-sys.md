# InstallStatus（系统接口）

Ӧ�ó���װж�صĽ����

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## status

```TypeScript
status: bundle.InstallErrorCode
```

��ʾ��װ��ж�ش���״̬�롣ȡֵ��Χ��ö��ֵ[InstallErrorCode](arkts-ability-bundle-installerrorcode-e.md#InstallErrorCode)��

**类型：** bundle.InstallErrorCode

**默认值：** Indicates the install or uninstall error code

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## statusMessage

```TypeScript
statusMessage: string
```

��ʾ��װ��ж�ص��ַ��������Ϣ��ȡֵ��Χ������

"SUCCESS" : ��װ�ɹ���</br> "STATUS_INSTALL_FAILURE": ��װʧ�ܣ������ڰ�װ�ļ�����</br> "STATUS_INSTALL_FAILURE_ABORTED": ��װ��ֹ�� </br>
"STATUS_INSTALL_FAILURE_INVALID": ��װ������Ч�� </br> "STATUS_INSTALL_FAILURE_CONFLICT": ��װ��ͻ������������������Ӧ�û�����Ϣ��һ�£��� </br>
"STATUS_INSTALL_FAILURE_STORAGE": �洢����Ϣʧ�ܡ� </br> "STATUS_INSTALL_FAILURE_INCOMPATIBLE": ��װ�����ݣ������ڰ汾������װ����ǩ����Ϣ���󣩡� <
/br> "STATUS_UNINSTALL_FAILURE": ж��ʧ�ܣ�������ж�ص�Ӧ�ã��� </br> "STATUS_UNINSTALL_FAILURE_ABORTED": ж����ֹ��û��ʹ�ã��� </br> "
STATUS_UNINSTALL_FAILURE_ABORTED": ж�س�ͻ��ж��ϵͳӦ��ʧ�ܣ� ����Ӧ�ý���ʧ�ܣ��� </br> "STATUS_INSTALL_FAILURE_DOWNLOAD_TIMEOUT": ��װʧ�ܣ�
���س�ʱ����</br> "STATUS_INSTALL_FAILURE_DOWNLOAD_FAILED": ��װʧ�ܣ�����ʧ�ܣ��� </br> "STATUS_RECOVER_FAILURE_INVALID": �ָ�Ԥ��Ӧ��ʧ�ܡ�
</br> "STATUS_ABILITY_NOT_FOUND": Abilityδ�ҵ���</br> "STATUS_BMS_SERVICE_ERROR": BMS������� </br> "
STATUS_FAILED_NO_SPACE_LEFT": �豸�ռ䲻�㡣</br> "STATUS_GRANT_REQUEST_PERMISSIONS_FAILED": Ӧ����Ȩʧ�ܡ� </br> "
STATUS_INSTALL_PERMISSION_DENIED": ȱ�ٰ�װȨ�ޡ� </br> "STATUS_UNINSTALL_PERMISSION_DENIED": ȱ��ж��Ȩ�ޡ�

**类型：** string

**默认值：** Indicates the install or uninstall result string message

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。


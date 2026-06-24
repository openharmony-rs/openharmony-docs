# BundleStatusCallback（系统接口）

Ӧ��״̬�����仯ʱ�ص�����Ϣ��
> **˵����**
>
> ��ģ�������ӿڴ�API version 8 ��ʼ֧�֡������汾�������ӿڣ������ϽǱ굥����ǽӿڵ���ʼ�汾��
>
> ��API version 9��ʼ����ģ�鲻��ά������������ӿڡ�
>
> ��ģ��Ϊϵͳ�ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**替代接口：** bundleMonitor/bundleMonitor

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## add

```TypeScript
add: (bundleName: string, userId: number) => void
```

��ȡӦ�ð�װʱ����Ϣ��

**类型：** (bundleName: string, userId: number) => void

**起始版本：** 8

**废弃版本：** 9

**替代接口：** BundleChangedInfo

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## remove

```TypeScript
remove: (bundleName: string, userId: number) => void
```

��ȡӦ��ж��ʱ����Ϣ��

**类型：** (bundleName: string, userId: number) => void

**起始版本：** 8

**废弃版本：** 9

**替代接口：** BundleChangedInfo

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## update

```TypeScript
update: (bundleName: string, userId: number) => void
```

��ȡӦ�ø���ʱ����Ϣ��

**类型：** (bundleName: string, userId: number) => void

**起始版本：** 8

**废弃版本：** 9

**替代接口：** BundleChangedInfo

**需要权限：** ohos.permission.LISTEN_BUNDLE_CHANGE

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。


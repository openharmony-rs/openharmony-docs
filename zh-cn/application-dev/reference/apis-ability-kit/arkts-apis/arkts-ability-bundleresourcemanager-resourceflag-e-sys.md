# ResourceFlag（系统接口）

```TypeScript
enum ResourceFlag
```

��Դ��Ϣ��־��ָʾ��Ҫ��ȡ����Դ��Ϣ�����ݡ�

**起始版本：** 11

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

## GET_RESOURCE_INFO_ALL

```TypeScript
GET_RESOURCE_INFO_ALL = 0x00000001
```

����ͬʱ��ȡicon��label��Ϣ��

**起始版本：** 11

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

## GET_RESOURCE_INFO_WITH_LABEL

```TypeScript
GET_RESOURCE_INFO_WITH_LABEL = 0x00000002
```

���ڻ�ȡ������label��Ϣ��icon��ϢΪ�ա�

**起始版本：** 11

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

## GET_RESOURCE_INFO_WITH_ICON

```TypeScript
GET_RESOURCE_INFO_WITH_ICON = 0x00000004
```

���ڻ�ȡ������icon��Ϣ��label��ϢΪ�ա�

**起始版本：** 11

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

## GET_RESOURCE_INFO_WITH_SORTED_BY_LABEL

```TypeScript
GET_RESOURCE_INFO_WITH_SORTED_BY_LABEL = 0x00000008
```

���ڻ�ȡ����label��������Ϣ�������ܵ���ʹ����Ҫ��GET_RESOURCE_INFO_ALL �� GET_RESOURCE_INFO_WITH_LABELһ��ʹ�á�

**起始版本：** 11

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

## GET_RESOURCE_INFO_WITH_DRAWABLE_DESCRIPTOR

```TypeScript
GET_RESOURCE_INFO_WITH_DRAWABLE_DESCRIPTOR = 0x00000010
```

���ڻ�ȡӦ��ͼ���[drawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-drawabledescriptor.md)����

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。

## GET_RESOURCE_INFO_ONLY_WITH_MAIN_ABILITY

```TypeScript
GET_RESOURCE_INFO_ONLY_WITH_MAIN_ABILITY = 0x00000020
```

���ڻ�ȡ����������չʾͼ���Ability��Դ��������
[getLauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-getlauncherabilityresourceinfo-f-sys.md#getLauncherAbilityResourceInfo-1)
��
[getAllLauncherAbilityResourceInfo](arkts-ability-bundleresourcemanager-getalllauncherabilityresourceinfo-f-sys.md#getAllLauncherAbilityResourceInfo-1)
�ӿ�����Ч��

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Resource

**系统接口：** 此接口为系统接口。


# UninstallComponentType（系统接口）

```TypeScript
export enum UninstallComponentType
```

��ʶж��ʱ����������͡�

**起始版本：** 15

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## EXTENSION

```TypeScript
EXTENSION = 1
```

������չ�������͡���֧��service���͵�[ExtensionAbility](../../../../quick-start/module-configuration-file.md#extensionabilities��ǩ)
��

�������ExtensionAbilityͨ��want��bundleName��moduleName��abilityName�ֶι�ͬȷ����

**起始版本：** 15

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## UI_EXTENSION

```TypeScript
UI_EXTENSION = 2
```

UI��չ�������͡�

�������UIExtensionAbilityͨ��want��bundleName��moduleName��abilityName�ֶι�ͬȷ����ͬʱwant.parameters�е�
ability.want.params.uiExtensionType�ֶ���Ҫ����Ϊ
[UIExtensionAbility](../../../../application-models/uiextensionability-sys.md)�����͡�

**起始版本：** 22

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。


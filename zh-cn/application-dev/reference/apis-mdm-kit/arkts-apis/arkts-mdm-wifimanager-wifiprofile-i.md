# WifiProfile

Wi-Fi������Ϣ��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## bssid

```TypeScript
bssid?: string
```

Wi-Fi�ȵ��MAC��ַ������6���ֽڣ����磺00:11:22:33:44:55����ȡ��ʽ���£�������Ӧ��-���ϵͳѡ��-���������ѡ��-����WLAN��ϸ��־��¼���أ�Ȼ���������Ӧ���е�WLAN�б����鿴��ʾ��MAC��ַ
����һ��Wi-Fi��Ӧ���MAC��ַ������������MAC��ַ��

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## creatorUid

```TypeScript
creatorUid?: number
```

�����û���ID��Ĭ��ֵ-1��

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## disableReason

```TypeScript
disableReason?: number
```

����ԭ��Ĭ��ֵ0��

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## eapProfile

```TypeScript
eapProfile?: WifiEapProfile
```

����չ������֤Э�����á�ֻ��securityTypeΪWIFI_SEC_TYPE_EAPʱ���

**类型：** WifiEapProfile

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## ipType

```TypeScript
ipType?: IpType
```

IP��ַ���ͣ�Ĭ��ֵDHCP��

**类型：** IpType

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## isHiddenSsid

```TypeScript
isHiddenSsid?: boolean
```

�Ƿ����������硣true��ʾ���������磬false��ʾ�����������磬Ĭ��Ϊfalse��

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## netId

```TypeScript
netId?: number
```

���������ID��Ĭ��ֵ-1��

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## preSharedKey

```TypeScript
preSharedKey: string
```

�ȵ����Կ����󳤶�Ϊ64�ֽڡ�

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## randomMacAddr

```TypeScript
randomMacAddr?: string
```

MAC��ַ��randomMacTypeΪ�豸MAC����ʱ�����ֶα��

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## randomMacType

```TypeScript
randomMacType?: number
```

���MAC���͡�0-���MAC��ַ�� 1-�豸MAC��ַ��Ĭ��ֵ0��

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## securityType

```TypeScript
securityType: WifiSecurityType
```

��ȫ���͡�

**类型：** WifiSecurityType

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## ssid

```TypeScript
ssid: string
```

Wi-Fi�ȵ����ƣ���󳤶�Ϊ32�ֽڣ������ʽΪUTF-8��

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## staticIp

```TypeScript
staticIp?: IpProfile
```

��̬IP������Ϣ��ipTypeΪSTATICʱ�����ֶα��

**类型：** IpProfile

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager


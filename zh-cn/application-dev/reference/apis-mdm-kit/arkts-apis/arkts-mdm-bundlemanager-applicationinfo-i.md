# ApplicationInfo

Ӧ�ó�����Ϣ��

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## accessTokenId

```TypeScript
readonly accessTokenId: number
```

Ӧ�ó����accessTokenId��Ӧ�õ����ݱ�ʶ���ڳ�����ʿ���У��ӿ�
[checkAccessToken](../../../../reference/apis-ability-kit/js-apis-abilityAccessCtrl.md#checkaccesstoken9)��ʹ�á�

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appDistributionType

```TypeScript
readonly appDistributionType: string
```

Ӧ�ó���ǩ��֤��ķַ����ͣ���ϸ��Ϣ��ο�[ApplicationInfo](../../apis-ability-kit/arkts-apis/arkts-ability-applicationinfo-i.md#ApplicationInfo)��appProvisionType�ֶΡ�

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appIndex

```TypeScript
readonly appIndex: number
```

Ӧ�ð��ķ���������ʶ�����ڷ���Ӧ������Ч��

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appProvisionType

```TypeScript
readonly appProvisionType: string
```

Ӧ�ó���ǩ��֤���ļ������ͣ���Ϊdebug��release�������͡�

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## codePath

```TypeScript
readonly codePath: string
```

Ӧ�ó���İ�װĿ¼��

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## dataUnclearable

```TypeScript
readonly dataUnclearable: boolean
```

��ʶӦ�������Ƿ�ɱ�ɾ����true��ʾ����ɾ����false��ʾ����ɾ����

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## debug

```TypeScript
readonly debug: boolean
```

��ʶӦ���Ƿ��ڵ���ģʽ��ȡֵΪtrue��ʾӦ�ô��ڵ���ģʽ��ȡֵΪfalse��ʾӦ�ô��ڷǵ���ģʽ��

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## description

```TypeScript
readonly description: string
```

��ʶӦ�õ�������Ϣ����Ӧ[app.json5](../../../../quick-start/app-configuration-file.md)�����õ�description�ֶΡ�����description����ϸ��Ϣ���������
��descriptionResource�ֶ�˵����

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## descriptionId

```TypeScript
readonly descriptionId: number
```

��ʶӦ�õ�������Ϣ����Դid���Ǳ��빹��ʱ����Ӧ�����õ�description�Զ����ɵ���Դid��

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## descriptionResource

```TypeScript
readonly descriptionResource: Resource
```

Ӧ�ó����������Դ��Ϣ�������˸���Դ����Ϣ��bundleName��moduleName��id��

**类型：** Resource

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## enabled

```TypeScript
readonly enabled: boolean
```

�ж�Ӧ�ó����Ƿ����ʹ�ã�ȡֵΪtrue��ʾ����ʹ�ã�ȡֵΪfalse��ʾ����ʹ�á�

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## icon

```TypeScript
readonly icon: string
```

Ӧ�ó����ͼ�꣬��Ӧ[app.json5](../../../../quick-start/app-configuration-file.md)�����õ�icon�ֶΡ�����icon����ϸ��Ϣ��������е�iconResource�ֶ�˵
����

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## iconData

```TypeScript
readonly iconData: string
```

Ӧ�ó����ͼ�꣬Ϊbase64�����ʽ��

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## iconId

```TypeScript
readonly iconId: number
```

Ӧ�ó���ͼ�����Դid���Ǳ��빹��ʱ����Ӧ�����õ�icon�Զ����ɵ���Դid��

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## iconResource

```TypeScript
readonly iconResource: Resource
```

Ӧ�ó����ͼ����Դ��Ϣ�������˸���Դ����Ϣ��bundleName��moduleName��id��

**类型：** Resource

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## installSource

```TypeScript
readonly installSource: string
```

Ӧ�ó���İ�װ��Դ��֧�ֵ�ȡֵ���£�

- pre-installed��ʾӦ��Ϊ��һ�ο���ʱ��װ��Ԥ��Ӧ�á�
- ota��ʾӦ��Ϊϵͳ����ʱ������Ԥ��Ӧ�á�
- recovery��ʾж�غ��ٻָ���Ԥ��Ӧ�á�
- bundleName��ʾӦ���ɴ˰�����Ӧ��Ӧ�ð�װ��
- unknown��ʾӦ�ð�װ��Դδ֪��

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## label

```TypeScript
readonly label: string
```

��ʶӦ�õ����ơ�

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## labelId

```TypeScript
readonly labelId: number
```

��ʶӦ�����Ƶ���Դid���Ǳ��빹��ʱ����Ӧ�����õ�label�Զ����ɵ���Դid��

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## labelResource

```TypeScript
readonly labelResource: Resource
```

Ӧ�ó���ı�ǩ��Դ��Ϣ�������˸���Դ����Ϣ��bundleName��moduleName��id��

**类型：** Resource

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## name

```TypeScript
readonly name: string
```

Ӧ�ð������ƣ���Ӧ[app.json5](../../../../quick-start/app-configuration-file.md)�����õ�bundleName�ֶΡ�

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## nativeLibraryPath

```TypeScript
readonly nativeLibraryPath: string
```

Ӧ�ó���ı��ؿ��ļ�·����

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## process

```TypeScript
readonly process: string
```

Ӧ�ó���Ľ������ơ�

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## releaseType

```TypeScript
readonly releaseType: string
```

��ʶӦ�ô��ʱʹ�õ�SDK�ķ������͡���ǰSDK�ķ������Ϳ���ΪCanary��Beta��Release������Canary��Beta����ͨ����Ž�һ��ϸ�֣�����Canary1��Canary2��Beta1��Beta2�ȡ������߿�ͨ
���Ա�Ӧ�ô��������SDK�������ͺ�OS�ķ������ͣ�[deviceInfo.distributionOSReleaseType](../../apis-basic-service-kit/arkts-apis/arkts-deviceinfo.md#deviceInfo)�����жϼ����ԡ�

**类型：** string

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## removable

```TypeScript
readonly removable: boolean
```

Ӧ�ó����Ƿ���Ա��Ƴ���ȡֵΪtrue��ʾ���Ա��Ƴ���ȡֵΪfalse��ʾ�����Ա��Ƴ���

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## systemApp

```TypeScript
readonly systemApp: boolean
```

��ʶӦ���Ƿ�ΪϵͳӦ�ã�ȡֵΪtrue��ʾϵͳӦ�ã�ȡֵΪfalse��ʾ��ϵͳӦ�á�

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## uid

```TypeScript
readonly uid: number
```

Ӧ�ó����UID��

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager


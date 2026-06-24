# NamedRouterOptions

����·����תѡ�

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

��ʾĿ������·��ҳ���name��

**ϵͳ������** SystemCapability.ArkUI.ArkUI.Full

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## params

```TypeScript
params?: Object
```

��ʾ·����תʱҪͬʱ���ݵ�Ŀ��ҳ������ݡ���ת��Ŀ��ҳ���ʹ��router.getParams()��ȡ���ݵĲ��������⣬����web��ʽ�У�����Ҳ������ҳ����ֱ��ʹ�ã���this.keyValue(keyValueΪ��תʱ
params�����е�keyֵ)�����Ŀ��ҳ�������и��ֶΣ�����ֵ�ᱻ������ֶ�ֵ���ǡ�

**˵����**

params�������ܴ��ݷ�����ϵͳ�ӿڷ��صĶ������磬ý��ӿڶ���ͷ��ص�PixelMap���󣩡����鿪������ȡϵͳ�ӿڷ��صĶ�������Ҫ�����ݵĻ����������ԣ����й���object���Ͷ�����д��ݡ�

**ϵͳ������** SystemCapability.ArkUI.ArkUI.Full

**类型：** Object

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## recoverable

```TypeScript
recoverable?: boolean
```

��ʾ��Ӧ��ҳ���Ƿ�ɻָ���Ĭ��Ϊtrue����Ϊtrueʱ����ʾ�ɻָ�����Ϊfalseʱ����ʾ���ɻָ���

**˵����**

��Ӧ���˵���̨��������δ����ĳ��ʱ��㣬����ϵͳ��Դ���Ƶ�ԭ��ϵͳɱ�������ĳ��ҳ�汻���óɿɻָ�����ô��Ӧ���ٴα�����ǰ̨��ϵͳ���Իָ���ҳ�棬��ϸ˵����ο�
[UIAbility���ݻָ�](../../../../application-models/ability-recover-guideline.md)��

**类型：** boolean

**起始版本：** 14

**系统能力：** SystemCapability.ArkUI.ArkUI.Lite


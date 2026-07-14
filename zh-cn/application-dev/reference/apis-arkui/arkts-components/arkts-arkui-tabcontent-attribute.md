# TabContent属性/事件

��֧��[ͨ������](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)�⣬��֧���������ԣ�

��֧��[ͨ���¼�](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)�⣬��֧�������¼���

**继承/实现关系：** TabContentAttribute extends [CommonMethod<TabContentAttribute>](CommonMethod<TabContentAttribute>)

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillHide

```TypeScript
onWillHide(event: VoidCallback)
```

�߼��ص���TabContent��Ҫ���ص�ʱ�򴥷��ûص�����������TabContent�л���ҳ���л�������ǰ��̨�л���

> **˵����**

> ��API version 20��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)�е��á�

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | VoidCallback | 是 | TabContent��Ҫ���صĻص������� |

## onWillShow

```TypeScript
onWillShow(event: VoidCallback)
```

�߼��ص���TabContent��Ҫ��ʾ��ʱ�򴥷��ûص�����������TabContent�״���ʾ��TabContent�л���ҳ���л�������ǰ��̨�л���

> **˵����**

> ��API version 20��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)�е��á�

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | VoidCallback | 是 | TabContent��Ҫ��ʾ�Ļص������� |

## tabBar

```TypeScript
tabBar(options: string | Resource | CustomBuilder | TabBarOptions)
```

����TabBar����ʾ���ݡ�

���icon����svg��ʽͼԴ����ɾ��svgͼԴ���õĿ�������ֵ������icon��С��ʹ��svgͼԴ���õĿ�������ֵ��

���õ����ݳ���tabBarҳǩʱ���в��С�

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | string \| Resource \| CustomBuilder \| TabBarOptions | 是 | TabBar����ʾ���ݡ�<br/>CustomBuilder��?���������ڲ����Դ��������API version 8�汾�������ã���<br>**起始版本：** 18 |

## tabBar

```TypeScript
tabBar(value: SubTabBarStyle | BottomTabBarStyle)
```

����TabBar����ʾ���ݡ��ײ���ʽû���»���Ч����icon�쳣ʱ��ʾ��ɫͼ�顣

> **˵����**

> - ��ҳǩ��[SubTabBarStyle](arkts-arkui-subtabbarstyle-c.md)����ʽ��ͨ��Ϊ����+�»��ߣ�����+�����ҳǩ������������ı���ʽ����������ڶ������ߵײ�ʹ�á��л�ҳǩʱĬ��֧�ֶ�����תЧ������������Ѷ
> ��Ӧ�õĶ������ࣨ��"��ע����Ƶ������"��������ģ��Ķ�������������
>
> - �ײ�ҳǩ/���ҳǩ��[BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md)����ʽ�����»��ߺͱ���Ч����ҳǩ��ʽͨ��Ϊͼ��+���ֵ���Ϸ�ʽ���л�ҳǩʱĬ���޶�����תЧ�����ײ�ҳǩͨ������Ӧ��
> ������������ҳ�����֡��Ƽ��������ҳǩ�����ڿ���������������vertical(true)�������򲼾֣���ҳǩ�ڲ����ʾ��Ĭ�������ʾ��

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | SubTabBarStyle \| BottomTabBarStyle | 是 | TabBar����ʾ���ݡ�<br/>SubTabBarStyle��?��ҳǩ��ʽ��<br/>BottomTabBarStyle��?�ײ�ҳǩ�Ͳ��ҳǩ��ʽ�� |

## tabBar

```TypeScript
tabBar(content: ComponentContent | SubTabBarStyle | BottomTabBarStyle | string | Resource | CustomBuilder | 
    TabBarOptions)
```

����TabBar����ʾ���ݡ�

ʹ��BottomTabBarStyle��TabBarOptions������Ϊ��β�����icon��icon�쳣ʱ��ʾ��ɫͼ�顣���icon����svg��ʽͼԴ����ɾ��svgͼԴ���õĿ�������ֵ������icon��С��ʹ��svgͼԴ���õĿ�
������ֵ��

���õ����ݳ���TabBarҳǩʱ���в��С�

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent \| SubTabBarStyle \| BottomTabBarStyle \| string \| Resource \| CustomBuilder \| TabBarOptions | 是 | Content displayed on the tab bar.<br>**ComponentContent**: encapsulation of the component content,which can be customized.<br>**SubTabBarStyle**: subtab style.<br>**BottomTabBarStyle**: style of the bottom andside tabs. The bottom style does not have the underline effect.<br>**string**: string type.<br>**Resource**:resource reference for importing strings from system or application resources.<br>**CustomBuilder**: builderthat can take components as arguments.<br>**TabBarOptions**: options for configuring images and text content onthe tabs. |


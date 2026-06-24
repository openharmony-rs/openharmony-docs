# NavigationMode

```TypeScript
declare enum NavigationMode
```

����ҳ��ʾģʽ��Navigation���ڷ�����ʾ״̬ʱ������ҳ��������֮�����ʾ�ָ��ߡ�

> **˵����**
>
> Ϊ�˼򻯱�ʾ�����Խ�`������� - minContentWidth - �ָ��߿��� (1px)`��ΪcalcNavBarWidth��

**��1** navBarWidth����ȡֵ�뿪��������ֵ�Ĺ�ϵ��

| ���������õ�navBarWidthֵ | calcNavBarWidth����ֵ | navBarWidth����ȡֵ |
| --- | --- | --- |
| navBarWidth < minNavBarWidth | NA | minNavBarWidth |
| navBarWidth > maxNavBarWidth | calcNavBarWidth > maxNavBarWidth | maxNavBarWidth |
| navBarWidth > maxNavBarWidth | calcNavBarWidth < minNavBarWidth | minNavBarWidth |
| navBarWidth > maxNavBarWidth | minNavBarWidth �� calcNavBarWidth �� maxNavBarWidth | calcNavBarWidth |
| minNavBarWidth �� navBarWidth �� maxNavBarWidth | calcNavBarWidth �� minNavBarWidth | minNavBarWidth |
| minNavBarWidth �� navBarWidth �� maxNavBarWidth | minNavBarWidth < calcNavBarWidth <= navBarWidth | calcNavBarWidth |
| minNavBarWidth �� navBarWidth �� maxNavBarWidth | calcNavBarWidth > navBarWidth | navBarWidth |

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Stack

```TypeScript
Stack = 0
```

����ҳ��������������ʾ���൱������ҳ�档

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Split

```TypeScript
Split = 1
```

����ҳ����������������ʾ��

**1.** navBarWidth����ȡֵ�뿪��������ֵ�Ĺ�ϵ�μ���1��

**2.** ��С����ߴ�ʱ������С�������ĳߴ���minContentWidth��Ȼ������С����ҳ�ĳߴ���minNavBarWidth����������С������С����������������ʧ������С����ҳ��

**3.** ���õ���ҳΪ�̶��ߴ�ʱ����������С����ߴ磬����ҳ���ѹ����ʾ��

**4.** ��ֻ������navBarWidth���ԣ��򵼺�ҳ����ΪnavBarWidth���ҷָ��߲����϶���

**5.** �ָ��ߵ��������Ҹ�2vp���������4vp���ϡ�

**6.** Splitģʽ�£���������ֻ����һ��ҳ�棬��ҳ�����Ͻǲ�����ʾ���ذ�ť��

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Auto

```TypeScript
Auto = 2
```

API version 9��֮ǰ�汾��Navigation����>=520vpʱ������Splitģʽ��ʾ��Navigation����<520vpʱ������Stackģʽ��ʾ��

��API version 10��ʼ��Navigation����>=600vpʱ������Splitģʽ��ʾ��Navigation����<600vpʱ������Stackģʽ��ʾ��600vp����minNavBarWidth(240vp) +
minContentWidth (360vp)��

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## AUTO_WITH_ASPECT_RATIO

```TypeScript
AUTO_WITH_ASPECT_RATIO = 3
```

Navigation����>=600vp�Ҹ߿���С�ڵ���1.2ʱ������Splitģʽ��ʾ���������Stackģʽ��ʾ��600vp����minNavBarWidth(240vp) + minContentWidth (360vp)��

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full


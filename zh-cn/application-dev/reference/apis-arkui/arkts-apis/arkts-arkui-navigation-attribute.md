# Navigation属性/事件

��֧��[ͨ������](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)�⣬��֧���������ԣ�

**继承/实现关系：** NavigationAttribute extends [CommonMethod<NavigationAttribute>](CommonMethod<NavigationAttribute>)

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backButtonIcon

```TypeScript
backButtonIcon(value: string | PixelMap | Resource | SymbolGlyphModifier)
```

���ñ������з��ؼ�ͼ�ꡣ

> **˵����**
>
> ��֧��ͨ��[SymbolGlyphModifier](SymbolGlyphModifier:SymbolGlyphModifier)�����
> [fontSize](SymbolGlyphAttribute#fontSize)�����޸�ͼ���С��
> [effectStrategy](SymbolGlyphAttribute#effectStrategy)�����޸Ķ�Ч��
> [symbolEffect](SymbolGlyphAttribute#symbolEffect(symbolEffect: SymbolEffect, isActive?: boolean))�����޸Ķ�Ч���͡�

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| PixelMap \| Resource \| SymbolGlyphModifier | 是 | �������з��ؼ�ͼ�ꡣ [since 9 - 11] |

## backButtonIcon

```TypeScript
backButtonIcon(icon: string | PixelMap | Resource | SymbolGlyphModifier, accessibilityText?: ResourceStr)
```

���ñ������з��ؼ�ͼ������ϰ��������ݡ�

> **˵����**
>
> �ýӿڲ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�
>
> ��֧��ͨ��[SymbolGlyphModifier](SymbolGlyphModifier:SymbolGlyphModifier)�����
> [fontSize](SymbolGlyphAttribute#fontSize)�����޸�ͼ���С��
> [effectStrategy](SymbolGlyphAttribute#effectStrategy)�����޸Ķ�Ч��
> [symbolEffect](SymbolGlyphAttribute#symbolEffect(symbolEffect: SymbolEffect, isActive?: boolean))�����޸Ķ�Ч���͡�

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| icon | string \| PixelMap \| Resource \| SymbolGlyphModifier | 是 | �������з��ؼ�ͼ�ꡣ |
| accessibilityText | ResourceStr | 否 | ���ؼ����ϰ��������ݡ�Ĭ��ֵ��ϵͳ����������ʱΪ�����ء���ϵͳ������Ӣ��ʱΪ��back���� |

## configuration

```TypeScript
configuration(config: NavigationConfiguration)
```

���õ������á�

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | NavigationConfiguration | 是 | ��������ѡ� |

## customNavContentTransition

```TypeScript
customNavContentTransition(delegate: (from: NavContentInfo, to: NavContentInfo, operation: NavigationOperation)
    => NavigationAnimatedTransition | undefined)
```

�Զ���ת�������ص���

> **˵����**
>
> ��API version 20��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| delegate | (from: NavContentInfo, to: NavContentInfo, operation: NavigationOperation)<br/>    =&gt; NavigationAnimatedTransition \| undefined | 是 | �Զ���ת�������ص���<br/>from���˳�Destination��ҳ�档<br/>to������Destination��ҳ�档operation��ת�����͡�<br/>��<br/>��NavigationAnimatedTransitionʱ����ʾ�Զ���ת������Э�顣<br/>undefined: ����δ���壬ִ��Ĭ��ת����Ч�� |

## divider

```TypeScript
divider(style: NavigationDividerStyle | null)
```

����Navigation˫��ģʽ�µķָ�����ʽ��

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | NavigationDividerStyle \| null | 是 | ����˫���ָ�����ʽ��<br/>- null�����طָ��ߡ� |

## enableDragBar

```TypeScript
enableDragBar(isEnabled: Optional<boolean>)
```

���Ʒ����������Ƿ���ʾ��ק������������PC/2in1�豸�ϲ���Ч��

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | Optional&lt;boolean&gt; | 是 | �Ƿ�����ק����Ĭ��Ϊ����ק����ʽ��<br/>true������ק����ʽ��false������ק����ʽ��<br/>��������Ƿ�ʱ����false������ |

## enableModeChangeAnimation

```TypeScript
enableModeChangeAnimation(isEnabled: Optional<boolean>)
```

�����Ƿ�����˫���л�ʱ�Ķ�Ч��

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | Optional&lt;boolean&gt; | 是 | �Ƿ�����˫���л���Ч��<br/>true��������˫���л���Ч��false���رյ�˫���л���Ч��<br/>��������Ƿ�ʱ����true������ |

## enableToolBarAdaptation

```TypeScript
enableToolBarAdaptation(enable: Optional<boolean>)
```

�����Ƿ�����Navigation��NavDestination�Ĺ�����[toolbarConfiguration](NavigationAttribute#toolbarConfiguration)����Ӧ�������رմ���
���󣬵ײ�������[toolbarConfiguration](NavigationAttribute#toolbarConfiguration)���������ƶ���ҳ�����ϽǵĲ˵��С��ýӿڲ��������Զ���˵���ʹ�øýӿ����
��[NavigationMenuItem](arkts-arkui-navigation-navigationmenuitem-i.md#NavigationMenuItem)�ӿ�������
[�˵�](NavigationAttribute#menus(value: Array<NavigationMenuItem> | CustomBuilder))��

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | Optional&lt;boolean&gt; | 是 | �Ƿ�����Navigation��NavDestination�Ĺ���������Ӧ������<br/>Ĭ��ֵ��true<br/>true������Navigation��<br/>NavDestination�Ĺ���������Ӧ������<br/>false��������Navigation��NavDestination�Ĺ���������Ӧ������ |

## enableVisibilityLifecycleWithContentCover

```TypeScript
enableVisibilityLifecycleWithContentCover(isEnabled: Optional<boolean>)
```

�����Ƿ�����[NavDestination](arkts-arkui-navdestination.md)ҳ��[onHidden](NavDestinationAttribute#onHidden)��
[onShown](NavDestinationAttribute#onShown)����������ȫģ̬������������

> **˵����**
>
> ��API version 23��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | Optional&lt;boolean&gt; | 是 | �Ƿ�����NavDestinationҳ��onShown��onHidden����������ȫģ̬������������<br/>Ĭ��ֵ��true<br/>true��ȫ<br/>ģ̬����ʱ���ᴥ����ǰNavDestinationҳ���onHidden�������ڣ�ȫģ̬�ر�ʱ�ᴥ����ǰNavDestinationҳ���onShown��������<br/>false��NavDestinationҳ��<br/>onHidden��onShown�������ڲ�����Ϊȫģ̬�����𡢹رն������� |

## hideBackButton

```TypeScript
hideBackButton(value: boolean)
```

�����Ƿ����ر������еķ��ؼ������ؼ�����[titleMode](NavigationAttribute#titleMode)����ΪNavigationTitleMode.Miniʱ����Ч��

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | �Ƿ����ر������еķ��ؼ���<br/>true�����ط��ؼ���<br/>false����ʾ���ؼ���<br/>��������Ƿ�ʱ����false������ |

## hideNavBar

```TypeScript
hideNavBar(value: boolean)
```

�����Ƿ����ص���ҳ������Ϊtrueʱ������Navigation�ĵ���ҳ���������������������͹������������ʱ·��ջ�д���NavDestinationҳ�棬��ֱ����ʾջ��NavDestinationҳ�棬��֮��ʾ�հס�

��API version 9��ʼ��API version 10����˫��ģʽ����Ч����API version 11��ʼ�ڵ�����˫��������Ӧģʽ����Ч��

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | �Ƿ����ص���ҳ��<br/>Ĭ��ֵ��false<br/>true�����ص���ҳ��false����ʾ����ҳ��<br/>��������Ƿ�ʱ����false������ |

## hideTitleBar

```TypeScript
hideTitleBar(value: boolean)
```

�����Ƿ����ر�������

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | �Ƿ����ر�������<br/>Ĭ��ֵ��false<br/>true�����ر�������false����ʾ��������<br/>��������Ƿ�ʱ����false������ |

## hideTitleBar

```TypeScript
hideTitleBar(hide: boolean, animated: boolean)
```

�����Ƿ����ر���������[hideTitleBar](NavigationAttribute#hideTitleBar(value: boolean))��ȣ���������������ʱ�Ƿ�ʹ�ö�����

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hide | boolean | 是 | �Ƿ����ر�������<br/>Ĭ��ֵ��false<br/>true�����ر�������false����ʾ��������<br/>��������Ƿ�ʱ����false������ |
| animated | boolean | 是 | �����Ƿ�ʹ�ö���������������<br/>Ĭ��ֵ��false<br/>true��ʹ�ö�����ʾ���ر�������false����ʹ�ö�����ʾ���ر�������<br/>��������Ƿ�ʱ����<br/>false������ |

## hideToolBar

```TypeScript
hideToolBar(value: boolean)
```

�����Ƿ����ع�������

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | �Ƿ����ع�������<br/>Ĭ��ֵ��false<br/>true�����ع�������false����ʾ��������<br/>��������Ƿ�ʱ����false������ |

## hideToolBar

```TypeScript
hideToolBar(hide: boolean, animated: boolean)
```

�����Ƿ����ع���������[hideToolBar](NavigationAttribute#hideToolBar(value: boolean))��ȣ���������������ʱ�Ƿ�ʹ�ö�����

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hide | boolean | 是 | �Ƿ����ع�������<br/>Ĭ��ֵ��false<br/>true�����ع�������false����ʾ��������<br/>��������Ƿ�ʱ����false������ |
| animated | boolean | 是 | �����Ƿ�ʹ�ö���������������<br/>Ĭ��ֵ��false<br/>true��ʹ�ö�����ʾ���ع�������false����ʹ�ö�����ʾ���ع�������<br/>��������Ƿ�ʱ����<br/>false������ |

## ignoreLayoutSafeArea

```TypeScript
ignoreLayoutSafeArea(types?: Array<LayoutSafeAreaType>, edges?: Array<LayoutSafeAreaEdge>)
```

��������Ĳ��֣�ʹ����չ���ǰ�ȫ����

> **˵����**
>
> - �������ignoreLayoutSafeArea֮����Ч������Ϊ��
> > ����LayoutSafeAreaType.SYSTEMʱ������ı߽���ǰ�ȫ�����غ�ʱ����ܹ����쵽�ǰ�ȫ�����¡�
>
> - �������չ���ǰ�ȫ�����ڣ���ʱ�ڷǰ�ȫ�����ﴥ�����¼������磺����¼����ȿ��ܻᱻϵͳ���أ�������Ӧ״̬����ϵͳ�����
>
> - �����Ҫ��չ���ǰ�ȫ�����ڣ������ػ������ñ������͹�����Ϊ[STACK](arkts-arkui-navigation-barstyle-e.md#BarStyle)ģʽ��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | Array&lt;LayoutSafeAreaType&gt; | 否 | ������չ��ȫ��������͡�<br/>Ĭ��ֵ��<br/>[LayoutSafeAreaType.SYSTEM] |
| edges | Array&lt;LayoutSafeAreaEdge&gt; | 否 | ������չ��ȫ����ķ���<br/>Ĭ��ֵ��<br/><br/>[LayoutSafeAreaEdge.TOP, LayoutSafeAreaEdge.BOTTOM]�� |

## menus

```TypeScript
menus(value: Array<NavigationMenuItem> | CustomBuilder)
```

����ҳ�����Ͻǲ˵���������ʱ����ʾ�˵��ʹ��Array<[NavigationMenuItem](arkts-arkui-navigation-navigationmenuitem-i.md#NavigationMenuItem)&gt; д��ʱ���������֧����ʾ3��ͼ�꣬�������֧����ʾ5��ͼ�꣬�����ͼ��
�ᱻ�����Զ����ɵĸ���ͼ�ꡣ

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;NavigationMenuItem&gt; \| CustomBuilder | 是 |  |

## menus

```TypeScript
menus(items: Array<NavigationMenuItem> | CustomBuilder, options?: NavigationMenuOptions)
```

����ҳ�����Ͻǲ˵���������ʱ����ʾ�˵����[menus](NavigationAttribute#menus(value: Array<NavigationMenuItem> | CustomBuilder))��ȣ�
�����˵�ѡ�ʹ��Array<[NavigationMenuItem](arkts-arkui-navigation-navigationmenuitem-i.md#NavigationMenuItem)&gt; д��ʱ���������֧����ʾ3��ͼ�꣬�������֧����ʾ5��ͼ�꣬�����ͼ��ᱻ�����Զ����ɵĸ���ͼ�ꡣ

> **˵����**
>
> �ýӿڲ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | Array&lt;NavigationMenuItem&gt; \| CustomBuilder | 是 | ҳ�����Ͻǲ˵��� |
| options | NavigationMenuOptions | 否 | ҳ�����Ͻǲ˵�ѡ� |

## minContentWidth

```TypeScript
minContentWidth(value: Dimension)
```

���õ���ҳ��������С���ȣ�˫��ģʽ����Ч����

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Dimension | 是 | ����ҳ��������С���ȡ�<br/>Ĭ��ֵ��360<br/>��λ��vp<br/>undefined����Ϊ��������������ҳ��������С������Ĭ��ֵ����һ�¡�<br/>Autoģʽ��<br/>����㣺Ĭ��600vp��minNavBarWidth(240vp) + minContentWidth (360vp) |

## mode

```TypeScript
mode(value: NavigationMode)
```

���õ���ҳ����ʾģʽ��֧�ֵ�����Stack����������Split��������Ӧ��Auto����

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | NavigationMode | 是 | ����ҳ����ʾģʽ��<br/>Ĭ��ֵ��NavigationMode.Auto<br/>����Ӧ�����������������Ӧ������˫���� |

## navBarPosition

```TypeScript
navBarPosition(value: NavBarPosition)
```

���õ���ҳλ�á�����[mode](NavigationAttribute#mode)����ΪNavigationMode.Auto��NavigationMode.Splitʱ��Ч��

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | NavBarPosition | 是 | ����ҳλ�á�<br/>Ĭ��ֵ��NavBarPosition.Start |

## navBarWidth

```TypeScript
navBarWidth(value: Length)
```

���õ���ҳ���ȡ�����[mode](NavigationAttribute#mode)����ΪNavigationMode.Auto��NavigationMode.Splitʱ��Ч��

��API version 18��ʼ���ò���֧��[!!](../../../../ui/state-management/arkts-new-binding.md)˫��󶨱�����

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Length | 是 | ����ҳ���ȡ�<br/>Ĭ��ֵ��240<br/>��λ��vp<br/>undefined����Ϊ��������������ҳ������Ĭ��ֵ����һ�¡� |

## navBarWidthRange

```TypeScript
navBarWidthRange(value: [Dimension, Dimension])
```

���õ���ҳ��С�������ȣ�˫��ģʽ����Ч����δ���øýӿ�ʱ����С����Ĭ��Ϊ240vp��������Ĭ��Ϊ������ȵ�40%���Ҳ�����432vp��������ҳ��������֮��ķָ��߿����ڴ˷�Χ�ڽ�����ק����ק�ָ���ʹ����ҳ���ȱ仯ʱ������������
�ݻᱻѹ����

�ָ��ߵ���ק��Χ��

| ����| ��ק��Χ |
| ----| ----------- |
|navBarWidthRange��minContentWidthͬʱ���� | ����minContentWidth�����õ�ֵ����navBarWidthRange�����õķ�Χ�ڽ�����ק |
|navBarWidthRange��minContentWidth�������� | ��navBarWidthRangeĬ�ϵ���С�����Χ�ڽ�����ק |
|������navBarWidthRange���� | ��navBarWidthRange�����õķ�Χ�ڽ�����ק�������ק��Χ���ܳ���minContentWidth��Ĭ��ֵ |
|������minContentWidth���� | ��navBarWidthRangeĬ�ϵ���С�����Χ�ڽ�����ק |
|������navBarWidth���� | ��֧����ק |

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Dimension, Dimension] | 是 | ����ҳ��С�������ȡ������쳣ֵʱ��Ĭ��ֵ������ |

## navDestination

```TypeScript
navDestination(builder: (name: string, param: unknown) => void)
```

����NavDestination�����ʹ��builder����������name��param����NavDestination�����builder��ֻ����һ�����ڵ㡣builder��������NavDestination��������һ���Զ�����
���� ���Զ�������������������Ժ��¼����������ʾ�հס�

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | (name: string, param: unknown) =&gt; void | 是 | ����NavDestination�����name��NavDestinationҳ�����ơ�param�����������õ�NavDestinationҳ����ϸ������unknown����<br/>���û��Զ�������͡� |

## onNavBarStateChange

```TypeScript
onNavBarStateChange(callback: (isVisible: boolean) => void)
```

����ҳ��ʾ״̬�л�ʱ�����ûص���

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (isVisible: boolean) =&gt; void | 是 | isVisibleΪtrueʱ��ʾ��ʾ��Ϊfalseʱ��ʾ���ء� [since 10] |

## onNavigationModeChange

```TypeScript
onNavigationModeChange(callback: (mode: NavigationMode) => void)
```

��Navigation�״���ʾ���ߵ�˫��״̬�����仯ʱ�����ûص���

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (mode: NavigationMode) =&gt; void | 是 | NavigationMode.Split����ǰNavigation��ʾΪ˫��;<br/>NavigationMode.Stack����ǰNavigation��ʾΪ������ |

## onTitleModeChange

```TypeScript
onTitleModeChange(callback: (titleMode: NavigationTitleMode) => void)
```

��[titleMode](NavigationAttribute#titleMode)ΪNavigationTitleMode.Freeʱ�����ſɹ�������Ļ���������ģʽ�����仯ʱ�����˻ص���

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (titleMode: NavigationTitleMode) =&gt; void | 是 | ����ģʽ�� [since 10] |

## recoverable

```TypeScript
recoverable(recoverable: Optional<boolean>)
```

����Navigation�Ƿ�ɻָ���������Ϊ�ɻָ�����Ӧ�ý����쳣�˳�������������ʱ�����Զ�������Navigation�����ָ����쳣�˳�ʱ��·��ջ��

> **˵����**
>
> 1. ʹ�øýӿ���Ҫ������Navigation��ͨ������[id](arkts-arkui-commonmethod-c.md#id-1)������ýӿ���Ч��
>
> 2. �ýӿ���Ҫ���NavDestination��[recoverable](NavDestinationAttribute#recoverable)�ӿ�ʹ�á�
>
> 3. �ָ��Ĺ����в������л�����Ϣ�����粻�����л��Ĳ������û����õ�onPop�ȣ��ᱻ�������޷��ָ���
>
> 4. ��Ӧ���˵���̨����ϵͳ��Դ�����ԭ��ϵͳ��ֹ�����ĳҳ��������Ϊ�ɻָ�����Ӧ���ٴα�������ǰ̨ʱ��ϵͳ���Զ��ָ���ҳ�档��ϸ˵����ο�
> [UIAbility���ݻָ�](../../../../application-models/ability-recover-guideline.md)����ϸʹ����ο�
> [ʾ��18](../../../../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#ʾ��18����navigation�ɻָ�)��

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| recoverable | Optional&lt;boolean&gt; | 是 | Navigation�Ƿ�ɻָ���Ĭ��Ϊ���ɻָ���<br/>true��·��ջ�ɻָ���false��·��ջ���ɻָ���<br/>��������Ƿ�ʱ����false������ |

## splitPlaceholder

```TypeScript
splitPlaceholder(placeholder: ComponentContent)
```

Navigation˫��ģʽ�£�֧�������Ҳ�ҳ����ʾĬ��ռλҳ��ռλҳ����ΪUIչʾҳ�����ɻ񽹺���Ӧ�¼���

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| placeholder | ComponentContent | 是 | ����Navigation˫��ģʽ���Ҳ��Ĭ��ռλҳ�� |

## subTitle

```TypeScript
subTitle(value: string)
```

����ҳ�渱���⡣

> **˵����**

**起始版本：** 8

**废弃版本：** 9

**替代接口：** title

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | ҳ�渱���⡣ |

## systemBarStyle

```TypeScript
systemBarStyle(style: Optional<SystemBarStyle>)
```

��Navigation����ʾNavigation��ҳʱ�����ö�Ӧϵͳ״̬������ʽ��

> **˵����**
>
> 1. ��������ʹ��systemBarStyle���Ժ�window����״̬����ʽ����ؽӿڣ����磺
> [setWindowSystemBarProperties](../../../../reference/apis-arkui/arkts-apis-window-Window.md#setwindowsystembarproperties9)��
>
>
> 2. ��������Navigation/NavDestination��systemBarStyle����ʱ���ᱸ�ݵ�ǰ״̬����ʽ���ں����Ļָ�������
>
> 3. Navigation��������ҳ��·��ջ��û��NavDestinationʱ������ջ��NavDestination���õ�״̬����ʽΪ׼��
>
> 4. Navigation��ҳ�����κ�ջ��NavDestinationҳ�棬�����������Ч��systemBarStyle�����ʹ�����õ���ʽ����֮���֮ǰ�Ѿ���������ʽ����ʹ�ñ��ݵ���ʽ���������κδ�����
>
> 5. [Split](arkts-arkui-navigation-navigationmode-e.md#NavigationMode)ģʽ�µ�Navigation�����������û��NavDestination�������Navigation��ҳ�����ã���֮�����ջ��NavDestination�����á�
>
>
> 6. ��֧���������ڵ���ҳ����ʹ��systemBarStyle����״̬����ʽ��
>
> 7. ����Navigationռ������ҳ��ʱ�����õ���ʽ�Ż���Ч����Navigationû��ռ������ҳ��ʱ������б��ݵ���ʽ����ָ����ݵ���ʽ��
>
> 8. ��ҳ�����ò�ͬ��ʽʱ����ҳ��ת����ʼʱ��Ч��
>
> 9. ��ȫ�������£�Navigation/NavDestination���õ�״̬������Ч��
>
> ��API version 20��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | Optional&lt;SystemBarStyle&gt; | 是 | ϵͳ״̬����ʽ�� |

## title

```TypeScript
title(value: ResourceStr | CustomBuilder | NavigationCommonTitle | NavigationCustomTitle, options?: NavigationTitleOptions)
```

����ҳ����⡣

> **˵����**
>
> ��API version 12��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ResourceStr \| CustomBuilder \| NavigationCommonTitle \| NavigationCustomTitle | 是 | ҳ����⣬ʹ��<br/>NavigationCustomTitle��������height�߶�ʱ��[titleMode](NavigationAttribute#titleMode)���Բ�����Ч��<br/>�ַ�������ʱ����������ø����⣬<br/>����С�ٻ��У�2�У����ضϡ�������ø����⣬����С���ضϡ� [since 10] |
| options | NavigationTitleOptions | 否 | ������ѡ� ����������������ɫ������������ģ����ʽ��ģ��ѡ��������������ԡ����������ַ�ʽ����������ʼ���ڼ�ࡢ�������������ڼ�ࡢ��<br/>���������޸������ӱ��������޸������Ƿ���Ӧ��̬ͣ�� [since 11] |

## titleMode

```TypeScript
titleMode(value: NavigationTitleMode)
```

����ҳ���������ʾģʽ��

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | NavigationTitleMode | 是 | ҳ���������ʾģʽ��<br/>Ĭ��ֵ��NavigationTitleMode.Free |

## toolBar

```TypeScript
toolBar(value: object | CustomBuilder)
```

���ù��������ݡ�������ʱ����ʾ��������items���ֵײ�����������ÿ�����������������ı���ͼ�꣬�ı�����ʱ������С����С֮���У����ضϡ�

**object����˵����**

| ���� | ���� | ���� | ˵�� |
| ------ | ------------- | ---- | --------------- |
| value | string | �� | ����������ѡ�����ʾ�ı��� |
| icon | string | �� | ����������ѡ���ͼ����Դ·���� |
| action | () =&gt; void | �� | ��ǰѡ�ѡ�е��¼��ص��� |

**起始版本：** 8

**废弃版本：** 10

**替代接口：** toolbarConfiguration

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | object \| CustomBuilder | 是 | ���������ݡ� |

## toolbarConfiguration

```TypeScript
toolbarConfiguration(value: Array<ToolbarItem> | CustomBuilder, options?: NavigationToolbarOptions)
```

���ù��������ݡ�������ʱ����ʾ��������

> **˵����**
>
> ��API version 20��ʼ���ýӿ�֧����[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier-1)�е��á�

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;ToolbarItem&gt; \| CustomBuilder | 是 | ���������ݣ�ʹ��Array���õĹ��������������ԣ�����������ѡ����ֵײ�����������ÿ�����������������ı���ͼ�ꡣ<br/>����ģʽ���֧����ʾ5��ͼ�꣬�����ͼ��ᱻ�����Զ����ɵĸ���ͼ�ꡣ����ģʽʱ�����Ϊ<br/>[Split](arkts-arkui-navigation-navigationmode-e.md#NavigationMode)ģʽ���԰�������ģʽ��ʾ�����Ϊ[Stack](arkts-arkui-navigation-navigationmode-e.md#NavigationMode)ģʽ�����menus���Ե�Arrayʹ�ã��ײ����������Զ����أ�ͬʱ�ײ�����������ѡ���ƶ���ҳ�����Ͻǲ˵���<br/>ʹ��<br/>[CustomBuilder](../../../../reference/apis-arkui/arkui-ts/ts-types.md#custombuilder8)д��Ϊ�û��Զ��幤����ѡ����߱����Ϲ��ܡ� |
| options | NavigationToolbarOptions | 否 | ������ѡ� ����������������ɫ������������ģ����ʽ��ģ��ѡ��������������ԡ����������ַ�ʽ���Ƿ����ع��������ı�������������ͼ���<br/>�˵�ѡ� [since 11] |


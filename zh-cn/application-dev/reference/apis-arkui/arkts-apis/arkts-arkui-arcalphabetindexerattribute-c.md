# ArcAlphabetIndexerAttribute

��֧��[ͨ������](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)�⣬��֧���������ԣ�

��֧��[ͨ���¼�](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)�⣬��֧�������¼���

**继承/实现关系：** ArcAlphabetIndexerAttribute extends [CommonMethod<ArcAlphabetIndexerAttribute>](CommonMethod<ArcAlphabetIndexerAttribute>)

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## autoCollapse

```TypeScript
autoCollapse(enable: Optional<boolean>): ArcAlphabetIndexerAttribute
```

�����Ƿ�ʹ������Ӧ�۵�ģʽ��

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | Optional&lt;boolean&gt; | 是 | �Ƿ�ʹ������Ӧ�۵�ģʽ��<br/>Ĭ��ֵ��true<br/>true��ʹ������Ӧ�۵�ģʽ��<br/>false����ʹ������Ӧ�۵�ģʽ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## color

```TypeScript
color(color: Optional<ColorMetrics>): ArcAlphabetIndexerAttribute
```

������ͨ״̬��������������ɫ��

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Optional&lt;ColorMetrics&gt; | 是 | ������ɫ��<br/>Ĭ��ֵ��0xFFFFFF����ʾΪ��ɫ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## font

```TypeScript
font(font: Optional<Font>): ArcAlphabetIndexerAttribute
```

������ĸ������Ĭ��������ʽ��

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| font | Optional&lt;Font&gt; | 是 | ��ĸ������Ĭ��������ʽ��<br/>Ĭ��ֵ��<br/>{<br/>size:'13.0fp',<br/>style:FontStyle.Normal,<br/><br/>weight:500,<br/>family:'HarmonyOS Sans'<br/>} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## itemSize

```TypeScript
itemSize(size: Optional<LengthMetrics>): ArcAlphabetIndexerAttribute
```

������ĸ��������ĸ�����С��

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | Optional&lt;LengthMetrics&gt; | 是 | ��ĸ��������ĸ�����С����ĸ����ΪԲ�Σ���Բ��ֱ������֧������Ϊ�ٷֱȡ�<br/>Ĭ��ֵ��24.0<br/>��λ��vp |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## onSelect

```TypeScript
onSelect(handler: Optional<OnSelectCallback>): ArcAlphabetIndexerAttribute
```

������ѡ�лص�������ֵΪ��ǰѡ��������

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | Optional&lt;OnSelectCallback&gt; | 是 | �ص��������͡� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## popupBackground

```TypeScript
popupBackground(color: Optional<ColorMetrics>): ArcAlphabetIndexerAttribute
```

������ʾ��������ɫ��

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Optional&lt;ColorMetrics&gt; | 是 | ��ʾ��������ɫ��<br/>Ĭ��ֵ��0xD8404040����ʾΪ΢͸�������ɫ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## popupBackgroundBlurStyle

```TypeScript
popupBackgroundBlurStyle(style: Optional<BlurStyle>): ArcAlphabetIndexerAttribute
```

������ʾ�����ı���ģ�����ʡ�δͨ���ýӿ�����ʱ��Ĭ��Ϊ�ر�ģ������ӦȡֵΪBlurStyle�е�NONE��

> **˵����**

> ��ͨ��popupBackgroundBlurStyle���õ������ݵı���ģ������ʱ����������ͨ��
> [popupBackground](arkts-arkui-arcalphabetindexerattribute-c.md#popupBackground-1)���ñ���ɫ��

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | Optional&lt;BlurStyle&gt; | 是 | ������ʾ�����ı���ģ�����ʡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## popupColor

```TypeScript
popupColor(color: Optional<ColorMetrics>): ArcAlphabetIndexerAttribute
```

������ʾ����������ɫ��

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Optional&lt;ColorMetrics&gt; | 是 | ��ʾ����������ɫ��<br/>Ĭ��ֵ��0xFFFFFF����ʾΪ��ɫ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## popupFont

```TypeScript
popupFont(font: Optional<Font>): ArcAlphabetIndexerAttribute
```

������ʾ����������ʽ��

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| font | Optional&lt;Font&gt; | 是 | ��ʾ����������ʽ��<br/>Ĭ��ֵ��<br/>{<br/>size:'19.0fp',<br/>style:FontStyle.Normal,<br/><br/>weight:500,<br/>family:'HarmonyOS Sans'<br/>} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## selected

```TypeScript
selected(index: Optional<number>): ArcAlphabetIndexerAttribute
```

����ѡ��������ֵ��

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | Optional&lt;number&gt; | 是 | ѡ��������ֵ��<br/>Ĭ��ֵ��0<br/>�ò���֧��<br/>[!!](../../../../ui/state-management/arkts-new-binding.md)˫��󶨱����� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(color: Optional<ColorMetrics>): ArcAlphabetIndexerAttribute
```

����ѡ�������ɫ��

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Optional&lt;ColorMetrics&gt; | 是 | ѡ�������ɫ��<br/>Ĭ��ֵ��0x1F71FF����ʾΪ����ɫ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## selectedColor

```TypeScript
selectedColor(color: Optional<ColorMetrics>): ArcAlphabetIndexerAttribute
```

����ѡ����������ɫ��

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Optional&lt;ColorMetrics&gt; | 是 | ѡ����������ɫ��<br/>Ĭ��ֵ��0xFFFFFF����ʾΪ��ɫ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## selectedFont

```TypeScript
selectedFont(font: Optional<Font>): ArcAlphabetIndexerAttribute
```

����ѡ�������ֳߴ硢��ϸ�������塢��б����ʽ��

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| font | Optional&lt;Font&gt; | 是 | ѡ����������ʽ��<br/>Ĭ��ֵ��{<br/>size:'13.0fp',<br/>style:FontStyle.Normal,<br/>weight:500<br/>,<br/>family:'HarmonyOS Sans'<br/>} |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |

## usePopup

```TypeScript
usePopup(enabled: Optional<boolean>): ArcAlphabetIndexerAttribute
```

�����Ƿ�ʹ����ʾ������

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | Optional&lt;boolean&gt; | 是 | �Ƿ�ʹ����ʾ������<br/>true��ʾʹ����ʾ������false��ʾ��ʹ����ʾ������<br/>Ĭ��ֵ��false |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArcAlphabetIndexerAttribute | @syscap SystemCapability.ArkUI.ArkUI.Circle<br/>@crossplatform<br/>@atomicservice |


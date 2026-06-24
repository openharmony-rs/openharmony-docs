# TabsController

Tabs����Ŀ����������ڿ���Tabs�������ҳǩ�л�����֧��һ��TabsController���ƶ��Tabs�����

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## changeIndex

```TypeScript
changeIndex(value: number): void
```

����Tabs�л���ָ��ҳǩ��

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | ҳǩ��Tabs�������ֵ������ֵ��0��ʼ��<br/>**˵����**<br/>����С��0��������������ֵʱ��ȡĬ��ֵ0�� |

## constructor

```TypeScript
constructor()
```

TabsController�Ĺ��캯����

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## preloadItems

```TypeScript
preloadItems(indices: Optional<Array<number>>): Promise<void>
```

����TabsԤ����ָ���ӽڵ㡣���øýӿں��һ���Լ�������ָ�����ӽڵ㣬���Ϊ�����ܿ��ǣ�������������ӽڵ㡣

> **˵����**

> - Tabs��preloadItems��Ҫ��Tabs����֮��ȥ���ã��״�Ԥ�����Ƽ���Tabs��[onAppear](arkts-arkui-commonmethod-c.md#onAppear-1)����������ȥ���ơ�
>
> - ���TabsController����δ���κ�Tabs�����ֱ�ӵ��øýӿڣ����׳�JS�쳣�����ʹ�øýӿ�ʱ������ͨ��try-catch�����쳣��
>
> - ʹ��preloadItemsԤ���ر�ǩҳʱ�������Զ���TabBar�ϵ���ʾ���ݣ��Ƽ�ʹ��ComponentContentʵ�֣�ʹ��ʾ����ο�
> [ʾ��9](../../../../reference/apis-arkui/arkui-ts/ts-container-tabcontent.md#ʾ��9ͨ��componentcontent����tabbar)��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| indices | Optional&lt;Array&lt;number&gt;&gt; | 是 | ��Ԥ���ص��ӽڵ���±����顣<br/>Ĭ��ֵ�������顣 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Ԥ������ɺ󴥷��Ļص��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter invalid. Possible causes:<br/><br/>1. The parameter type is not Array.<br/><br/>2. The parameter is an empty array.<br/><br/>3. The parameter contains an invalid index. |

## setTabBarOpacity

```TypeScript
setTabBarOpacity(opacity: number): void
```

����TabBar�Ĳ�͸���ȡ�

> **˵����**

> ��ʹ��
> [bindTabsToScrollable](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#bindtabstoscrollable13)��
> [bindTabsToNestedScrollable](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#bindtabstonestedscrollable13)
> �Ƚӿڰ���Tabs����Ϳɹ�������������ڻ����ɹ����������ʱ���ᴥ����������󶨵�Tabs�����TabBar����ʾ�����ض�Ч������setTabBarOpacity�ӿ����õ�TabBar��͸���Ȼ�ʧЧ����˲�����ͬʱʹ��
> bindTabsToScrollable��bindTabsToNestedScrollable��setTabBarOpacity�ӿڡ�

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| opacity | number | 是 | ����TabBar�Ĳ�͸���ȣ�ȡֵ��ΧΪ[0.0, 1.0]�����õ�ֵС��0.0ʱ����0.0���������õ�ֵ����1.0ʱ����1.0������<br/>Ĭ��ֵ��1.0�� |

## setTabBarTranslate

```TypeScript
setTabBarTranslate(translate: TranslateOptions): void
```

����TabBar��ƽ�ƾ��롣

> **˵����**

> ��ʹ��
> [bindTabsToScrollable](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#bindtabstoscrollable13)��
> [bindTabsToNestedScrollable](../../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#bindtabstonestedscrollable13)
> �Ƚӿڰ���Tabs����Ϳɹ�������������ڻ����ɹ����������ʱ���ᴥ����������󶨵�Tabs�����TabBar����ʾ�����ض�Ч������setTabBarTranslate�ӿ����õ�TabBarƽ�ƾ����ʧЧ����˲�����ͬʱʹ
> ��bindTabsToScrollable��bindTabsToNestedScrollable��setTabBarTranslate�ӿڡ�

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| translate | TranslateOptions | 是 | ����TabBar��ƽ�ƾ��롣 |


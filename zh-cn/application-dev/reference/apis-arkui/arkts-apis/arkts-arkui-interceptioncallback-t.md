# InterceptionCallback

```TypeScript
declare type InterceptionCallback = (from: NavPathInfo|NavBar, to: NavPathInfo|NavBar, pathStack: NavPathStack, operation: NavigationOperation, isAnimated: boolean) => void
```

Navigationҳ����תǰ�����ػص���

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| from | NavPathInfo \| NavBar | 是 | �˳�ҳ����Ϣ������ֵΪnavBar�����ʾ��תǰ��ҳ��ΪNavigation��ҳ�� |
| to | NavPathInfo \| NavBar | 是 | ����ҳ����Ϣ������ֵΪnavBar�����ʾ��ת��Ŀ��ҳ��ΪNavigation��ҳ�� |
| pathStack | NavPathStack | 是 | ҳ��ջ�� |
| operation | NavigationOperation | 是 | ��ǰҳ����ת���͡� |
| isAnimated | boolean | 是 | ҳ����ת�Ƿ��ж�����<br/>true��ҳ����ת�ж�����<br/>false��ҳ����תû�ж����� |


# mutableBuilder

## mutableBuilder

```TypeScript
declare function mutableBuilder<Args extends Object[]>(builder: BuilderCallback): MutableBuilder<Args>
```

定义mutableBuilder函数。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare function mutableBuilder<Args extends Object[]>(builder: BuilderCallback): MutableBuilder<Args>--><!--Device-unnamed-declare function mutableBuilder<Args extends Object[]>(builder: BuilderCallback): MutableBuilder<Args>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | [BuilderCallback](arkts-arkui-buildercallback-t.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MutableBuilder](arkts-arkui-mutablebuilder-c.md)&lt;Args&gt; | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |


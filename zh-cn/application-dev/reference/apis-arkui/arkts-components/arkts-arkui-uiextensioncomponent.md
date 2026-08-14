# UIExtensionComponent

**UIExtensionComponent**用于将其他应用提供的UI嵌入到本应用UI中。嵌入内容运行在另一个进程中，本应用不参与其布局和渲染。 通常用于需要进程隔离的模块化开发场景。

## 约束 该组件不支持预览。 待启动的能力必须是UIExtensionAbility，即带UI的扩展能力。关于如何实现UIExtensionAbility的详细信息，请参见[@ohos.app.ability.UIExtensionAbility（带UI的ExtensionAbility基类）](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md#UIExtensionAbility)。 组件的宽高必须显式设置为非零有效值。 不支持到达边缘后继续滚动的场景。当**UIExtensionComponent**宿主和UIExtensionAbility都支持内容滚动时，基于手势的滚动会导致**UIExtensionComponent**内外同时响应，包括但不限于Scroll、Swiper、List、Grid等可滚动容器。关于如何避免**UIExtensionComponent**内外同时滚动的详细信息，请参见[示例2](../../../reference/apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#example-2-isolating-scrolling-inside-and-outside-of-uiextensioncomponent)。 ###### 子组件 不支持

## UIExtensionComponent

```TypeScript
UIExtensionComponent(
    want: import('../api/@ohos.app.ability.Want').default,
    options?: UIExtensionOptions
  )
```

构造UIExtensionComponent。&lt;br/&gt; 在使用UIExtensionComponent时调用。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIExtensionComponentInterface-(    want: import('../api/@ohos.app.ability.Want').default,    options?: UIExtensionOptions  ): UIExtensionComponentAttribute--><!--Device-UIExtensionComponentInterface-(    want: import('../api/@ohos.app.ability.Want').default,    options?: UIExtensionOptions  ): UIExtensionComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | import('../api/@ohos.app.ability.Want').default | 是 | 表示UIExtensionAbility的want |
| options | [UIExtensionOptions](arkts-arkui-uiextensionoptions-i-sys.md) | 否 | UIExtensionComponentAttribute的构造配置 |

## 汇总

- [TerminationInfo](arkts-arkui-terminationinfo-i-sys.md)
- [UIExtensionOptions](arkts-arkui-uiextensionoptions-i-sys.md)
- [UIExtensionProxy](arkts-arkui-uiextensionproxy-i-sys.md)
- [ReceiveCallback](arkts-arkui-receivecallback-t-sys.md)
- [DpiFollowStrategy](arkts-arkui-dpifollowstrategy-e-sys.md)
- [WindowModeFollowStrategy](arkts-arkui-windowmodefollowstrategy-e-sys.md)

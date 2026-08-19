# UIExtensionComponent

**UIExtensionComponent**用于将其他应用提供的UI嵌入到本应用UI中。嵌入内容运行在另一个进程中，本应用不参与其布局和渲染。 通常用于需要进程隔离的模块化开发场景。

## 约束 该组件不支持预览。 待启动的能力必须是UIExtensionAbility，即带UI的扩展能力。关于如何实现UIExtensionAbility的详细信息，请参见[@ohos.app.ability.UIExtensionAbility（带UI的ExtensionAbility基类）](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)。 组件的宽高必须显式设置为非零有效值。 不支持到达边缘后继续滚动的场景。当**UIExtensionComponent**宿主和UIExtensionAbility都支持内容滚动时，基于手势的滚动会导致**UIExtensionComponent**内外同时响应，包括但不限于Scroll、Swiper、List、Grid等可滚动容器。关于如何避免**UIExtensionComponent**内外同时滚动的详细信息，请参见[示例2](../../../reference/apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#example-2-isolating-scrolling-inside-and-outside-of-uiextensioncomponent)。 ###### 子组件 不支持

## UIExtensionComponent

```TypeScript
UIExtensionComponent(
    want: import('../api/@ohos.app.ability.Want').default,
    options?: UIExtensionOptions
  )
```

构造UIExtensionComponent。<br/> 在使用UIExtensionComponent时调用。

**起始版本：** 10

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

### 接口

| 名称 | 说明 |
| --- | --- |
| [TerminationInfo](arkts-arkui-terminationinfo-i-sys.md) | 用于表示被拉起的UIExtensionAbility通过调用terminateSelfWithResult或者terminateSelf正常退出时的返回结果。 |
| [UIExtensionOptions](arkts-arkui-uiextensionoptions-i-sys.md) | 该接口用于在构造时设置UIExtensionComponentAttribute的选项。 |
| [UIExtensionProxy](arkts-arkui-uiextensionproxy-i-sys.md) | 该接口用于向UIExtensionAbility发送数据。<br/> 当UIExtensionAbility连接成功时，<br/> 它从UIExtensionComponent的onRemoteReady回调中返回。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ReceiveCallback](arkts-arkui-receivecallback-t-sys.md) | 回调函数，用于封装被拉起的Ability发送的数据。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DpiFollowStrategy](arkts-arkui-dpifollowstrategy-e-sys.md) | 表示不同类型的DpiFollowStrategy的枚举。 |
| [WindowModeFollowStrategy](arkts-arkui-windowmodefollowstrategy-e-sys.md) | 表示不同类型的WindowModeFollowStrategy的枚举。 |


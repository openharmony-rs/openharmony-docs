# UIExtensionComponent(System API) (System API)

**UIExtensionComponent**用于将其他应用提供的UI嵌入到本应用UI中。嵌入内容运行在另一个进程中，本应用不参与其布局和渲染。

通常用于需要进程隔离的模块化开发场景。

## 约束

该组件不支持预览。

待启动的能力必须是UIExtensionAbility，即带UI的扩展能力。关于如何实现UIExtensionAbility的详细信息，请参见[@ohos.app.ability.UIExtensionAbility（带UI的ExtensionAbility基类）](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)。

组件的宽高必须显式设置为非零有效值。

不支持到达边缘后继续滚动的场景。当**UIExtensionComponent**宿主和UIExtensionAbility都支持内容滚动时，基于手势的滚动会导致**UIExtensionComponent**内外同时响应，包括但不限于Scroll、Swiper、List、Grid等可滚动容器。关于如何避免**UIExtensionComponent**内外同时滚动的详细信息，请参见[示例2](../../../reference/apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#example-2-isolating-scrolling-inside-and-outside-of-uiextensioncomponent)。

## 子组件

不支持

## UIExtensionComponent

```TypeScript
UIExtensionComponent(
    want: import('../api/@ohos.app.ability.Want').default,
    options?: UIExtensionOptions
  )
```

构造UIExtensionComponent。<br>在使用UIExtensionComponent时调用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

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
| [TerminationInfo](arkts-arkui-terminationinfo-i-sys.md) | 用于表示被拉起的UIExtensionAbility通过调用`terminateSelfWithResult`或者`terminateSelf`正常退出时的返回结果。 |
| [UIExtensionOptions](arkts-arkui-uiextensionoptions-i-sys.md) | 用于在UIExtensionComponent进行构造时传递可选的构造参数。 |
| [UIExtensionProxy](arkts-arkui-uiextensionproxy-i-sys.md) | 用于在双方建立连接成功后，组件使用方将数据发送给被拉起的Ability，并订阅和取消订阅扩展Ability的注册事件。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ReceiveCallback](arkts-arkui-receivecallback-t-sys.md) | 回调函数，用于封装被拉起的Ability发送的数据。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DpiFollowStrategy](arkts-arkui-dpifollowstrategy-e-sys.md) | 表示不同类型的DpiFollowStrategy的枚举。 |
| [WindowModeFollowStrategy](arkts-arkui-windowmodefollowstrategy-e-sys.md) | 窗口Mode跟随策略，用于设置窗口Mode，使其能够跟随宿主或UIExtensionAbility。 |

## 示例

```TypeScript
### 示例1 (加载UIExtension)

UIExtensionComponent组件使用分为使用方和提供方。本示例仅展示组件使用的方法和扩展的Ability，实际运行需在设备中安装bundleName为"com.example.newdemo"，abilityName为"UIExtensionProvider"的Ability扩展。

组件使用方

使用方入口界面Index.ets内容如下：
```

```TypeScript
组件提供方

提供方包含三个文件需要修改：

提供方新增扩展入口文件/src/main/ets/uiextensionability/UIExtensionProvider.ets
```

```TypeScript
提供方扩展Ability入口页面文件/src/main/ets/pages/extension.ets
```

```TypeScript
提供方扩展Ability，module配置文件/src/main/module.json5添加对应配置
```

```TypeScript
### 示例2 (UIExtensionComponent内外部同时响应滚动时隔离处理)

本示例展示了当UIExtensionComponent组件使用方和扩展的Ability同时使用[Scroll](ts-container-scroll.md)容器的场景，通过对UIExtensionComponent设置手势拦截处理，实现当UIExtensionComponent内部滚动时，外部组件不响应滚动。

手势使用方式：

组件内部滚动：手指在组件内部进行滚动操作；

组件外部滚动：拖动外部滚动条进行滚动。

实际运行时需先在设备中安装bundleName为"com.example.newdemo"，abilityName为"UIExtensionProvider"的Ability扩展。

提供方扩展入口文件UIExtensionProvider.ets与[示例1](#示例1-加载uiextension)扩展入口文件UIExtensionProvider.ets代码一致。

提供方扩展Ability的module配置文件与[示例1](#示例1-加载uiextension)扩展module配置文件module.json5代码一致。

使用方组件使用示例：
```

```TypeScript
提供方扩展Ability入口页面文件extension.ets
```

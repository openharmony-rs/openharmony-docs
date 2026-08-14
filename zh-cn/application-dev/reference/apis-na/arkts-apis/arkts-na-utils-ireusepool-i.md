# IReusePool

`IReusePool` 接口提供自定义组件上的全局复用池的相关功能。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare interface IReusePool--><!--Device-unnamed-export declare interface IReusePool-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getReusableInfo

```TypeScript
getReusableInfo(componentConstructor : Class, 
    reuseId?: string): IReusableInfo[] | IReusableInfo | undefined
```

检索此复用池中给定可复用组件类型的回收实例信息。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IReusePool-getReusableInfo(componentConstructor : Class,     reuseId?: string): IReusableInfo[] | IReusableInfo | undefined--><!--Device-IReusePool-getReusableInfo(componentConstructor : Class,     reuseId?: string): IReusableInfo[] | IReusableInfo | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| componentConstructor | Class | 是 | 要查询的可复用自定义组件的类型。 |
| reuseId | string | 否 | 可选的reuseId用于过滤结果。如果指定，则仅返回此特定reuseId复用池的信息。默认值是undefined，返回所有reuseId复用池信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [IReusableInfo](arkts-na-utils-ireusableinfo-i.md)[] | undefined if this pool does not accepts given Component. returns IReusableInfo if this pool accepts given Component/V2, reuseId was not used to recycle instances returns IReusableInfo[] if this pool accepts given Component/V2, reuseId was used to recycle instances. |

## preRender

```TypeScript
preRender(builder: WrappedBuilder<CustomBuilder>, times: int): Promise<void>
```

预创建@Reusable/@ReusableV2组件并将它们放入此复用池中。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IReusePool-preRender(builder: WrappedBuilder<CustomBuilder>, times: int): Promise<void>--><!--Device-IReusePool-preRender(builder: WrappedBuilder<CustomBuilder>, times: int): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | WrappedBuilder&lt;CustomBuilder&gt; | 是 | 包含要执行`times`次的@Builder函数的 `WrappedBuilder`。每次执行应创建一个或多个@Reusable /@ReusableV2组件。 |
| times | int | 是 | 执行@Builder函数的次数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 当空闲任务成功完成时解析的Promise。Promise对象无返回结果。 |


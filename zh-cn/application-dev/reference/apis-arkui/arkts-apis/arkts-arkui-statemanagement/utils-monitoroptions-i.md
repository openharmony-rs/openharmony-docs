# MonitorOptions

设置监听的行为。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface MonitorOptions--><!--Device-unnamed-export declare interface MonitorOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isSynchronous

```TypeScript
isSynchronous?: boolean
```

指定函数是否同步执行，\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_为同步，\_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_为异步。默认为\_\_\_INLINE\_CODE\_DESC\_USD\_2\_\_\_。

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MonitorOptions-isSynchronous?: boolean--><!--Device-MonitorOptions-isSynchronous?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## owner

```TypeScript
owner?: IVariableOwner
```

指定冻结的组件，仅能传入@ComponentV2装饰的自定义组件，默认值为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。

**类型：** IVariableOwner

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MonitorOptions-owner?: IVariableOwner--><!--Device-MonitorOptions-owner?: IVariableOwner-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## path

```TypeScript
path?: string | string[]
```

显式指定监听状态变量的路径，默认为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_自动生成的路径。

**类型：** string \| string[]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MonitorOptions-path?: string | string[]--><!--Device-MonitorOptions-path?: string | string[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full


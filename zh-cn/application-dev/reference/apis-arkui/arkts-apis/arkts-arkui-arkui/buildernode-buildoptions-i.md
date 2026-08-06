# BuildOptions

build的可选参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface BuildOptions--><!--Device-unnamed-export interface BuildOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## localStorage

```TypeScript
localStorage?: LocalStorage
```

给当前BuilderNode设置LocalStorage，挂载在此BuilderNode下的自定义组件共享该LocalStorage。如果自定义组件构造函数同时也传入LocalStorage，优先使用构造函数中传入的 LocalStorage。 默认值：undefined

**类型：** LocalStorage

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BuildOptions-localStorage?: LocalStorage--><!--Device-BuildOptions-localStorage?: LocalStorage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## useParallel

```TypeScript
useParallel?: boolean
```

是否开启BuilderNode并行构建。\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_表示开启，\_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_表示关闭。 默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BuildOptions-useParallel?: boolean--><!--Device-BuildOptions-useParallel?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full


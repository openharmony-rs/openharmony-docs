# BlurSnapshotOptions（系统接口）

模糊快照优化选项。设置该对象后，将开启模糊优化。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## enableFreeze

```TypeScript
enableFreeze?: boolean
```

设置模糊快照是否开启冻结优化。开启后，在模糊快照时应用冻结优化以降低渲染开销；未设置或设置为false时，冻结优化关闭，采用常规渲染方式。

拉起半模态后支持动态切换该参数值。

默认值：false

**系统接口：** 此接口为系统接口。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

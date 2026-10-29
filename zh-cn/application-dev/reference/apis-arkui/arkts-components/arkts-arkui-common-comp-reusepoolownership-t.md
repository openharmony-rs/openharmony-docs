# ReusePoolOwnership

```TypeScript
declare type ReusePoolOwnership = 'shared' | 'perInstance'
```

全局复用池的持有类型。

'shared'：\@Component/\@ComponentV2类的所有实例共享同一个复用池实例。适用于多个同类型组件实例间需要复用相同资源的场景，可最大化复用池利用率，减少内存占用。'perInstance'：\@Component/\@ComponentV2的每个实例拥有独立的复用池实例。适用于需要隔离各组件实例复用资源的场景，避免不同实例间的复用资源相互影响。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-declare type ReusePoolOwnership = 'shared' | 'perInstance'--><!--Device-unnamed-declare type ReusePoolOwnership = 'shared' | 'perInstance'-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| 'shared' |  |
| 'perInstance' |  |

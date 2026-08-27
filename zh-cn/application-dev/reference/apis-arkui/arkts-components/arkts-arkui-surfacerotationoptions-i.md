# SurfaceRotationOptions

定义屏幕旋转时是否锁定当前XComponent所持有的surface的方向。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## lock

```TypeScript
lock?: boolean
```

屏幕旋转时是否锁定surface的方向。 如果不设置此参数，默认值为false，表示不锁定方向。  
**true**：屏幕旋转时锁定surface的方向。  
**false**：屏幕旋转时不锁定surface的方向。

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

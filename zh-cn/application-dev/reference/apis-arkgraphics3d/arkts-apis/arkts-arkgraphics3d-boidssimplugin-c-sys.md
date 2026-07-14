# BoidsSimPlugin（系统接口）

群组模拟插件. 提供用于管理群组模拟组件的静态方法.

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## getDefaultBoidsSimWorld

```TypeScript
static getDefaultBoidsSimWorld(scene: Scene): BoidsSimWorld | null
```

获取指定场景的默认群组模拟世界.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scene | Scene | 是 | 要获取群组模拟世界的场景 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| BoidsSimWorld | 群组模拟世界，如果插件未加载则返回null |


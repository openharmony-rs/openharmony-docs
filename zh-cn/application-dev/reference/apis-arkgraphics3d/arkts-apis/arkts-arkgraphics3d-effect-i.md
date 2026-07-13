# Effect

特效资源.

**继承/实现关系：** Effect extends [SceneResource](arkts-arkgraphics3d-sceneresource-i.md)

**起始版本：** 21

**系统能力：** SystemCapability.ArkUi.Graphics3D

## getPropertyValue

```TypeScript
getPropertyValue(propertyName: string): Object | null | undefined
```

获取特定特效属性的值.

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propertyName | string | 是 | 特定属性的名称 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 特效属性值，如果"get"操作失败则返回null. |

## setPropertyValue

```TypeScript
setPropertyValue(propertyName: string, value: Object | undefined): boolean
```

设置特定特效属性的值

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propertyName | string | 是 | 特定属性的名称 |
| value | Object \| undefined | 是 | 要设置的属性值 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果"set"操作失败则返回false |

## effectId

```TypeScript
readonly effectId: string
```

特效的ID.
这是用于创建特效的ID.

**类型：** string

**起始版本：** 21

**系统能力：** SystemCapability.ArkUi.Graphics3D

## enabled

```TypeScript
enabled: boolean
```

控制特效是否启用.

**类型：** boolean

**起始版本：** 21

**系统能力：** SystemCapability.ArkUi.Graphics3D


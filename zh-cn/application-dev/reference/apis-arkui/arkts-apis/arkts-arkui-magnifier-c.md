# Magnifier

提供控制放大镜的能力。

**起始版本：** 22

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## bind

```TypeScript
bind(id: string): void
```

将放大镜和组件绑定。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 组件id |

## show

```TypeScript
show(x: number, y: number): void
```

设置放大镜显示内容的位置。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | 放大镜显示内容相对组件水平方向坐标。单位为vp。 |
| y | number | 是 | 放大镜显示内容相对组件垂直方向坐标。单位为vp。 |

## unbind

```TypeScript
unbind(): void
```

将放大镜和组件解绑。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full


# Magnifier

提供控制放大镜的能力。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class Magnifier--><!--Device-unnamed-export declare class Magnifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## bind

```TypeScript
bind(id: string): void
```

将放大镜和组件绑定。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Magnifier-bind(id: string): void--><!--Device-Magnifier-bind(id: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 组件id |

## show

```TypeScript
show(x: double, y: double): void
```

设置放大镜显示内容的位置。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Magnifier-show(x: double, y: double): void--><!--Device-Magnifier-show(x: double, y: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | double | 是 | 放大镜显示内容相对组件水平方向坐标。 单位为vp |
| y | double | 是 | 放大镜显示内容相对组件垂直方向坐标。 单位为vp |

## unbind

```TypeScript
unbind(): void
```

将放大镜和组件解绑。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Magnifier-unbind(): void--><!--Device-Magnifier-unbind(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full


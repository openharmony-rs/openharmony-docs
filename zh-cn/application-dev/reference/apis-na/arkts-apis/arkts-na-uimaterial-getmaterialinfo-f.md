# getMaterialInfo

## 导入模块

```TypeScript
```

## getMaterialInfo

```TypeScript
export function getMaterialInfo(): MaterialInfo
```

获取当前应用的材质配置信息。返回的配置信息来自应用在[module.json5](../../../quick-start/module-configuration-file.md)中配置的metadata。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiMaterial-export function getMaterialInfo(): MaterialInfo--><!--Device-uiMaterial-export function getMaterialInfo(): MaterialInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MaterialInfo](../../apis-arkui/arkts-apis/arkts-arkui-uimaterial-materialinfo-i.md) | 返回当前应用的材质配置信息，包含材质使能状态和材质类型。 |


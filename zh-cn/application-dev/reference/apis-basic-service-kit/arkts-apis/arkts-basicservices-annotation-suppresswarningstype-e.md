# SuppressWarningsType

支持消除告警的规则。帮助开发者根据实际需求选择性地屏蔽兼容性告警、多设备告警、权限告警等，在确保代码质量的同时减少不必要的告警干扰，提升开发体验。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export const enum SuppressWarningsType--><!--Device-unnamed-export const enum SuppressWarningsType-End-->

**系统能力：** SystemCapability.Base

## COMPATIBILITY

```TypeScript
COMPATIBILITY = 'compatibility'
```

支持消除兼容性告警。 当调用API的起始版本高于工程设置的兼容SDK版本时（build-profile.json5中指定的compatibleSdkVersion）产生的告警。 建议在已做版本判断或兼容性处理时使用，避免盲目抑制告警导致低版本设备运行异常。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-SuppressWarningsType-COMPATIBILITY = 'compatibility'--><!--Device-SuppressWarningsType-COMPATIBILITY = 'compatibility'-End-->

**系统能力：** SystemCapability.Base

## SYSCAP

```TypeScript
SYSCAP = 'syscap'
```

支持消除多设备告警。当调用API的系统能力在目标设备上不支持时产生的告警。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-SuppressWarningsType-SYSCAP = 'syscap'--><!--Device-SuppressWarningsType-SYSCAP = 'syscap'-End-->

**系统能力：** SystemCapability.Base

## PERMISSION

```TypeScript
PERMISSION = 'permission'
```

支持消除权限告警。当调用需要权限的API但未在配置文件中声明相应权限时产生的告警。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-SuppressWarningsType-PERMISSION = 'permission'--><!--Device-SuppressWarningsType-PERMISSION = 'permission'-End-->

**系统能力：** SystemCapability.Base


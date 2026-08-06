# InterruptForceType

表示音频打断类型的枚举。 当用户监听到音频中断（即收到[InterruptEvent]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_事件）时，获取此信息。 此类型表示音频打断是否已由系统强制执行，具体操作信息（如音频暂停、停止等）可通过[InterruptHint]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_获取。关于音频打断策略的详细说明可参考文档 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-audio-enum InterruptForceType--><!--Device-audio-enum InterruptForceType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_FORCE

```TypeScript
INTERRUPT_FORCE = 0
```

强制打断类型，即具体操作已由系统强制执行。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InterruptForceType-INTERRUPT_FORCE = 0--><!--Device-InterruptForceType-INTERRUPT_FORCE = 0-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## INTERRUPT_SHARE

```TypeScript
INTERRUPT_SHARE = 1
```

共享打断类型，即系统不执行具体操作，通过[InterruptHint]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_建议并提示应用操作，应用可自行决策下一步处理方式。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InterruptForceType-INTERRUPT_SHARE = 1--><!--Device-InterruptForceType-INTERRUPT_SHARE = 1-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer


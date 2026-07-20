# EffectiveMode（系统接口）

生效模式。

**起始版本：** 9

<!--Device-update-export enum EffectiveMode--><!--Device-update-export enum EffectiveMode-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## COLD

```TypeScript
COLD = 1
```

冷升级，需重启设备生效，适用于需要完整系统重置或固件升级的场景。详见[术语](docroot://basic-services/update/update-kit-term.md)。

**起始版本：** 9

<!--Device-EffectiveMode-COLD = 1--><!--Device-EffectiveMode-COLD = 1-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## LIVE

```TypeScript
LIVE = 2
```

热升级，无需重启即可生效，适用于应用层组件升级或需要保持设备运行的场景。详见[术语](docroot://basic-services/update/update-kit-term.md)。

**起始版本：** 9

<!--Device-EffectiveMode-LIVE = 2--><!--Device-EffectiveMode-LIVE = 2-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## LIVE_AND_COLD

```TypeScript
LIVE_AND_COLD = 3
```

融合升级，结合两者特性，适用于同时包含热升级和冷升级组件的场景。详见[术语](docroot://basic-services/update/update-kit-term.md)。

**起始版本：** 9

<!--Device-EffectiveMode-LIVE_AND_COLD = 3--><!--Device-EffectiveMode-LIVE_AND_COLD = 3-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。


# KeyPolicy

按键策略。MDM应用下发按键策略的按键编码与系统按键事件匹配后的系统行为。

**起始版本：** 23

<!--Device-systemManager-enum KeyPolicy--><!--Device-systemManager-enum KeyPolicy-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## INTERCEPTION

```TypeScript
INTERCEPTION = 0
```

拦截消息。设置后仅会拦截当前按键事件，系统不会再处理该事件，按键回调接口也不会响应按键事件。例如：下发电源键拦截策略后，按电源键无任何响应，无法关机，无法锁屏，仅影响开机状态下电源键事件，关机时可通过电源键正常开机。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyPolicy-INTERCEPTION = 0--><!--Device-KeyPolicy-INTERCEPTION = 0-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## CUSTOM

```TypeScript
CUSTOM = 1
```

拦截并转发消息。 设置后会拦截当前按键事件，系统不会再处理该事件，同时通过[EnterpriseAdminExtensionAbility.onKeyEvent](arkts-mdm-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md#onkeyevent)回调接口将发生的按键事件通知给MDM应用，通知MDM应用处理该事件的过程不会阻塞系统后续的其他事件处理。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KeyPolicy-CUSTOM = 1--><!--Device-KeyPolicy-CUSTOM = 1-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager


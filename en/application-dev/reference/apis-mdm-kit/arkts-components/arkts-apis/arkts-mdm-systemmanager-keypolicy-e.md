# KeyPolicy

Enumerates key policies. This refers to the system behavior triggered after the key code delivered by the MDM app matches the system key event.

**Since:** 23

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## INTERCEPTION

```TypeScript
INTERCEPTION = 0
```

Intercepts messages. After this parameter is set, only the current key event is intercepted. The system does not process the event, and the key callback API does not respond to the key event. For example, after the power key interception policy is delivered, pressing the power key does not respond, the device cannot be powered off or locked, and only the power key event in the power-on state is affected. When the device is powered off, the power key can be used to power on the device.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## CUSTOM

```TypeScript
CUSTOM = 1
```

Intercepts and forwards messages. When this policy is configured, the system intercepts the current key event and does not process the event. In addition, the [EnterpriseAdminExtensionAbility.onKeyEvent](arkts-mdm-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md#onkeyevent) callback API is used to notify the MDM app of the key event, which does not block the processing of other events.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

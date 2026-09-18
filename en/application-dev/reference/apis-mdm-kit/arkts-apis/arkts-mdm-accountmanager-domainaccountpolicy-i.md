# DomainAccountPolicy

Domain account policy.

**Since:** 19

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { accountManager } from '@kit.MDMKit';
```

## authenticationValidityPeriod

```TypeScript
authenticationValidityPeriod?: number
```

Validity period (in seconds) of the token for domain account authentication. This parameter is used to control that a user can access system resources without repeated authentication within the validity period of the token. The value range is [-1,2147483647]. The validity period starts from the time when the domain account is authenticated for the last time, for example, login or unlocking after the screen is locked.

The default value is **-1**, indicating that the token is permanently valid. The value **0** indicates that the token becomes invalid immediately. After the token expires or becomes invalid, the domain account and password must be authenticated when a user logs in to the system.

**Type:** number

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## passwordExpirationNotification

```TypeScript
passwordExpirationNotification?: number
```

Notification period before a domain account password expires, in seconds. The value range is [0, 2147483647].

The default value is **0**, indicating that the system does not display a message indicating that the domain account password has expired.

**Note:** **passwordExpirationNotification** must be used together with **passwordValidityPeriod**. When the system time is later than or equal to (the time when the domain account password is last changed on the device + the value of **passwordValidityPeriod** – the value of **passwordExpirationNotification**), a message is displayed, indicating that the password is about to expire.

**Type:** number

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## passwordValidityPeriod

```TypeScript
passwordValidityPeriod?: number
```

Validity period (in seconds) of the domain account password. It is used to require users to change their passwords periodically to enhance account security. The value range is [-1, 2147483647]. The validity period starts from the time of the last password change on the device side.

The default value is **-1**, indicating that the domain account password is permanently valid.

**Type:** number

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## supportUKeyAuthentication

```TypeScript
supportUKeyAuthentication?: boolean
```

Whether the domain account supports USB key authentication.

If set to **true**, the domain account supports USB key authentication for login.If set to **false**, the domain account does not support USB key authentication. Default value: false.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

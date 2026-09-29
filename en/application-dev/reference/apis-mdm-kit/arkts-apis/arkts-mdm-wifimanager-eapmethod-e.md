# EapMethod

```TypeScript
enum EapMethod
```

Enumerates the EAP authentication methods.

> **NOTE:** 
> 
> Currently, only the EAP_PEAP and EAP_TLS authentication methods are supported.

**Since:** 12

<!--Device-wifiManager-enum EapMethod--><!--Device-wifiManager-enum EapMethod-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## EAP_NONE

```TypeScript
EAP_NONE = 0
```

Not specified.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-EapMethod-EAP_NONE = 0--><!--Device-EapMethod-EAP_NONE = 0-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## EAP_PEAP

```TypeScript
EAP_PEAP = 1
```

Protected Extensible Authentication Protocol (PEAP). It first establishes a secure TLS tunnel, followed by performing simple authentication within the tunnel.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-EapMethod-EAP_PEAP = 1--><!--Device-EapMethod-EAP_PEAP = 1-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## EAP_TLS

```TypeScript
EAP_TLS = 2
```

Transport Layer Security (TLS). It implements mutual certificate authentication.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-EapMethod-EAP_TLS = 2--><!--Device-EapMethod-EAP_TLS = 2-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## EAP_TTLS

```TypeScript
EAP_TTLS = 3
```

Tunnel Transport Layer Security (TTLS). It is similar to PEAP, but supports a more diverse set of authentication methods inside the tunnel.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-EapMethod-EAP_TTLS = 3--><!--Device-EapMethod-EAP_TTLS = 3-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## EAP_PWD

```TypeScript
EAP_PWD = 4
```

Password Authentication (PWD). It enables password-based authentication and does not require a server certificate.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-EapMethod-EAP_PWD = 4--><!--Device-EapMethod-EAP_PWD = 4-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## EAP_SIM

```TypeScript
EAP_SIM = 5
```

Subscriber Identity Module (SIM). It performs authentication using the keys and algorithms stored in the SIM card of a smartphone.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-EapMethod-EAP_SIM = 5--><!--Device-EapMethod-EAP_SIM = 5-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## EAP_AKA

```TypeScript
EAP_AKA = 6
```

Authentication and Key Agreement (AKA). It performs authentication using enhanced keys and algorithms stored in a USIM card (applicable to 3G/4G/5G SIM cards).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-EapMethod-EAP_AKA = 6--><!--Device-EapMethod-EAP_AKA = 6-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## EAP_AKA_PRIME

```TypeScript
EAP_AKA_PRIME = 7
```

AKA Prime. It is an enhanced version of EAP-AKA and binds the network name during key derivation.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-EapMethod-EAP_AKA_PRIME = 7--><!--Device-EapMethod-EAP_AKA_PRIME = 7-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## EAP_UNAUTH_TLS

```TypeScript
EAP_UNAUTH_TLS = 8
```

Unauthenticated TLS (UNAUTH TLS). It implements one-way authentication (client authentication only) while establishing an encrypted communication channel.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-EapMethod-EAP_UNAUTH_TLS = 8--><!--Device-EapMethod-EAP_UNAUTH_TLS = 8-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

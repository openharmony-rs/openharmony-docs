# SuppState (System API)

```TypeScript
export enum SuppState
```

The state of the supplicant enumeration.

@enum { int }

**Since:** 9

<!--Device-wifiManager-export enum SuppState--><!--Device-wifiManager-export enum SuppState-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## DISCONNECTED

```TypeScript
DISCONNECTED
```

The supplicant is not associated with or is disconnected from the AP.

**Since:** 9

<!--Device-SuppState-DISCONNECTED--><!--Device-SuppState-DISCONNECTED-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## INTERFACE_DISABLED

```TypeScript
INTERFACE_DISABLED
```

The network interface is disabled.

**Since:** 9

<!--Device-SuppState-INTERFACE_DISABLED--><!--Device-SuppState-INTERFACE_DISABLED-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## INACTIVE

```TypeScript
INACTIVE
```

The supplicant is disabled.

**Since:** 9

<!--Device-SuppState-INACTIVE--><!--Device-SuppState-INACTIVE-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## SCANNING

```TypeScript
SCANNING
```

The supplicant is scanning for a Wi-Fi connection.

**Since:** 9

<!--Device-SuppState-SCANNING--><!--Device-SuppState-SCANNING-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## AUTHENTICATING

```TypeScript
AUTHENTICATING
```

The supplicant is authenticating with a specified AP.

**Since:** 9

<!--Device-SuppState-AUTHENTICATING--><!--Device-SuppState-AUTHENTICATING-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## ASSOCIATING

```TypeScript
ASSOCIATING
```

The supplicant is associating with a specified AP.

**Since:** 9

<!--Device-SuppState-ASSOCIATING--><!--Device-SuppState-ASSOCIATING-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## ASSOCIATED

```TypeScript
ASSOCIATED
```

The supplicant is associated with a specified AP.

**Since:** 9

<!--Device-SuppState-ASSOCIATED--><!--Device-SuppState-ASSOCIATED-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## FOUR_WAY_HANDSHAKE

```TypeScript
FOUR_WAY_HANDSHAKE
```

The four-way handshake is ongoing.

**Since:** 9

<!--Device-SuppState-FOUR_WAY_HANDSHAKE--><!--Device-SuppState-FOUR_WAY_HANDSHAKE-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## GROUP_HANDSHAKE

```TypeScript
GROUP_HANDSHAKE
```

The group handshake is ongoing.

**Since:** 9

<!--Device-SuppState-GROUP_HANDSHAKE--><!--Device-SuppState-GROUP_HANDSHAKE-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## COMPLETED

```TypeScript
COMPLETED
```

All authentication is completed.

**Since:** 9

<!--Device-SuppState-COMPLETED--><!--Device-SuppState-COMPLETED-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## UNINITIALIZED

```TypeScript
UNINITIALIZED
```

Failed to establish a connection to the supplicant.

**Since:** 9

<!--Device-SuppState-UNINITIALIZED--><!--Device-SuppState-UNINITIALIZED-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

## INVALID

```TypeScript
INVALID
```

The supplicant is in an unknown or invalid state.

**Since:** 9

<!--Device-SuppState-INVALID--><!--Device-SuppState-INVALID-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

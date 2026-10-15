# NetType (System API)

```TypeScript
export enum NetType
```

Enumerates the network types allowed for download. The value **CELLULAR** indicates that only download over the cellular network is allowed; **WiFi** that only download using Wi-Fi is allowed; **CELLULAR_AND_WIFI** indicates that download over both the cellular network and Wi-Fi is allowed.

**Since:** 9

<!--Device-update-export enum NetType--><!--Device-update-export enum NetType-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## CELLULAR

```TypeScript
CELLULAR = 1
```

Data network.

**Since:** 9

<!--Device-NetType-CELLULAR = 1--><!--Device-NetType-CELLULAR = 1-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## CELLULAR_AND_WIFI

```TypeScript
CELLULAR_AND_WIFI = 7
```

Data network and Wi-Fi.

**Since:** 9

<!--Device-NetType-CELLULAR_AND_WIFI = 7--><!--Device-NetType-CELLULAR_AND_WIFI = 7-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## METERED_WIFI

```TypeScript
METERED_WIFI = 2
```

Wi-Fi hotspot.

**Since:** 9

<!--Device-NetType-METERED_WIFI = 2--><!--Device-NetType-METERED_WIFI = 2-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## NOT_METERED_WIFI

```TypeScript
NOT_METERED_WIFI = 4
```

Non Wi-Fi hotspot.

**Since:** 9

<!--Device-NetType-NOT_METERED_WIFI = 4--><!--Device-NetType-NOT_METERED_WIFI = 4-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## WIFI

```TypeScript
WIFI = 6
```

Wi-Fi.

**Since:** 9

<!--Device-NetType-WIFI = 6--><!--Device-NetType-WIFI = 6-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

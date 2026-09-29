# DescriptionType (System API)

```TypeScript
export enum DescriptionType
```

Enumerates description file types.

**Since:** 9

<!--Device-update-export enum DescriptionType--><!--Device-update-export enum DescriptionType-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## CONTENT

```TypeScript
CONTENT = 0
```

Content. This type indicates that the description content is directly provided, which is applicable to scenarios where the description content is short or needs to be displayed immediately.

**Since:** 9

<!--Device-DescriptionType-CONTENT = 0--><!--Device-DescriptionType-CONTENT = 0-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## URI

```TypeScript
URI = 1
```

Link. This type indicates that the description is provided through a link, which is applicable to scenarios where the description content is long or needs to be obtained from external resources.

**Since:** 9

<!--Device-DescriptionType-URI = 1--><!--Device-DescriptionType-URI = 1-End-->

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

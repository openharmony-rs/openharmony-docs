# DescriptionInfo (System API)

Represents information about the version description file.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## content

```TypeScript
content: string
```

Content of the description file.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## descriptionType

```TypeScript
descriptionType: DescriptionType
```

Description type. The value **CONTENT** indicates that the description is content, which is applicable to scenarios where the description content is short or needs to be displayed immediately. **URI** indicates that the description is a link, which is applicable to scenarios where the description content is long or needs to be obtained from external resources. Select a value based on the description length and display mode.

**Type:** [DescriptionType](arkts-basicservices-update-descriptiontype-e-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

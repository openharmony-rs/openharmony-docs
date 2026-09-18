# ContentFormCard

Defines the information of a content card component that is displayed in an application, including the title, description, content image, application information, and the like. It is applicable to scenarios such as content distribution, social updates, and message notifications.

**Since:** 20

**Decorator:** @Component

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { ContentFormCard, FormType } from '@kit.ArkData';
```

## contentFormData

```TypeScript
contentFormData: uniformDataStruct.ContentForm
```

Data of the form card.

**Type:** [uniformDataStruct.ContentForm](arkts-arkdata-uniformdatastruct-contentform-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## formHeight

```TypeScript
formHeight?: number
```

Height of the content form card. The unit of measurement is vp.

**Type:** number

**Since:** 20

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## formType

```TypeScript
formType: FormType
```

Type of the form card.

**Type:** [FormType](arkts-arkdata-data-udmfcomponents-formtype-e.md)

**Since:** 20

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## formWidth

```TypeScript
formWidth?: number
```

Width of the content form card. The unit of measurement is vp.

**Type:** number

**Since:** 20

**Decorator:** @Prop

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## handleOnClick

```TypeScript
handleOnClick?: Function
```

Callback to be invoked when the form card is tapped.

**Type:** Function

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

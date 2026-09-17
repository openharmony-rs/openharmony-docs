# PhotoEditorExtensionAbility

Class of the photo editor ExtensionAbility, which provides APIs for you to edit photos.

@extends ExtensionAbility

**Inheritance/Implementation:** PhotoEditorExtensionAbility extends [ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md)

**Since:** 12

**System capability:** SystemCapability.Ability.AppExtension.PhotoEditorExtension

## Modules to Import

```TypeScript
import { PhotoEditorExtensionAbility } from '@kit.AbilityKit';
```

## onBackground

```TypeScript
onBackground(): void
```

Called back when the state of an UI extension changes to background.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Examples**

```TypeScript
import { PhotoEditorExtensionAbility } from '@kit.AbilityKit';

const TAG: string = '[testTag] ExamplePhotoEditorAbility';

export default class ExamplePhotoEditorAbility extends PhotoEditorExtensionAbility {
  onBackground() {
    console.info(TAG, `onBackground`);
  }
}
```

## onCreate

```TypeScript
onCreate(): void
```

Called back when an UI extension is started for initialization.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AppExtension.PhotoEditorExtension

**Examples**

```TypeScript
import { PhotoEditorExtensionAbility } from '@kit.AbilityKit';

const TAG: string = '[testTag] ExamplePhotoEditorAbility';

export default class ExamplePhotoEditorAbility extends PhotoEditorExtensionAbility {
  onCreate() {
    console.info(TAG, `onCreate`);
  }
}
```

## onDestroy

```TypeScript
onDestroy(): void | Promise<void>
```

Called back before an UI extension is destroyed.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AppExtension.PhotoEditorExtension

**Examples**

```TypeScript
A synchronous callback example is as follows:
```

```TypeScript
A promise asynchronous callback example is as follows:
```

## onForeground

```TypeScript
onForeground(): void
```

Called back when the state of an UI extension changes to foreground.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Examples**

```TypeScript
import { PhotoEditorExtensionAbility } from '@kit.AbilityKit';

const TAG: string = '[testTag] ExamplePhotoEditorAbility';

export default class ExamplePhotoEditorAbility extends PhotoEditorExtensionAbility {
  onForeground() {
    console.info(TAG, `onForeground`);
  }
}
```

## onStartContentEditing

```TypeScript
onStartContentEditing(uri: string, want: Want, session: UIExtensionContentSession): void
```

Called back when an UI extension session is created and original image is ready.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AppExtension.PhotoEditorExtension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | Indicates the uri info of the original image. |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Indicates the want info of the UI extension. |
| session | [UIExtensionContentSession](arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md) | Yes | Indicates the session of the UI extension page. |

**Examples**

```TypeScript
import { PhotoEditorExtensionAbility, Want, UIExtensionContentSession } from '@kit.AbilityKit';

const TAG: string = '[testTag] ExamplePhotoEditorAbility';

export default class ExamplePhotoEditorAbility extends PhotoEditorExtensionAbility {
  onStartContentEditing(uri: string, want: Want, session: UIExtensionContentSession) {
    console.info(TAG, `onStartContentEditing want: ${JSON.stringify(want)}, uri: ${uri}`);
  }
}
```

## context

```TypeScript
context: PhotoEditorExtensionContext
```

Indicates configuration information about an Photo editor extension ability context.

**Type:** [PhotoEditorExtensionContext](arkts-ability-photoeditorextensioncontext-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AppExtension.PhotoEditorExtension

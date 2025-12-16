# @ohos.app.ability.PhotoEditorExtensionAbility (ExtensionAbility for Image Editing)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @liusu23-->
<!--Designer: @xukeke-->
<!--Tester: @lusq-->
<!--Adviser: @huipeizi-->

The PhotoEditorExtensionAbility enables your application to provide an image editing page for applications that do not have the image editing capability. It inherits from the [ExtensionAbility](js-apis-app-ability-extensionAbility.md). After an application uses [startAbilityByType](js-apis-inner-application-uiAbilityContext.md#startability) to start a vertical domain panel with available image editing applications that have implemented the PhotoEditorExtensionAbility, the user can select one of the applications on the panel to display an image editing page.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> 
> The APIs of this module can be used only in the stage model.

## Implementation Effect

The figure below shows an example of an image editing page implemented using the PhotoEditorExtensionAbility. The layout and features of this page can be fully customized to meet specific needs.

![Targetapp_PhotoEditorExtensionAbility](figures/photo-editor-demo.png)

## Modules to Import

```ts
import { PhotoEditorExtensionAbility } from '@kit.AbilityKit';
```

## PhotoEditorExtensionAbility

### Properties

**System capability**: SystemCapability.Ability.AppExtension.PhotoEditorExtension

|  Name|Type  |Read Only  |Optional  |Description  |
| ------------ | ------------ | ------------ | ------------ | ------------ |
|  context | [PhotoEditorExtensionContext](./js-apis-app-ability-photoEditorExtensionContext.md)  | No | No | Context of the PhotoEditorExtensionAbility. It provides the capability of saving images. |

### onCreate

onCreate(): void

Called when a PhotoEditorExtensionAbility instance is created. Within this callback, you can execute initialization logic within this callback.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AppExtension.PhotoEditorExtension

**Example**

```ts
import { PhotoEditorExtensionAbility } from '@kit.AbilityKit';

const TAG: string = '[testTag] ExamplePhotoEditorAbility';

export default class ExamplePhotoEditorAbility extends PhotoEditorExtensionAbility {
  onCreate() {
    console.info(TAG, `onCreate`);
  }
}

```

### onStartContentEditing

onStartContentEditing(uri: string, want: Want, session: UIExtensionContentSession): void

Called when a UIExtensionContentSession instance (an image editing page) is created for this PhotoEditorExtensionAbility. Within this callback, you can read the original image and load the page.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AppExtension.PhotoEditorExtension

**Parameters**
| Name|  Type| Mandatory | Description |
| ------------ | ------------ | ------------ | ------------ |
|  uri |  string |  Yes| [URI](../apis-core-file-kit/js-apis-file-fileuri.md) of the image to edit. The format is file://\<bundleName>/\<sandboxPath>. |
| want  | [Want](./js-apis-app-ability-want.md)  | Yes | Want information, including the ability name and bundle name, of the PhotoEditorExtensionAbility. |
|  session |  [UIExtensionContentSession](./js-apis-app-ability-uiExtensionContentSession.md) | Yes |  UI content information related to the PhotoEditorExtensionAbility.|


**Example**

```ts
import { PhotoEditorExtensionAbility, Want, UIExtensionContentSession } from '@kit.AbilityKit';

const TAG: string = '[testTag] ExamplePhotoEditorAbility';

export default class ExamplePhotoEditorAbility extends PhotoEditorExtensionAbility {
  onStartContentEditing(uri: string, want: Want, session: UIExtensionContentSession) {
    console.info(TAG, `onStartContentEditing want: ${JSON.stringify(want)}, uri: ${uri}`);
  }
}

```

### onForeground

onForeground(): void

Called when this PhotoEditorExtensionAbility transitions from the background to the foreground.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Example**

```ts
import { PhotoEditorExtensionAbility } from '@kit.AbilityKit';

const TAG: string = '[testTag] ExamplePhotoEditorAbility';

export default class ExamplePhotoEditorAbility extends PhotoEditorExtensionAbility {
  onForeground() {
    console.info(TAG, `onForeground`);
  }
}

```

### onBackground

onBackground(): void

Called when this PhotoEditorExtensionAbility transitions from the foreground to the background.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Example**

```ts
import { PhotoEditorExtensionAbility } from '@kit.AbilityKit';

const TAG: string = '[testTag] ExamplePhotoEditorAbility';

export default class ExamplePhotoEditorAbility extends PhotoEditorExtensionAbility {
  onBackground() {
    console.info(TAG, `onBackground`);
  }
}

```

### onDestroy

onDestroy(): void | Promise\<void>

Called when this PhotoEditorExtensionAbility is destroyed. Within this callback, you can clear resources. This API returns the result synchronously or uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AppExtension.PhotoEditorExtension

**Return value**
|  Type|Description  |
| ------------ | ------------ |
|  void \| Promise\<void> |  No return value or a Promise object that returns no value.|

**Example**

- A synchronous callback example is as follows:
  ```ts
  import { PhotoEditorExtensionAbility } from '@kit.AbilityKit';

  const TAG: string = '[testTag] ExamplePhotoEditorAbility';

  export default class ExamplePhotoEditorAbility extends PhotoEditorExtensionAbility {
    onDestroy() {
      console.info(TAG, `onDestroy`);
      // Call the synchronous function.
    }
  }

  ```
- A promise asynchronous callback example is as follows:

  ```ts
  import { PhotoEditorExtensionAbility } from '@kit.AbilityKit';

  const TAG: string = '[testTag] ExamplePhotoEditorAbility';

  export default class ExamplePhotoEditorAbility extends PhotoEditorExtensionAbility {
    async onDestroy() {
      console.info(TAG, `onDestroy`);
      // Call the asynchronous function.
    }
  }

  ```

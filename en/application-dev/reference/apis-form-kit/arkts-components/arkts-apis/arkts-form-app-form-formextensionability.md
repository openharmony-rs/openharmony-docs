# @ohos.app.form.FormExtensionAbility

The **FormExtensionAbility** module provides lifecycle callbacks invoked when a widget is created, destroyed, or
 updated.

> **NOTE**

> - The formExtensionAbility is cleared after 10 seconds of inactivity.

> - The following modules cannot be referenced in the FormExtensionAbility, as doing so may cause the program to exit
 >  abnormally:
 >   - @ohos.ability.particleAbility (ParticleAbility)
 >   - @ohos.multimedia.audio (Audio Management)
 >   - @ohos.multimedia.camera (Camera Management)
 >   - @ohos.multimedia.media (Media)
 >   - @ohos.resourceschedule.backgroundTaskManager (Background Task Management)



## Modules to Import

```TypeScript
import { FormExtensionAbility } from '@kit.FormKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [FormExtensionAbility](arkts-form-app-form-formextensionability-formextensionability-c.md) | Widget extension class. It provides APIs to notify the widget provider that a widget is being created or the widget visibility status is being changed. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [FormExtensionAbility](arkts-form-app-form-formextensionability-formextensionability-c-sys.md) | Widget extension class. It provides APIs to notify the widget provider that a widget is being created or the widget visibility status is being changed. |
<!--DelEnd-->

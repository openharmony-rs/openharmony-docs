# Developing a Scene-based Widget (for System Applications)

For details about the development guidelines of scene-based widgets, see [Developing a Scene-based Widget](arkts-ui-liveform-sceneanimation-development.md). For system applications, scene-based widgets provide two extended capabilities: gesture suspension configuration and long-term widget activation.

## Available APIs

The following table lists the key APIs for a scene-based widget.

**Table 1** Main APIs

| API                                                                                                                                                                      | Description                                                                                                                 |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| [formProvider.activateSceneAnimation(formId: string): Promise&lt;void&gt;](../reference/apis-form-kit/js-apis-app-form-formProvider-sys.md#activatesceneanimation20)     | Called to switch the interactive widget state to active.|
| [formProvider.deactivateSceneAnimation(formId: string): Promise&lt;void&gt;](../reference/apis-form-kit/js-apis-app-form-formProvider-sys.md#deactivatesceneanimation20) | Called to switch the interactive widget state to inactive.|


## Gesture Suspension Configuration
For [scene-based widgets](arkts-ui-liveform-sceneanimation-overview.md), operations such as long-pressing and dragging on the home screen will interrupt the current animation, causing the widget to revert to the inactive state. However, system applications can cancel this limitation by configuring [disabledDesktopBehaviors](arkts-ui-widget-configuration.md#sceneanimationparams-field) in the **form_config.json** file, ensuring smooth animations within the interactive target of the activated widget.
If no configuration is performed, the system does not intercept any valid gesture operations on the home screen by default. Once gestures are intercepted, the corresponding gesture events are handled by the LiveFormExtensionAbility.

```ts
// entry/src/main/resources/base/profile/form_config.json
{
  "forms": [
    {
      // ...
      "sceneAnimationParams": {
        "abilityName": "MySystemLiveFormExtensionAbility",
        "disabledDesktopBehaviors": [
          "SWIPE_DESKTOP",
          "PULL_DOWN_SEARCH",
          "LONG_CLICK",
          "DRAG"
        ]
      }
    }
  ]
}
```

## Long-term Widget Activation

For system applications, the widget provider can use APIs to switch widget states. The active duration is not strictly limited, which means a widget can remain active for a long time. You can call [formProvider.activateSceneAnimation](../reference/apis-form-kit/js-apis-app-form-formProvider-sys.md#activatesceneanimation20) and [formProvider.deactivateSceneAnimation](../reference/apis-form-kit/js-apis-app-form-formProvider-sys.md#deactivatesceneanimation20) to activate and deactivate a widget.
After the widget is activated by calling **formProvider.activateSceneAnimation**, the rendering area of the widget animation is the same as that of the widget itself, and the [formProvider.requestOverflow](../reference/apis-form-kit/js-apis-app-form-formProvider.md#formproviderrequestoverflow20) API cannot be called to request animation.

### How to Develop
1. Import modules.

```ts
import { formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
```

2. Trigger long-time widget activation.

```ts
let formId: string = '12400633174999288';

try {
  formProvider.activateSceneAnimation(formId).then(() => {
    console.info('activateSceneAnimation succeed.');
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message})`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message})`);
}
```

3. Deactivate the widget.

```ts
let formId: string = '12400633174999288';

try {
  formProvider.deactivateSceneAnimation(formId).then(() => {
    console.info('deactivateSceneAnimation succeed.');
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message})`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message})`);
}
```

4. Adapt LiveFormExtensionAbility.

To allow the widget provider to accurately control widget state switching and prevent delays caused by complex UI loading, the widget provider should notify the widget host via **session** when transitioning to the active state. After receiving the notification, the widget host starts to load the activated widget UI.

```ts
// entry/src/main/ets/mysystemliveformextensionability/MySystemLiveFormExtensionAbility.ets 
import { formInfo, LiveFormInfo, LiveFormExtensionAbility } from '@kit.FormKit';
import { UIExtensionContentSession } from '@kit.AbilityKit';

export default class MySystemLiveFormExtensionAbility extends LiveFormExtensionAbility {
  onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession) {
    let storage: LocalStorage = new LocalStorage();
    storage.setOrCreate('session', session);

    // Obtain the widget information.
    let formId: string = liveFormInfo.formId as string;
    storage.setOrCreate('formId', formId);
    let formRect: formInfo.Rect = liveFormInfo.rect;
    storage.setOrCreate('formRect', formRect);
    let borderRadius: number = liveFormInfo.borderRadius;
    storage.setOrCreate('borderRadius', borderRadius);
    console.log(`MySystemLiveFormExtensionAbility onSessionCreate formId: ${formId}, borderRadius: ${borderRadius}` +
      `, formRect: ${JSON.stringify(formRect)}`);

    // Load the provider page.
    session.loadContent('mysystemliveformextensionability/pages/MySystemLiveFormPage', storage);

    // The widget provider needs to notify the widget host via session when the activated page is ready.
    session.sendData({['isFormReady']: true});
  }

  onLiveFormDestroy(liveFormInfo: LiveFormInfo) {
    console.log(`MySystemLiveFormExtensionAbility onDestroy`);
  }
}
```

# Effect

Effect resource, which inherits from SceneResource. It is obtained from the createEffect API.

@extends SceneResource @interface Effect

**Inheritance/Implementation:** Effect extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)

**Since:** 21

**System capability:** SystemCapability.ArkUi.Graphics3D

## getPropertyValue

```TypeScript
getPropertyValue(propertyName: string): Object | null | undefined
```

Obtains the value of the specified effect property.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propertyName | string | Yes | Name of a specified effect property. Currently, the following strings are supported: -'exposure': exposure level of an image. -'vibrance': natural saturation of an image. |

**Return value:**

| Type | Description |
| --- | --- |
| Object &#124; null &#124; undefined | Effect property value. If the value fails to be obtained, null is returned. |

**Examples**

```TypeScript
import { SceneResourceFactory, Scene, Effect, EffectParameters } from '@kit.ArkGraphics3D';

function getEffectProperty() {
  let scene: Promise<Scene> = Scene.load();
  scene.then(async (result: Scene | undefined) => {
    if (!result) {
      return;
    }
    let sceneFactory: SceneResourceFactory = result.getResourceFactory();
    // Effect ID, which is in the format of 'XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX', for example, 'e68a7f45-2d21-4a0d-9aef-7d9c825d3f12'.
    let params: EffectParameters = {effectId: "e68a7f45-2d21-4a0d-9aef-7d9c825d3f12"};
    let effect: Effect = await sceneFactory.createEffect(params);
    effect.getPropertyValue('exposure');
  });
}
```

## setPropertyValue

```TypeScript
setPropertyValue(propertyName: string, value: Object | undefined): boolean
```

Sets the value of a specified effect property.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propertyName | string | Yes | Name of a specified effect property. Currently, the following strings are supported: -'exposure': exposure level of an image. -'vibrance': natural saturation of an image. |
| value | Object &#124; undefined | Yes | Value of the effect property to set. -'exposure': The value is of the number type. The recommended value range is [-5, 5]. A larger value indicates a brighter image. -'vibrance': The value is of the number type. The recommended value range is [-1, 1]. A larger value indicates more vivid image colors. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the operation of setting the effect property value is successful. true indicates that the setting is successful, and false indicates that the setting fails. |

**Examples**

```TypeScript
import { SceneResourceFactory, Scene, Effect, EffectParameters } from '@kit.ArkGraphics3D';

function setEffectProperty() {
  let scene: Promise<Scene> = Scene.load();
  scene.then(async (result: Scene | undefined) => {
    if (!result) {
      return;
    }
    let sceneFactory: SceneResourceFactory = result.getResourceFactory();
    // Effect ID, which is in the format of 'XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX', for example, 'e68a7f45-2d21-4a0d-9aef-7d9c825d3f12'.
    let params: EffectParameters = {effectId: "e68a7f45-2d21-4a0d-9aef-7d9c825d3f12"};
    let effect: Effect = await sceneFactory.createEffect(params);
    effect.setPropertyValue('exposure', 1);
  });
}
```

## effectId

```TypeScript
readonly effectId: string
```

Effect ID, which is in the format of 'XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX', for example, 'e68a7f45-2d21-4a0d-9aef-7d9c825d3f12'. It is used to create an effect.

**Type:** string

**Since:** 21

**System capability:** SystemCapability.ArkUi.Graphics3D

## enabled

```TypeScript
enabled: boolean
```

Enabled status of the effect. true if enabled, false otherwise.

**Type:** boolean

**Since:** 21

**System capability:** SystemCapability.ArkUi.Graphics3D

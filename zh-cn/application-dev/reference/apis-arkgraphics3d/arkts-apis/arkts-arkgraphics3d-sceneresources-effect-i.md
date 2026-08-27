# Effect

特效类型，继承自SceneResource。由createEffect接口获得。@extends SceneResource @interface Effect

**继承/实现关系：** Effect extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)

**起始版本：** 21

**系统能力：** SystemCapability.ArkUi.Graphics3D

## getPropertyValue

```TypeScript
getPropertyValue(propertyName: string): Object | null | undefined
```

获取特定特效属性的值。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propertyName | string | 是 | 特定特效属性的名称。目前支持的字符串为： -'exposure'：该属性表示图像的曝光度。 -'vibrance'：该属性表示图像的自然饱和度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object \| null \| undefined | 特效属性值。 若当前Effect类型下不存在与传入的propertyName匹配的属性，则获取属性值失败，返回null； 若propertyName对应的可选属性未设置，则返回undefined。 |

**示例**

```TypeScript
import { SceneResourceFactory, Scene, Effect, EffectParameters } from '@kit.ArkGraphics3D';

function getEffectProperty() {
  let scene: Promise<Scene> = Scene.load();
  scene.then(async (result: Scene | undefined) => {
    if (!result) {
      return;
    }
    let sceneFactory: SceneResourceFactory = result.getResourceFactory();
    // 特效ID，固定格式为'XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX'，比如'e68a7f45-2d21-4a0d-9aef-7d9c825d3f12'
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

设置特定特效属性的值。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propertyName | string | 是 | 特定特效属性的名称。目前支持的字符串为： -'exposure'：该属性表示图像的曝光度。 -'vibrance'：该属性表示图像的自然饱和度。 |
| value | Object \| undefined | 是 | 要设置的特效属性值。'exposure'：value实际类型为number，推荐取值范围[-5, 5]。取值越大，图像越亮。'vibrance'：value实际类型为number，推荐取值范围 [-1, 1]。取值越大，图像颜色越鲜艳。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回设置特效属性值操作是否成功。true表示设置成功，false表示设置失败。 |

**示例**

```TypeScript
import { SceneResourceFactory, Scene, Effect, EffectParameters } from '@kit.ArkGraphics3D';

function setEffectProperty() {
  let scene: Promise<Scene> = Scene.load();
  scene.then(async (result: Scene | undefined) => {
    if (!result) {
      return;
    }
    let sceneFactory: SceneResourceFactory = result.getResourceFactory();
    // 特效ID，固定格式为'XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX'，比如'e68a7f45-2d21-4a0d-9aef-7d9c825d3f12'
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

特效ID，固定格式为'XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX'，用于特效的创建，比如'e68a7f45-2d21-4a0d-9aef-7d9c825d3f12'。

**类型：** string

**起始版本：** 21

**系统能力：** SystemCapability.ArkUi.Graphics3D

## enabled

```TypeScript
enabled: boolean
```

特效打开状态。true表示开启特效，false表示关闭特效。

**类型：** boolean

**起始版本：** 21

**系统能力：** SystemCapability.ArkUi.Graphics3D

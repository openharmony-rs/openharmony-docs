# Effect

特效资源.

**继承/实现关系：** Effect extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md#SceneResource)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface Effect--><!--Device-unnamed-export interface Effect-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## getPropertyValue

```TypeScript
getPropertyValue(propertyName: string): Object | null | undefined
```

获取特定特效属性的值.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Effect-getPropertyValue(propertyName: string): Object | null | undefined--><!--Device-Effect-getPropertyValue(propertyName: string): Object | null | undefined-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propertyName | string | 是 | 特定属性的名称 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object | 特效属性值，如果"get"操作失败则返回null. |

## 示例

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

设置特定特效属性的值

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Effect-setPropertyValue(propertyName: string, value: Object | undefined): boolean--><!--Device-Effect-setPropertyValue(propertyName: string, value: Object | undefined): boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| propertyName | string | 是 | 特定属性的名称 |
| value | Object \| undefined | 是 | 要设置的属性值 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果"set"操作失败则返回false |

## 示例

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

特效的ID. 这是用于创建特效的ID.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Effect-readonly effectId: string--><!--Device-Effect-readonly effectId: string-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## enabled

```TypeScript
enabled: boolean
```

控制特效是否启用.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Effect-enabled: boolean--><!--Device-Effect-enabled: boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D


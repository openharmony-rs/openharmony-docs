# LayerMask

用于定义节点的图层掩码。

**起始版本：** 23

<!--Device-unnamed-export interface LayerMask--><!--Device-unnamed-export interface LayerMask-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## getEnabled

```TypeScript
getEnabled(index: int): boolean
```

获取指定图层下标图层掩码的使能状态。

**起始版本：** 23

<!--Device-LayerMask-getEnabled(index: int): boolean--><!--Device-LayerMask-getEnabled(index: int): boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 要使能图层的下标，值域为大于等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回特定下标的图层是否使能。true表示使用图层掩码，false表示不使用。 |

**示例**

```TypeScript
import { Scene, Node } from '@kit.ArkGraphics3D';

function layerMask(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result) {
      let node : Node | null = result.getNodeByPath("rootNode_");
      if (node) {
          // 获取掩码的使能状态，可根据业务需求对返回值进行后续处理
          let enabled: boolean = node.layerMask.getEnabled(1);
      }
    }
  }).catch((err: Error) => {
    console.error(`Failed to load scene. Message: ${err.message}`);
  });
}
```

## setEnabled

```TypeScript
setEnabled(index: int, enabled: boolean): void
```

将特定下标的图层掩码使能。

**起始版本：** 23

<!--Device-LayerMask-setEnabled(index: int, enabled: boolean): void--><!--Device-LayerMask-setEnabled(index: int, enabled: boolean): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 要使能图层的下标，值域为大于等于0的整数。 |
| enabled | boolean | 是 | 要设置的使能状态。true表示使用图层掩码，false表示不使用。 |

**示例**

```TypeScript
import { Scene, Node } from '@kit.ArkGraphics3D';

function layerMask(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result) {
      let node : Node | null = result.getNodeByPath("rootNode/Scene/");
      if (node) {
          // 设置掩码状态
          node.layerMask.setEnabled(1, true);
      }
    }
  }).catch((err: Error) => {
    console.error(`Failed to load scene. Message: ${err.message}`);
  });
}
```


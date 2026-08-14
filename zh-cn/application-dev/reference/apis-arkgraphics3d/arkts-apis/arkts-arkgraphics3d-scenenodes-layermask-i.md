# LayerMask

定义节点的图层掩码.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface LayerMask--><!--Device-unnamed-export interface LayerMask-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## getEnabled

```TypeScript
getEnabled(index: int): boolean
```

获取图层掩码是否启用.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-LayerMask-getEnabled(index: int): boolean--><!--Device-LayerMask-getEnabled(index: int): boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 图层掩码 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 图层掩码是否启用 |

## 示例

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
  }).catch((error: Error) => {
    console.error('Scene load failed:', error);
  });
}
```

## setEnabled

```TypeScript
setEnabled(index: int, enabled: boolean): void
```

设置图层掩码是否启用.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-LayerMask-setEnabled(index: int, enabled: boolean): void--><!--Device-LayerMask-setEnabled(index: int, enabled: boolean): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 图层掩码 |
| enabled | boolean | 是 | 图层掩码是否启用 |

## 示例

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
  }).catch((error: Error) => {
    console.error('Scene load failed:', error);
  });
}
```


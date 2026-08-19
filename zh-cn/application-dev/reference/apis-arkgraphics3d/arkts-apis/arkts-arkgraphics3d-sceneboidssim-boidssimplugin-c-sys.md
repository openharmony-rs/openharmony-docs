# BoidsSimPlugin（系统接口）

群组模拟插件，提供静态方法用于获取群组模拟世界。

**起始版本：** 26.0.0

<!--Device-unnamed-export declare class BoidsSimPlugin--><!--Device-unnamed-export declare class BoidsSimPlugin-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## getDefaultBoidsSimWorld

```TypeScript
static getDefaultBoidsSimWorld(scene: Scene): BoidsSimWorld | null
```

获取与指定场景关联的群组模拟世界实例。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BoidsSimPlugin-static getDefaultBoidsSimWorld(scene: Scene): BoidsSimWorld | null--><!--Device-BoidsSimPlugin-static getDefaultBoidsSimWorld(scene: Scene): BoidsSimWorld | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scene | [Scene](arkts-arkgraphics3d-scene-c.md) | 是 | 目标场景的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BoidsSimWorld](arkts-arkgraphics3d-sceneboidssim-boidssimworld-c-sys.md) | 返回群组模拟世界实例，若不存在则返回null。 |

**示例**

```TypeScript
import { BoidsSimPlugin, BoidsSimWorld, Scene, RenderContext } from '@kit.ArkGraphics3D';

async function initBoidsSim(): Promise<BoidsSimWorld | null> {
  const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
  if (!renderContext) {
    return null;
  }
  // 群组模拟插件UUID
  const BOIDS_SIM_PLUGIN_UUID: string = 'a1b2c3d4-e5f6-4a5b-8c9d-0e1f2a3b4c5d';
  // 加载群组模拟插件
  const loaded: boolean = await renderContext.loadPlugin(BOIDS_SIM_PLUGIN_UUID);
  if (!loaded) {
    return null;
  }
  // 创建空场景
  const scene: Scene = await Scene.load();
  // 获取群组模拟世界实例
  const world: BoidsSimWorld | null = BoidsSimPlugin.getDefaultBoidsSimWorld(scene);
  return world;
}
```


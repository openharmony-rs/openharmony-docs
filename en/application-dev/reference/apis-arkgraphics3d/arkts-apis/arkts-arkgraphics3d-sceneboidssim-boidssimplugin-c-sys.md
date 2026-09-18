# BoidsSimPlugin (System API)

Boids simulation plugin, providing static methods for obtaining the boids simulation world.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## getDefaultBoidsSimWorld

```TypeScript
static getDefaultBoidsSimWorld(scene: Scene): BoidsSimWorld | null
```

Gets the Boids simulation world instance associated with the specified scene.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scene | [Scene](arkts-arkgraphics3d-scene-c.md) | Yes | Object of the target scene. |

**Return value:**

| Type | Description |
| --- | --- |
| [BoidsSimWorld](arkts-arkgraphics3d-sceneboidssim-boidssimworld-c-sys.md) &#124; null | Returns the Boids simulation world instance, or null if it does not exist. |

**Examples**

```TypeScript
import { BoidsSimPlugin, BoidsSimWorld, Scene, RenderContext } from '@kit.ArkGraphics3D';

async function initBoidsSim(): Promise<BoidsSimWorld | null> {
  const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
  if (!renderContext) {
    return null;
  }
  // Boids simulation plugin UUID
  const BOIDS_SIM_PLUGIN_UUID: string = 'a1b2c3d4-e5f6-4a5b-8c9d-0e1f2a3b4c5d';
  // Load the Boids simulation plugin
  const loaded: boolean = await renderContext.loadPlugin(BOIDS_SIM_PLUGIN_UUID);
  if (!loaded) {
    return null;
  }
  // Create an empty scene
  const scene: Scene = await Scene.load();
  // Get the Boids simulation world instance
  const world: BoidsSimWorld | null = BoidsSimPlugin.getDefaultBoidsSimWorld(scene);
  return world;
}
```

# Animation

Animation resource, which inherits from SceneResource.

@extends SceneResource @interface Animation

**Inheritance/Implementation:** Animation extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## finish

```TypeScript
finish(): void
```

Finishes the playing of the animation and sets its progress of 1 (finished).

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

**Examples**

```TypeScript
import { Animation, Scene } from '@kit.ArkGraphics3D';

function finish(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result && result.animations && result.animations[0]) {
      let anim: Animation = result.animations[0];
      // Jump directly to the end of the animation and set the animation progress to 1.
      anim.finish();
    }
  });
}
```

## onFinished

```TypeScript
onFinished(callback: Callback<void>): void
```

Called when the animation playback is complete or the finish API is called.

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback function. The return value is null. |

**Examples**

```TypeScript
import { Animation, Scene } from '@kit.ArkGraphics3D';

function onFinished(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result && result.animations && result.animations[0]) {
      let anim: Animation = result.animations[0];
      // Register a callback.
      anim.onFinished(()=>{
        console.info("onFinished");  
      });
    }
  });
}
```

## onStarted

```TypeScript
onStarted(callback: Callback<void>): void
```

Called when the animation starts to play. The start operation is triggered by calling start or restart.

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback function. The return value is null. |

**Examples**

```TypeScript
import { Animation, Scene } from '@kit.ArkGraphics3D';

function onStarted(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result && result.animations && result.animations[0]) {
      let anim: Animation = result.animations[0];
      // Register a callback.
      anim.onStarted(()=>{
        console.info("onStarted");  
      });
    }
  });
}
```

## pause

```TypeScript
pause(): void
```

Pauses the animation. The animation remains in the current playing progress.

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

**Examples**

```TypeScript
import { Animation, Scene } from '@kit.ArkGraphics3D';

function pause(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result && result.animations && result.animations[0]) {
      let anim: Animation = result.animations[0];
      // Pause the animation.
      anim.pause();
    }
  });
}
```

## restart

```TypeScript
restart(): void
```

Plays the animation from the beginning.

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

**Examples**

```TypeScript
import { Animation, Scene } from '@kit.ArkGraphics3D';

function restart(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result && result.animations && result.animations[0]) {
      let anim: Animation = result.animations[0];
      // Restart the animation.
      anim.restart();
    }
  });
}
```

## seek

```TypeScript
seek(position: number): void
```

Plays the animation from the specified position.

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | number | Yes | Position from which the animation playback starts. The value range is [0, 1]. |

**Examples**

```TypeScript
import { Animation, Scene } from '@kit.ArkGraphics3D';

function seek(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result && result.animations && result.animations[0]) {
      let anim: Animation = result.animations[0];
      // Set the animation playback progress to 10%.
      anim.seek(0.1);
    }
  });
}
```

## start

```TypeScript
start(): void
```

Plays the animation based on the current progress.

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

**Examples**

```TypeScript
import { Animation, Scene } from '@kit.ArkGraphics3D';

function start(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result && result.animations && result.animations[0]) {
      let anim: Animation = result.animations[0];
      // Start the animation.
      anim.start();
    }
  });
}
```

## stop

```TypeScript
stop(): void
```

Stops playing the animation and sets its progress to 0 (not started).

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

**Examples**

```TypeScript
import { Animation, Scene } from '@kit.ArkGraphics3D';

function stop(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result && result.animations && result.animations[0]) {
      let anim: Animation = result.animations[0];
      // Stop playing the animation and set the animation progress to 0.
      anim.stop();
    }
  });
}
```

## duration

```TypeScript
readonly duration: number
```

Animation duration, in seconds. The value must be greater than or equal to 0.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## enabled

```TypeScript
enabled: boolean
```

Whether the animation is enabled. true if enabled, false otherwise.

**Type:** boolean

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## progress

```TypeScript
readonly progress: number
```

Playing progress of the animation. The value range is [0, 1].

**Type:** number

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## running

```TypeScript
readonly running: boolean
```

Whether the animation is running. true if running, false otherwise.

**Type:** boolean

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## speed

```TypeScript
speed?: number
```

Playback speed factor of the animation. The default value is 1.0, indicating that the animation is played at normal speed. If the value is negative, the animation plays in reverse.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

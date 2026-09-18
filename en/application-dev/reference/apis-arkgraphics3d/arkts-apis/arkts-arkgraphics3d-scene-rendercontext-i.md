# RenderContext

Defines the context of all rendering resources. Multiple scenes created within the same render context can share rendering resources.

@interface RenderContext

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## getRenderResourceFactory

```TypeScript
getRenderResourceFactory() : RenderResourceFactory
```

Obtains the rendering resource factory, which provides APIs for creating different rendering resources.

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

**Return value:**

| Type | Description |
| --- | --- |
| [RenderResourceFactory](arkts-arkgraphics3d-scene-renderresourcefactory-i.md) | RenderResourceFactory instance for creating rendering resources. |

**Examples**

```TypeScript
import { Scene, RenderContext, RenderResourceFactory } from '@kit.ArkGraphics3D';

function getRenderResourceFactory(): void {
  const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
  if (!renderContext) {
    console.error("Failed to get default render context");
    return;
  }
  const renderResourceFactory: RenderResourceFactory = renderContext.getRenderResourceFactory();
  console.info("TEST getRenderResourceFactory");
}
```

## loadPlugin

```TypeScript
loadPlugin(name: string): Promise<boolean>
```

Loads a plugin by name. The API locates and loads the corresponding plugin resource using the provided plugin name. It uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the plugin to load, which must be a system predefined or registered and available plugin name, and follow the naming conventions. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return a Boolean value, indicating whether the plugin is loaded. The value true means that the plugin is loaded, and false means the opposite. |

**Examples**

```TypeScript
import { Scene, RenderContext } from '@kit.ArkGraphics3D';

function loadPlugin(): Promise<boolean> {
  const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
  if (!renderContext) {
    console.error("Failed to get default render context");
    return Promise.reject(new Error("RenderContext is null"));
  }
  return renderContext.loadPlugin("pluginName");
}
```

## registerResourcePath

```TypeScript
registerResourcePath(protocol: string, uri: string): boolean
```

Registers the directory path and retrieval name for asset files, such as shaders. It allows the system to find and replace the path descriptions of related files within the shaders using the retrieval name. This ensures that the correct paths for assets and their associated files are located and loaded properly.

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| protocol | string | Yes | Path retrieval name to be registered, used as the prefix identifier for file paths associated internally in the shader. Must be a non-empty retrieval name that is not predefined or registered by the system. |
| uri | string | Yes | Directory path of the assets to be registered, which corresponds to the retrieval name. When the shader is loaded, the retrieval name prefix in the path is replaced with this directory. It must be the path to the folder containing the asset files. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Result indicating whether the registration is successful. true if successful, and false otherwise. The possible cause of a registration failure is that the retrieval name has been registered or an input parameter is invalid. |

**Examples**

```TypeScript
import { Scene, RenderContext } from '@kit.ArkGraphics3D';

function registerResourcePath(): void {
  // Create shader resources. The path and file name can be customized based on the specific project resources.
  Scene.load($rawfile("shaders/custom_shader/custom_material_sample.shader"))
    .then(() => {
      const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
      if (!renderContext) {
        console.error("Failed to get default render context");
        return false;
      }
      // Register the path retrieval name "myproto" and its corresponding asset path directory "OhosRawFile://shaders/custom_shader/".
      // When the shader references an associated file by retrieval name, for example, "myproto://textures/base.png",
      // the system replaces "myproto://" with "OhosRawFile://shaders/custom_shader/",
      // and the associated file is finally loaded from "OhosRawFile://shaders/custom_shader/textures/base.png".
      return renderContext.registerResourcePath("myproto", "OhosRawFile://shaders/custom_shader/");
    })
    .then(result => {
      if (result) {
        console.info("Succeeded in registering resource path");
      } else {
        console.error("Failed to register resource path");
      }
    });
}
```

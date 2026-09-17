# Scene(3D scene declarations)

## Summary

### Classes

| Name | Description |
| --- | --- |
| [PCFConfig](arkts-arkgraphics3d-scene-pcfconfig-c.md) | Configuration class for soft shadows using the Percentage-Closer Filtering (PCF) algorithm. |
| [Scene](arkts-arkgraphics3d-scene-c.md) | Describes a scene. |
| [SoftShadowConfig](arkts-arkgraphics3d-scene-softshadowconfig-c.md) | Abstract base class for soft shadow configuration. It defines the interface for controlling the shadow algorithm type and its parameters. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [Scene](arkts-arkgraphics3d-scene-c-sys.md) | Describes a scene. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [CameraParameters](arkts-arkgraphics3d-scene-cameraparameters-i.md) | Describes the camera parameters, which are used to define additional configuration options for camera initialization. |
| [EffectParameters](arkts-arkgraphics3d-scene-effectparameters-i.md) | Special effect parameter configuration, which is used to specify the special effect ID required for creating a special effect. It is used as the input parameter of the createEffect API to create a special effect object. |
| [RaycastParameters](arkts-arkgraphics3d-scene-raycastparameters-i.md) | Describes the configuration parameters for raycasting, defining the behavior of raycasting. |
| [RaycastResult](arkts-arkgraphics3d-scene-raycastresult-i.md) | Describes a result object from raycasting, containing details about the 3D object hit by the ray. |
| [RenderConfiguration](arkts-arkgraphics3d-scene-renderconfiguration-i.md) | Describes the rendering configuration. |
| [RenderContext](arkts-arkgraphics3d-scene-rendercontext-i.md) | Defines the context of all rendering resources. Multiple scenes created within the same render context can share rendering resources. |
| [RenderParameters](arkts-arkgraphics3d-scene-renderparameters-i.md) | Describes the rendering parameters. |
| [RenderResourceFactory](arkts-arkgraphics3d-scene-renderresourcefactory-i.md) | Creates rendering resources that can be shared in multiple scenes ([Scene](arkts-arkgraphics3d-scene-c.md)) that share RenderContext. |
| [SceneComponent](arkts-arkgraphics3d-scene-scenecomponent-i.md) | Represents a basic scene component, which is used to describe the component information of a scene node, including the component name and its properties. |
| [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | Describes the scene node parameters, which are used to provide the name and path in the scene node tree. |
| [SceneResourceFactory](arkts-arkgraphics3d-scene-sceneresourcefactory-i.md) | Provides APIs for creating resources, such as cameras and light sources, used in 3D scenes. This class inherits from RenderResourceFactory. |
| [SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md) | Describes the scene resource parameters (name and uri), which are used to provide the name of a scene resource and the path of the resource file required in the 3D scene. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [RenderResourceFactory](arkts-arkgraphics3d-scene-renderresourcefactory-i-sys.md) | Creates rendering resources that can be shared in multiple scenes ([Scene](arkts-arkgraphics3d-scene-c.md)) that share RenderContext. |
| [SceneLoadParams](arkts-arkgraphics3d-scene-sceneloadparams-i-sys.md) | Scene load parameters object, used to specify additional configuration options when loading 3D model resources. A typical use case is loading an embedded glb model from an MP4 container file. |
<!--DelEnd-->

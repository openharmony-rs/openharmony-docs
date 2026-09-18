# SceneResources(3D scene resource type declarations)

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [Animation](arkts-arkgraphics3d-sceneresources-animation-i.md) | Animation resource, which inherits from SceneResource. |
| [Blend](arkts-arkgraphics3d-sceneresources-blend-i.md) | Controls the transparency of materials. |
| [Effect](arkts-arkgraphics3d-sceneresources-effect-i.md) | Effect resource, which inherits from SceneResource. It is obtained from the createEffect API. |
| [Environment](arkts-arkgraphics3d-sceneresources-environment-i.md) | Environment resource, which inherits from SceneResource. |
| [Image](arkts-arkgraphics3d-sceneresources-image-i.md) | Image resource, which inherits from SceneResource. |
| [ImageStream](arkts-arkgraphics3d-sceneresources-imagestream-i.md) | ImageStream resource. |
| [Material](arkts-arkgraphics3d-sceneresources-material-i.md) | Material resource, which inherits from SceneResource. |
| [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md) | Defines the textures, property factors, and texture samplers used by a material. |
| [Mesh](arkts-arkgraphics3d-sceneresources-mesh-i.md) | Mesh resource, which inherits from SceneResource. |
| [MeshResource](arkts-arkgraphics3d-sceneresources-meshresource-i.md) | Mesh resource, which inherits from SceneResource. |
| [MetallicRoughnessMaterial](arkts-arkgraphics3d-sceneresources-metallicroughnessmaterial-i.md) | Material resource for creating realistic appearances, using the Metallic-Roughness model based on PBR. It simulates the surface lighting and reflection effects of different materials like metal and plastic by adjusting metallicity and roughness parameters. It inherits from Material. |
| [Morpher](arkts-arkgraphics3d-sceneresources-morpher-i.md) | Defines the deformation of 3D models by adjusting the weights of different deformation targets to create dynamic effects. |
| [OcclusionMaterial](arkts-arkgraphics3d-sceneresources-occlusionmaterial-i.md) | Occlusion material: occludes other objects in the scene but does not occlude the environment. It is inherited from Material. |
| [RenderSort](arkts-arkgraphics3d-sceneresources-rendersort-i.md) | Describes the order in which materials are rendered, controlling the sequence of drawing in the rendering pipeline. |
| [Sampler](arkts-arkgraphics3d-sceneresources-sampler-i.md) | Describes the sampling modes used during texture sampling. |
| [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md) | Describes a resource in a scene. |
| [Shader](arkts-arkgraphics3d-sceneresources-shader-i.md) | Shader resource, which inherits from SceneResource. |
| [ShaderMaterial](arkts-arkgraphics3d-sceneresources-shadermaterial-i.md) | Shader material, which inherits from Material. |
| [SubMesh](arkts-arkgraphics3d-sceneresources-submesh-i.md) | Sub-mesh resource. |
| [UnlitMaterial](arkts-arkgraphics3d-sceneresources-unlitmaterial-i.md) | Material that is not affected by lighting. The shading value of the material is related only to the base color and is irrelevant to lighting conditions. It inherits from Material. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [UnlitShadowAlphaMaterial](arkts-arkgraphics3d-sceneresources-unlitshadowalphamaterial-i-sys.md) | This material inherits from Material and draws only the surface shadows. When the Blend property is enabled, the material can be blended with the background to simulate transparency. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [CullMode](arkts-arkgraphics3d-sceneresources-cullmode-e.md) | Enumerates the culling modes of PBR materials. You can improve rendering performance and visual quality by determining whether the front or back faces of objects are culled. |
| [EnvironmentBackgroundType](arkts-arkgraphics3d-sceneresources-environmentbackgroundtype-e.md) | Enumerates the environment background types, which are used to define how the background of a scene is presented. @enum { int } |
| [MaterialType](arkts-arkgraphics3d-sceneresources-materialtype-e.md) | Enumerates the material types in a scene. The material type defines how materials in a scene are rendered. |
| [PolygonMode](arkts-arkgraphics3d-sceneresources-polygonmode-e.md) | Enumerates the polygon drawing mode. |
| [SamplerAddressMode](arkts-arkgraphics3d-sceneresources-sampleraddressmode-e.md) | Enumerates the sampler addressing modes, which are used to control how texture coordinates are handled when they go beyond the [0, 1] range. |
| [SamplerFilter](arkts-arkgraphics3d-sceneresources-samplerfilter-e.md) | Enumerates the filtering modes of a sampler. The filtering mode determines the interpolation method used when sampling textures, controlling how final pixel colors are calculated during texture scaling or deformation. |
| [SceneResourceType](arkts-arkgraphics3d-sceneresources-sceneresourcetype-e.md) | Enumerates the scene resource types, which are used to classify resources in a scene. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [MaterialType](arkts-arkgraphics3d-sceneresources-materialtype-e-sys.md) | Enumerates the material types in a scene. The material type defines how materials in a scene are rendered. |
<!--DelEnd-->

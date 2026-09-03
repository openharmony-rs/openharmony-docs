# @ohos.graphics.scene (ArkGraphics 3D)

<!--Kit: ArkGraphics 3D-->
<!--Subsystem: Graphics-->
<!--Owner: @jason_stark-->
<!--Designer: @zdustc-->
<!--Tester: @zhangyue283-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=9bb5a62ecd61b6f45356eb97818a280b50c70dac translatedAt=2026-08-20T12:27:04.415Z pushedAt=2026-08-21T06:22:33.975Z -->

The @ohos.graphics.scene module organizes the APIs of 3D development-related modules together for developers to use.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Scene

[Scene](js-apis-inner-scene.md): ArkGraphics 3D basic module, which provides common data types such as [SceneResourceParameters](js-apis-inner-scene.md#sceneresourceparameters) and [SceneNodeParameters](js-apis-inner-scene.md#scenenodeparameters). It also provides basic methods such as glTF model loading, scene creation, and resource creation.

**System capability**: SystemCapability.ArkUi.Graphics3D

## SceneNode

[SceneNode](js-apis-inner-scene-nodes.md): A 3D scene is organized in a tree structure. You can change the 3D scene by operating node properties and the node tree structure. This module provides the types and operation methods of scene resource nodes in ArkGraphics 3D.

**System capability**: SystemCapability.ArkUi.Graphics3D

## SceneType

[SceneType](js-apis-inner-scene-types.md): This module provides the data types in ArkGraphics 3D, including vectors and quaternions.

**System capability**: SystemCapability.ArkUi.Graphics3D

## SceneResources

[SceneResources](js-apis-inner-scene-resources.md): This module provides the common basic resource types in ArkGraphics 3D, including materials, images, and shaders.

**System capability**: SystemCapability.ArkUi.Graphics3D

## ScenePostProcessSettings

[ScenePostProcessSettings](js-apis-inner-scene-post-process-settings.md): This module provides image post-processing methods such as tone mapping in ArkGraphics 3D.

**System capability**: SystemCapability.ArkUi.Graphics3D
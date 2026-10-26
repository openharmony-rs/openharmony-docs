# SceneBoidsSim

This module provides types and operation methods for Boids simulation animation in ArkGraphics 3D.
 Boids simulation animation is a computer animation method that drives individuals in a group through rules such as separation,
 alignment, and cohesion, making them exhibit movement characteristics similar to flocks of birds or schools of fish in nature.

> **NOTE**
 >
 > Before using the APIs of this module, you need to load the Boids simulation plugin [BoidsSimPlugin](arkts-arkgraphics3d-sceneboidssim-boidssimplugin-c-sys.md)
 > through [RenderContext.loadPlugin](arkts-arkgraphics3d-scene-rendercontext-i.md#loadplugin).



## Summary

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [BoidsSimPlugin](arkts-arkgraphics3d-sceneboidssim-boidssimplugin-c-sys.md) | Boids simulation plugin, providing static methods for obtaining the boids simulation world. |
| [BoidsSimWorld](arkts-arkgraphics3d-sceneboidssim-boidssimworld-c-sys.md) | The Boids simulation world object, used to manage the lifecycle and components of the Boids simulation. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [BoidsSimGravityParameters](arkts-arkgraphics3d-sceneboidssim-boidssimgravityparameters-i-sys.md) | Attraction field parameters, used to configure the attraction field in the scene. |
| [BoidsSimParameters](arkts-arkgraphics3d-sceneboidssim-boidssimparameters-i-sys.md) | Boids simulation parameters used to configure the behavioral attributes of each individual. |
| [BoidsSimRepulsionParameters](arkts-arkgraphics3d-sceneboidssim-boidssimrepulsionparameters-i-sys.md) | Repulsion field parameters, used to configure the repulsion field in the scene. |
<!--DelEnd-->

# SceneBoidsSim

本模块提供ArkGraphics 3D中群组模拟动画的类型及操作方法。
 群组模拟动画是通过分离、对齐、凝聚等规则驱动群体中的个体，使其展现出类似自然界中鸟群、鱼群运动特征的计算机动画方法。

> **说明：**
 >
 > 使用本模块的接口前，
 > 需先通过[RenderContext.loadPlugin](arkts-arkgraphics3d-scene-rendercontext-i.md#loadplugin)加载群组模拟插件[BoidsSimPlugin](arkts-arkgraphics3d-sceneboidssim-boidssimplugin-c-sys.md)。



## 汇总

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BoidsSimPlugin](arkts-arkgraphics3d-sceneboidssim-boidssimplugin-c-sys.md) | 群组模拟插件，提供静态方法用于获取群组模拟世界。 |
| [BoidsSimWorld](arkts-arkgraphics3d-sceneboidssim-boidssimworld-c-sys.md) | 群组模拟世界对象，用于管理群组模拟的生命周期及组件。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [BoidsSimGravityParameters](arkts-arkgraphics3d-sceneboidssim-boidssimgravityparameters-i-sys.md) | 引力场参数，用于配置场景中的引力场。 |
| [BoidsSimParameters](arkts-arkgraphics3d-sceneboidssim-boidssimparameters-i-sys.md) | 群组模拟参数，用于配置每个个体的行为属性。 |
| [BoidsSimRepulsionParameters](arkts-arkgraphics3d-sceneboidssim-boidssimrepulsionparameters-i-sys.md) | 斥力场参数，用于配置场景中的斥力场。 |
<!--DelEnd-->

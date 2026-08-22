# 沉浸光感开发指导
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @H-xinwei-->
<!--Designer: @zhanghaibo0-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

本文按照接入流程介绍如何为应用接入沉浸光感，内容分为以下两个部分：

- [开启沉浸光感](arkts-immersive-light-sense-enable.md)：介绍应用级和组件级两种接入方式、如何通过应用级配置开关开启沉浸光感，以及如何关闭默认开启的组件沉浸式系统材质。
- [定制沉浸式系统材质效果](arkts-immersive-light-sense-common-capability.md)：介绍自动反色、材质赋色、交互反馈、自定义阴影等跨场景通用能力。

## 注意事项

- **属性冲突**：不建议为设置了沉浸式系统材质的组件同时设置背景色、背景模糊、阴影和边框样式。不透明背景色或背景模糊样式会覆盖在材质层之上，导致材质效果被遮挡；DEFAULT模式下主动设置这些属性还会导致沉浸式系统材质不默认开启。相关问题及解决措施请参见[沉浸光感常见问题](arkts-immersive-light-sense-faq.md)。
- **渲染区域与显示层级**：材质渲染区域由组件布局区域决定，可能与组件可视区域不一致；材质效果作用于背板层（组件背景所在的绘制层），无法绘制在内容层（组件内容与自绘制内容所在的绘制层，位于背板层之上），自绘制组件的背景色会遮盖材质效果。详见[材质渲染区域与组件可视区域不一致](arkts-immersive-light-sense-faq.md#材质渲染区域与组件可视区域不一致)和[材质效果的显示层级问题](arkts-immersive-light-sense-faq.md#材质效果的显示层级问题)。
- **功耗优化**：沉浸式系统材质由材质滤镜、折射、高光、阴影等多层效果叠加而成，应控制使用面积与层数、不应固定显示在视频/动图/动画等变化的内容之上，详见[沉浸光感功耗优化](arkts-immersive-light-sense-constraints.md)。

# ArkGraphics 2D（方舟2D图形服务）

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @oh_wangxk; @goumiao; @hangmengxin-->
<!--Designer: @liumingxiang; @wangyanglan-->
<!--Tester: @yhl0101; @nobuggers-->
<!--Adviser: @ge-yafang-->

- [ArkGraphics 2D简介](arkgraphics2D-introduction.md)
- 使用可变帧率能力定制不同内容的绘制帧率<!--displaysync-->
  - [可变帧率简介](displaysync-overview.md)
  - [请求动画绘制帧率](displaysync-animation.md)
  - [请求UI绘制帧率](displaysync-ui.md)
  - [请求自绘制内容绘制帧率](displaysync-xcomponent.md)
  - [NativeDisplaySoloist开发指导 (C/C++)](displaysoloist-native-guidelines.md)
- [过度绘制调试使用指导](overdraw-dfx-guidelines.md)
- 图形绘制与显示<!--graphic-drawing-->
  - [图形绘制与显示开发概述](graphic-drawing-overview.md)
  - 画布的获取与绘制结果的显示<!--canvas-get-result-draw-->
    - [画布的获取与绘制结果的显示（ArkTS）](canvas-get-result-draw-arkts.md)
    - [画布的获取与绘制结果的显示（C/C++）](canvas-get-result-draw-c.md)
  - 画布操作及状态<!--canvas-operation-state-->
    - [画布操作及状态处理（ArkTS）](canvas-operation-state-arkts.md)
    - [画布操作及状态处理（C/C++）](canvas-operation-state-c.md)
  - 绘制效果<!--drawing-effect-->
    - [绘制效果概述](drawing-effect-overview.md)
    - [基础绘制效果（ArkTS）](basic-drawing-effect-arkts.md)
    - [复杂绘制效果（ArkTS）](complex-drawing-effect-arkts.md)
    - [基础绘制效果（C/C++）](basic-drawing-effect-c.md)
    - [复杂绘制效果（C/C++）](complex-drawing-effect-c.md)
  - 图元绘制<!--primitive-drawing-->
    - [图元绘制概述](primitive-drawing-overview.md)
    - [几何形状绘制（ArkTS）](geometric-shape-drawing-arkts.md)
    - [图片绘制（ArkTS）](pixelmap-drawing-arkts.md)
    - [字块绘制（ArkTS）](textblock-drawing-arkts.md)
    - [几何形状绘制（C/C++）](geometric-shape-drawing-c.md)
    - [图片绘制（C/C++）](pixelmap-drawing-c.md)
    - [字块绘制（C/C++）](textblock-drawing-c.md)
- 文本<!--text-->
    - [文本开发概述](text-overview.md)
    - 字体管理<!--font-manager-->
      - [使用主题字体（ArkTS）](theme-font-arkts.md)
      - [自定义字体的注册和使用（ArkTS）](custom-font-arkts.md)
      - [系统字体的信息获取和使用（ArkTS）](system-font-arkts.md)
      - [使用主题字体（C/C++）](theme-font-c.md)
      - [自定义字体的注册和使用（C/C++）](custom-font-c.md)
      - [系统字体的信息获取和使用（C/C++）](system-font-c.md)
    - 文本测量<!--text-measure-->
      - [文本测量（ArkTS）](text-measure-arkts.md)
      - [文本测量（C/C++）](text-measure-c.md)
    - 文本绘制与显示<!--draw-text-display-->
      - [简单文本绘制与显示（ArkTS）](simple-text-arkts.md)
      - [复杂文本绘制与显示（ArkTS）](complex-text-arkts.md)
      - [简单文本绘制与显示（C/C++）](simple-text-c.md)
      - [复杂文本绘制与显示（C/C++）](complex-text-c.md)
- [NativeBuffer开发指导 (C/C++)](native-buffer-guidelines.md)
- [NativeImage开发指导 (C/C++)](native-image-guidelines.md)
- [NativeVsync开发指导 (C/C++)](native-vsync-guidelines.md)
- [NativeWindow开发指导 (C/C++)](native-window-guidelines.md)
- [GPU/CPU内存访问同步操作开发指南 (C/C++)](native-fence-guidelines.md)
- [图形开发术语](graphic-term.md)

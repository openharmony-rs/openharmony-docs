# Animation Overview
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->


The UI contains various components (such as time and wallpaper) that users interact with on their devices. Attributes are APIs used to control the behavior of components. For example, you can adjust the location of a component on the screen through the location attribute.


In most cases, changing attribute values triggers corresponding UI updates. Animations introduce smooth transitions during these updates, preventing abrupt changes that cause visual discontinuity.

![en-us_image_20230822](figures/en-us_image_20230822.gif)

Animations enable you to:

- Create smooth transitions between states.
- Provide visual feedback to give users a sense of control.
- Inform users of the system status, for example, the loading progress, to make them less stressed while waiting.
- Show users how to interact with the UI.


Smart use of animations can breathe life into the process of interaction. The frequently seen animations include those that play under device startup, application startup or exit, and pull-down-to-access-the-control-panel scenarios. These animations provide effective user feedback and direct the user attention to where it should be focused.

ArkUI provides a wide range of animation APIs (such as [property animation](arkts-attribute-animation-overview.md) and [transition animation](arkts-transition-overview.md)), which you can leverage to cause attributes to gradually change from the start value to the end value based on the specified settings. Although attribute values change discretely rather than continuously, the human eye's persistence of vision creates the illusion of smooth animation. Each UI change represents an animation frame, corresponding to a screen refresh. The frame rate, which indicates frames per second (fps), critically affects animation smoothness. Higher frame rates create smoother animations. In ArkUI, animation parameters include animation duration, animation curve, and more. [Traditional curves](arkts-traditional-curve.md) in particular influence how attribute values change over time. For example, with a linear animation curve, the attribute changes from the start value to the end value at a constant speed over the given duration. If the attribute changes too fast or too slow, the visual experience may suffer. Therefore, animation parameters, especially animation curves, must be well designed and adjusted to suit specific use cases.


Animation APIs drive attribute values to continuously transit from one state to another according to the rule determined by the animation parameters, and thereby generate a continuous visual effect on the UI. This walkthrough demonstrates the steps and considerations for creating a compelling animation experience.

- [Property animation](arkts-attribute-animation-overview.md): It is the most basic animation type. It drives property changes frame by frame based on animation parameters to create an animation on a frame-by-frame basis. Except for custom property animations, the system handles the animation process with no application-side awareness of the intermediate states.

- [Transition animation](arkts-transition-overview.md): It handles component appearance and disappearance transitions. To maintain animation consistency, some animation curves have been built in and cannot be customized.
  - Whenever possible, avoid [UIAbility](../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) redirection in your application. A UIAbility is a task in effect and is individually displayed on the recent tasks screen. Redirection between UIAbilities is redirection between tasks. In the typical scenario of viewing large images in an application, if you call the gallery UIAbility from the application to open large images, then the gallery UIAbility will appear on the recent tasks screen. This is not recommended. A more recommended practice is as follows: Build a large image component in the application and invoke that component through modal transition. In this way, the entire animation can be completed in one UIAbility.
  - To implement navigation, use the [Navigation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md) component instead of the page+router mode. The latter causes page separation, which complicates transition effect synchronization and hinders one-time development for multi-device deployment.

- [Particle animation](arkts-particle-animation.md): Enhance visual effects with a multitude of particles based on certain principles.

- [Component animation](arkts-component-animation.md): Components provide default animations (such as the scroll animation of the [List](../reference/apis-arkui/arkui-ts/ts-container-list.md) component) with some supporting customization.

- [Animation curve](arkts-traditional-curve.md): You can use traditional and spring curves to control property value changes, creating engaging animation effects.

- [Animation smoothing](arkts-animation-smoothing.md): Ensure natural transitions between animations and between gestures and animations.

- [Animation effect](arkts-blur-effect.md): Enhance animations with blur, shadow, color gradient, and other sophisticated effects.

- [Frame animation](arkts-animator.md): The system provides interpolated values during the animation process, requiring you to manually update property values each frame to generate animation effects. Compared with the property animation, this type of animation offers the advantage of pause/resume animation control, but with inferior performance.
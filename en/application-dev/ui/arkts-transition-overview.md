# Transition Animation Overview
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->


Transition animations are used to apply animation effects to components that are about to appear or disappear. Components that are always displayed should use the property animation (arkts-attribute-animation-overview.md). Transition animations aim to simplify the management of disappearing components. If you use property animations to implement component transitions, you need to manually delete the component nodes in the animation completion callback. In addition, the nodes that have been deleted before the animation ends may appear again. Therefore, you need to add the logic for checking the node status in the callback.


There are several types of transition animations:

- [Enter/Exit transition](arkts-enter-exit-transition.md): used on appearing and disappearing components. It is a basic type of transition.

- [Modal transition](arkts-modal-transition.md): achieved by a modal – a view that appears on top of the current view while the current view remains. The dialog box is a typical type of modal.

- [Shared element transition](arkts-shared-element-transition.md): achieved by animating the size and position between styles of the same or similar elements during page switching.

- [Rotation transition animation](arkts-rotation-transition-animation.md): designed to create seamless visual transitions when the screen display orientation changes. There are two approaches to choose from: [rotation transition animation with layout switching](arkts-rotation-transition-animation.md#rotation-transition-animation-with-layout-switching) and [rotation transition animation with opacity changing](arkts-rotation-transition-animation.md#rotation-transition-animation-with-opacity-changing).

- [Page transition animation](arkts-page-transition-animation.md): achieved by customizing the page transition effects through the **pageTransition** API. To achieve a better transition effect, you are advised to use the [navigation transition](./arkts-navigation-navigation.md) and [modal transition](arkts-modal-transition.md).

- [Navigation transition](./arkts-navigation-navigation.md): The route transition mode of the page corresponds to the animation effect when one page disappears and another page appears. For example, the level-1 menu of the setting application is switched to the level-2 page.

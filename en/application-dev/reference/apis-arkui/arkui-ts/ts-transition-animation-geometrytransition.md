# Implicit Shared Element Transition (geometryTransition)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @chensiyi_CE-->
<!--Tester: @lxl007-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=39ca26def5c22dc659f3dc0b76ef62a29421e77a translatedAt=2026-09-01T11:55:21.202Z -->

Provides a smooth, seamless context transition during view switching. The generic transition mechanism provides transition effects such as opacity and scale. By arranging the frame and position of the bound in/coming and out/leaving components (in refers to the new view, and out refers to the old view), geometryTransition establishes a spatial relationship between the originally independent transition animations, guiding the visual focus from the old view position to the new view position. The in/coming and out/leaving components must be used together with transition to ensure that the leaving component is not immediately destroyed and to provide the transition effect. If transition is not used, the out/leaving component will be destroyed immediately upon leaving, and the shared element transition animation may not be displayed properly.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7 and effective since API version 10. Updates will be marked with a superscript to indicate their earliest API version.
>
> [geometryTransition](ts-transition-animation-geometrytransition.md) must be used together with [animateTo](../arkts-apis-uicontext-uicontext.md#animateto) to produce the animation effect. The animation duration and curve follow the settings in [animateTo](../arkts-apis-uicontext-uicontext.md#animateto). The components participating in the transition must have [transition](ts-transition-animation-component.md#transition) set to ensure that they are not immediately destroyed when leaving, so that the shared element transition animation can play properly. The [animation](ts-animatorproperty.md) animation is not supported.

## geometryTransition

geometryTransition(id: string): T

In-Component Implicit Shared Element Transition. It must be used together with [animateTo](../arkts-apis-uicontext-uicontext.md#animateto) to produce the animation effect. The animation duration and curve follow the settings in [animateTo](../arkts-apis-uicontext-uicontext.md#animateto). The [animation](ts-animatorproperty.md) animation is not supported. geometryTransition synchronizes the rounded corners, but only at the location where geometryTransition is bound; it does not operate on the borderRadius of the child components inside the container.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 11.

**Parameters**

| Name | Type                | Mandatory| Description                                                    |
| ------- | ------------------------ | ---- | ------------------------------------------------------------ |
| id      | string                   | Yes   | Used to set the binding relationship. Setting id to an empty string clears the binding relationship to avoid participating in the shared behavior. The id can be changed to re-establish the binding relationship. The same id can be bound to only two components, which serve as two different roles: in (new view) and out (old view). Multiple components cannot be bound to the same id. |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component, used for chained calls. |

## geometryTransition<sup>11+</sup>

geometryTransition(id: string, options?: GeometryTransitionOptions): T

Implements an implicit shared element transition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                | Mandatory| Description                                                    |
| ------- | ------------------------ | ---- | ------------------------------------------------------------ |
| id      | string                   | Yes   | Used to set the binding relationship. Setting id to an empty string clears the binding relationship to avoid participating in the shared behavior. id can be changed to re-establish the binding relationship. The same id can be bound to only two components, which serve as two different role types: in (new view) and out (old view). Multiple components cannot be bound to the same id. |
| options | [GeometryTransitionOptions](#geometrytransitionoptions11) | No   | Parameters of the in-component implicit shared element transition animation. It must be used together with [animateTo](../arkts-apis-uicontext-uicontext.md#animateto) to produce an animation effect.<br>The default value is { follow: false }.                                    |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component, used for chained calls. |

## GeometryTransitionOptions<sup>11+</sup>

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description                                                  |
| ------ | -------- | -------- | ---- | ------------------------------------------------------------ |
| follow | boolean  | No | Yes   | Used only in the if paradigm to mark whether a component that always remains in the component tree follows the shared element transition. The if paradigm is a declarative UI development pattern that uses an if conditional statement in the build() method to control the visibility of components. The value true means that the component follows the shared element transition, and false means that it does not follow the shared element transition.<br>Default value: false |

## Example

```ts
// xxx.ets
@Entry
@Component
struct Index {
  @State isShow: boolean = false;

  build() {
    Stack({ alignContent: Alignment.Center }) {
      if (this.isShow) {
        // Customize the image resource path as needed.
        Image($r('app.media.pic'))
          .autoResize(false)
          .clip(true)
          .width(300)
          .height(400)
          .offset({ y: 100 })
          .geometryTransition('picture', { follow: false })
          .transition(TransitionEffect.OPACITY)
      } else {
        // geometryTransition is bound to a container. Therefore, a relative layout must be configured for the child components of the container.
        // The multiple levels of containers here are used to demonstrate passing of relative layout constraints.
        Column() {
          Column() {
            // Customize the image resource path as needed.
            Image($r('app.media.icon'))
              .width('100%').height('100%')
          }.width('100%').height('100%')
        }
        .width(80)
        .height(80)
        // geometryTransition synchronizes corner radius settings, but only for the bound component, which is the container in this example.
        // In other words, corner radius settings of the container are synchronized, and those of the child components are not.
        .borderRadius(20)
        .clip(true)
        .geometryTransition('picture')
        // transition ensures that the component is not destructed immediately when it exits. You can customize the transition effect.
        .transition(TransitionEffect.OPACITY)
      }
    }
    .onClick(() => {
      this.getUIContext().animateTo({ duration: 1000 }, () => {
        this.isShow = !this.isShow;
      });
    })
  }
}
```

![geometrytransition](figures/geometrytransition.gif)

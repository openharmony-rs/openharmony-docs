# Component Extension Overview
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=b4c16a3481f0a0bf24de133bf760018019cda10c translatedAt=2026-10-28T03:57:33.349Z pushedAt=2026-10-28T07:37:43.175Z nl=1 -->

ArkUI uses the @Builder decorator to provide developers with a code simplification solution. This decorator simplifies the UI development process through modular encapsulation, and derives the @BuilderParam decorator, @LocalBuilder decorator, wrapBuilder mechanism, and mutableBuilder mechanism, forming a reusable UI structure system.

> **NOTE**
>
> The @Builder decorator is the cornerstone of the @BuilderParam decorator, @LocalBuilder decorator, and wrapBuilder mechanism.

## @Builder Decorator

[@Builder decorator](./arkts-builder.md) is designed to build a modular and reusable UI structure. It cannot define state variables or call component lifecycle methods. It can only exchange data with the invoker through parameters.

## @LocalBuilder Decorator

When using @Builder for inter-component data transfer, note that component hierarchy relationships may conflict with state management parent-child relationships. To solve this problem, the framework provides the [@LocalBuilder decorator](./arkts-localBuilder.md).

## @BuilderParam Decorator

When multiple scenarios share the same @Builder function, you can use the [@BuilderParam decorator](./arkts-builderparam.md) to extend features for specific scenarios (similar to the slot placeholder mechanism). This decorator is used to receive and encapsulate the @Builder function.

## wrapBuilder Mechanism

When multiple global @Builder functions with different UI structures exist on a page, the maintenance cost is high. The framework provides the [wrapBuilder](./arkts-wrapBuilder.md) mechanism to simplify code maintenance.

## mutableBuilder Mechanism

Currently, [wrapBuilder](./arkts-wrapBuilder.md) does not support secondary assignment, that is, dynamically switching \@Builder does not cause the UI to change. The framework provides [mutableBuilder](./arkts-mutableBuilder.md) to support dynamic switching of \@Builder.

## @Styles Decorator

[@Styles](./arkts-style.md) is used to define component reuse styles. Multiple common styles can be extracted into one method and directly called at the component declaration position. You can use the \@Styles decorator to quickly define and reuse custom styles.

## @Extend Decorator

[@Extend](./arkts-extend.md) is used to define the component reuse style. It can extract the private attributes and private event settings of a specified component into a method and directly call the method in the component declaration position. You can use the \@Extend decorator to quickly define and reuse the custom style of a specified component.

## stateStyles Mechanism

[stateStyles](./arkts-statestyles.md) You can quickly set different styles based on the internal status of the component.

## @AnimatableExtend Decorator

The [@AnimatableExtend](./arkts-animatable-extend.md) decorator is used to customize the animated attribute method. In this attribute method, you can modify the non-animatable properties. During animation execution, frame-by-frame callbacks are executed to change the values of non-animatable properties to allow them to achieve animation effects. Additionally, you can implement frame-by-frame layout effects by changing the values of animatable properties in the per-frame callback function.
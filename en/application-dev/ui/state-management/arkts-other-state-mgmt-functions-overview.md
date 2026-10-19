# Overview of Other State Management Features
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=c4eacd7749f17b808b6e998528fa58a7554f7518 translatedAt=2026-09-21T11:28:16.870Z pushedAt=2026-09-23T09:15:53.745Z -->

In addition to component-level and application-level state management, ArkTS also provides \@Watch, the $$ operator, \@Track, and custom component freezing to give you more capabilities:

- [\@Watch decorator](arkts-watch.md): listens for the changes of state variables.

- [$$ operator](arkts-two-way-sync.md): creates two-way binding between TypeScript variables and built-in component states.

- [\@Track decorator](arkts-track.md): enables property-level updates for class objects. When a property decorated with \@Track changes, only the UI associated with that property is updated.

- [Component freezing](arkts-custom-components-freeze.md): suspends inactive components' state responsiveness.
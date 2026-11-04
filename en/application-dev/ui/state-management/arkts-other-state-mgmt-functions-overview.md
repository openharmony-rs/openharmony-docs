# Overview of Other State Management Features
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=8917fa9a06fba0322d5ee6f97bf1bc1616272188 translatedAt=2026-11-04T05:34:05.954Z pushedAt=2026-11-04T07:27:15.234Z nl=1 -->

In addition to component-level and application-level state management, ArkTS also provides \@Watch, the $$ operator, \@Track, and custom component freezing to give you more capabilities:

- [\@Watch decorator](arkts-watch.md): listens for the changes of state variables.

- [$$ operator](arkts-two-way-sync.md): creates two-way binding between TypeScript variables and built-in component states.

- [\@Track decorator](arkts-track.md): enables property-level updates for class objects. When a property decorated with \@Track changes, only the UI associated with that property is updated.

- [Component freezing](arkts-custom-components-freeze.md): suspends inactive components' state responsiveness.
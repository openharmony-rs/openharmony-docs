# Module Description

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=b604c666043da7d4010df0a994db7ed1901c2f5a translatedAt=2026-11-04T10:22:44.358Z pushedAt=2026-11-04T10:29:08.132Z nl=1 -->

When drawing UI elements, if ArkUI components cannot meet the requirements for custom graphics, developers can use the Drawing module to implement flexible custom drawing effects. The Drawing module provides basic graphics drawing capabilities, including drawing rectangles, circles, points, lines, custom Path, and fonts.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This module uses the physical pixel unit, px.
>
> - The module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

## Modules to Import

```ts
import { drawing } from '@kit.ArkGraphics2D';
```
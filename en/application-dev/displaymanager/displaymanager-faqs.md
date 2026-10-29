# Display Development FAQs
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @wulong158-->
<!--Tester: @LiTongguan2026-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=494f31a35d1b25179fe202754d9ee44d527d8ab6 translatedAt=2026-10-13T12:49:12.176Z pushedAt=2026-10-15T10:38:11.239Z -->

<!--RP1-->
<!--RP1End-->

## What Does the Orientation Value 4 of the Display Object Mean for a Virtual Screen?

**Symptom**

After obtaining the **Display** object of a virtual screen, the orientation value is **4**, which is not within the [Orientation](../reference/apis-arkui/js-apis-display.md#orientation10) enumeration range.

**Possible Causes**

A virtual screen has no physical screen and cannot perceive the screen orientation. If the screen orientation is not actively set, the system cannot return any value in the **Orientation** enumeration. In this case, the orientation property returns **4** to indicate that the screen orientation is unknown.
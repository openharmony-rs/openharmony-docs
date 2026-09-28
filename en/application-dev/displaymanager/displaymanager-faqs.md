# Display Development FAQs
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @wulong158-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=1901db9be343b0a2f2f315e66f0588f9bda6dfc5 translatedAt=2026-09-14T09:13:25.836Z pushedAt=2026-09-15T13:10:13.320Z -->

<!--RP1-->
<!--RP1End-->

## What Does the Orientation Value 4 of the Display Object Mean for a Virtual Screen?

**Symptom**

After obtaining the **Display** object of a virtual screen, the orientation value is **4**, which is not within the [Orientation](../reference/apis-arkui/js-apis-display.md#orientation10) enumeration range.

**Possible Causes**

A virtual screen has no physical screen and cannot perceive the screen orientation. If the screen orientation is not actively set, the system cannot return any value in the **Orientation** enumeration. In this case, the orientation property returns **4** to indicate that the screen orientation is unknown.
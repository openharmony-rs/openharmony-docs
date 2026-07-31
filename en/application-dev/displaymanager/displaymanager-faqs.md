# Display Development FAQs
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @logn; @wulong158-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=b21bd82a68f5cb2fefefde92a7afef87223beafc translatedAt=2026-07-09T08:20:45.072Z pushedAt=2026-07-09T10:42:12.501Z -->

<!--RP1-->
<!--RP1End-->

## What Does the Orientation Value 4 of the Display Object Mean for a Virtual Screen?

**Symptom**

After obtaining the **Display** object of a virtual screen, the orientation value is **4**, which is not within the [Orientation](../reference/apis-arkui/js-apis-display.md#orientation10) enumeration range.

**Possible Causes**

A virtual screen has no physical screen and cannot perceive the screen orientation. If the screen orientation is not actively set, the system cannot return any value in the **Orientation** enumeration. In this case, the orientation property returns **4** to indicate that the screen orientation is unknown.
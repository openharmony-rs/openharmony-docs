---
kits: ["ArkUI"]
description: "Answers common display development questions, including the meaning of the orientation value for virtual screens and discrepancies between screen orientation enumerations and actual behavior, to help you identify causes and understand related concepts."
keywords: [virtual screen, Display object, orientation, screen orientation]
doctype: faq
status: active
---

# Display Development FAQs
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk-->
<!--Designer: @wulong158-->
<!--Tester: @LiTongguan2026-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=27bf6967fc994505af5bc56dd1e6eb560ab219d9 translatedAt=2026-11-12T12:34:02.148Z pushedAt=2026-11-03T12:47:30.238Z nl=1 -->

<!--RP1-->
<!--RP1End-->

## What Does the Orientation Value 4 of the Display Object Mean for a Virtual Screen?

**Symptom**

After obtaining the **Display** object of a virtual screen, the orientation value is **4**, which is not within the [Orientation](../reference/apis-arkui/js-apis-display.md#orientation10) enumeration range.

**Possible Causes**

A virtual screen has no physical screen and cannot perceive the screen orientation. If the screen orientation is not actively set, the system cannot return any value in the **Orientation** enumeration. In this case, the orientation property returns **4** to indicate that the screen orientation is unknown.
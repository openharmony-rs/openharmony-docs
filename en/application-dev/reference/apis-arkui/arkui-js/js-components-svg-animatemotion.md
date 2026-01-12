# animateMotion
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

>  **NOTE**
>
>  This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.

The **\<animateMotion>** component is used to define the animation along a path.

## Required Permissions

None.


## Child Components

Not supported


## Attributes

The **animate** attributes (**values** does not take effect) and the attributes in the following table are supported.

| Name| Type| Default Value| Mandatory| Description|
| -------- | -------- | -------- | -------- | -------- |
| keyPoints | string | - | Yes| Point position of a group of key frames. The value of each frame is the distance proportion of the object along the path. The function is the same as that of **values** in the **animate** attribute.|
| path | string | - | Yes| Motion path. The syntax is the same as that of the **d** attribute of the **\<path>** component.|
| rotate | [auto \| auto-reverse \| &lt;number&gt;] | auto | No| Rotation direction of an animation object.|

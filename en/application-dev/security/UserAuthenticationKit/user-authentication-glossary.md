# Glossary

<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=2387034923775bac161d9ecf5f8bba32e286eb75 translatedAt=2026-11-03T05:47:23.361Z pushedAt=2026-11-03T07:45:11.634Z nl=1 -->

## M

### System Modal Dialog

A system modal dialog is a system-level dialog. When launched by an application, it is fixedly centered on the desktop and its position is independent of the source application. Before the user finishes interacting with it, the entire system is blocked, meaning no other operations can be performed. It is suitable for high-priority authentication scenarios that require blocking global operations.

The following figure shows the diagram:

![system-level-modal](figures/system-level-modal.png)

### Application-Level Modal Dialog

A dialog that takes effect only within an application. It is displayed in the center of the application UI after being brought up by the application. Once displayed, the application UI that brought up the dialog is blocked and cannot be operated within the application until the user completes the interaction. Other UIs are not affected and remain operable.

The following figure shows the diagram:

![application-level-modal](figures/application-level-modal.png)

# DataAbility Overview
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @xialiangwei-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=79e2b0709a488b07e5881d61578e00850aa4f234 translatedAt=2026-11-23T08:08:24.608Z pushedAt=2026-11-24T09:05:06.735Z nl=1 -->


A DataAbility is an ability that uses the Data template. It provides unified data access objects for external systems, but not a UI for user interaction. A DataAbility can be started by a PageAbility, a ServiceAbility, or other applications. It remains to run in the background even after the user switches to another application.


A DataAbility helps applications manage access to data stored by themselves and other applications, and provides methods for sharing data with other applications, either on the same device or across devices.


Data can be stored in a database or files on disks. The DataAbility provides methods for inserting, deleting, updating, and querying data, and opening files. You should implement these methods.

# Text Selection Service Glossary

<!--Kit: Basic Services Kit-->
<!--Subsystem: SelectionInput-->
<!--Owner: @zl_startup-->
<!--Designer: @zl_startup-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=b7fd791217eb31a347f5d13714b33196dd35ae59 translatedAt=2026-11-16T04:30:51.202Z pushedAt=2026-11-16T07:30:21.280Z nl=1 -->

## S

### Selected Application

The source app where text is selected by the user. The selection service extracts the selected text from it through the system copy mechanism, requiring no additional adaptation by the app. Apps that do not support system-level copying (such as controlled WebViews or sandboxed apps) cannot work with this feature.

### Selection Application

An app that implements the Selection ExtensionAbility. After being launched by the selection service, this type of app can listen for the selection completion event to obtain the text selected by the user, and then execute subsequent business logic such as translation, summarization, and expansion.

### Selection ExtensionAbility

A type of ExtensionAbility component. It allows an app to obtain the selected text after the user makes a selection and manages the lifecycle of the selection panel, thereby facilitating the implementation of business logic such as translation, summarization, and expansion.
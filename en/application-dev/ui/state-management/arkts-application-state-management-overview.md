# Application State Management Overview

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=59b65fcc65a22b7c940ca535023658111a023e22 translatedAt=2026-06-29T10:55:15.484Z pushedAt=2026-06-29T11:42:47.950Z -->

The decorators introduced in the component status management chapter can only share state variables within a page, that is, on a single component tree. If you want to implement application-level state data sharing or share state across multiple pages, they need to implement application-level state management. ArkTS provides various application state management capabilities based on different characteristics:

- [LocalStorage](arkts-localstorage.md): API for storing the UI state, usually used for state sharing within a [UIAbility](../../reference/apis-ability-kit/js-apis-app-ability-uiAbility.md) or between pages.

- [AppStorage](arkts-appstorage.md): special, singleton LocalStorage object within the application, which is created by the UI framework at application startup and provides the central storage for application UI state attributes.

- [PersistentStorage](arkts-persiststorage.md): API for persisting application attributes. It is usually used together with AppStorage to persist selected AppStorage attributes to the disk so that their values are the same upon application re-start as they were when the application was closed.

- [Environment](arkts-environment.md): a range of environment parameters regarding the device where the application runs. The environment parameters are synchronized to AppStorage and can be used together with AppStorage.
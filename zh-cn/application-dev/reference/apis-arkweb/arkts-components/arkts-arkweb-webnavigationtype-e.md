# WebNavigationType

Enum type supplied to {@link navigationType} for the navigation's type.

**起始版本：** 11

**系统能力：** SystemCapability.Web.Webview.Core

## UNKNOWN

```TypeScript
UNKNOWN = 0
```

Unknown type.

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## MAIN_FRAME_NEW_ENTRY

```TypeScript
MAIN_FRAME_NEW_ENTRY = 1
```

A new entry was created due to a navigation happened on the main frame.
Contains all situations that will generate a mainframe navigation entry,
which means that navigations to a hash on the same document or history.pushState
also belong to this type.

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## MAIN_FRAME_EXISTING_ENTRY

```TypeScript
MAIN_FRAME_EXISTING_ENTRY = 2
```

Navigate to an existing entry due to a navigation on the main frame.
e.g.
1. History navigations.
2. Reloads (contains loading the same url).
3. Same-document navigations(history.replaceState(), location.replace()).

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## NAVIGATION_TYPE_NEW_SUBFRAME

```TypeScript
NAVIGATION_TYPE_NEW_SUBFRAME = 4
```

A navigation happened on subframe which was triggered by user.

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## NAVIGATION_TYPE_AUTO_SUBFRAME

```TypeScript
NAVIGATION_TYPE_AUTO_SUBFRAME = 5
```

A navigation happened on the subframe automatically.

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core


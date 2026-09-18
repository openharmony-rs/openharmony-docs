# RenderProcessNotRespondingData

Provides detailed information about the unresponsive rendering process. It is suitable for scenarios where diagnosing rendering process exceptions is required, improving troubleshooting accuracy and efficiency.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## jsStack

```TypeScript
jsStack: string
```

JavaScript call stack information of the web page.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## pid

```TypeScript
pid: number
```

Process ID of the web page.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## reason

```TypeScript
reason: RenderProcessNotRespondingReason
```

Reason why the rendering process does not respond.

**Type:** [RenderProcessNotRespondingReason](arkts-arkweb-renderprocessnotrespondingreason-e.md)

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

# SiteIsolationMode

The site isolation mechanism isolates websites from different origins in different renderer subprocesses, reducing the cross-origin attack surface. For example, in the original process model on PC, each tab corresponds to one renderer subprocess. After site isolation is enabled, iframes from different origins run in independent renderer subprocesses.

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

## PARTIAL

```TypeScript
PARTIAL = 0
```

Partial site isolation, that is, new sites are loaded in the same renderer process.

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

## STRICT

```TypeScript
STRICT = 1
```

Strict site isolation. Iframes from different sites are switched to new render processes.

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

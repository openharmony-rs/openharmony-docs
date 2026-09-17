# EventProcess

```TypeScript
type EventProcess = (event: string, args: Record<string, Object>) => void
```

The general process funcation with an event and arguments.

**Since:** 26.1.0

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | string | Yes | request event |
| args | Record&lt;string, Object&gt; | Yes | arguments associated with event |

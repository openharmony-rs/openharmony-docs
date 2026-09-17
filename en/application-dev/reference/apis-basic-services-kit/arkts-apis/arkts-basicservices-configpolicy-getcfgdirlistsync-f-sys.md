# getCfgDirListSync (System API)

## Modules to Import

```TypeScript
import { configPolicy } from '@kit.BasicServicesKit';
```

## getCfgDirListSync

```TypeScript
function getCfgDirListSync(): Array<string>
```

Obtains a list of configuration level directories, in ascending order of priority.

**Since:** 11

**System capability:** SystemCapability.Customization.ConfigPolicy

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Obtains the list of configuration level directories. This API returns the result synchronously. |

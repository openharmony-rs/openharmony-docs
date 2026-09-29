# FormItem

```TypeScript
interface FormItem
```

Describes the form item of a task.

**Since:** 10

<!--Device-agent-interface FormItem--><!--Device-agent-interface FormItem-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## name

```TypeScript
name: string
```

Form parameter name.

**Type:** string

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormItem-name: string--><!--Device-FormItem-name: string-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## value

```TypeScript
value: string | FileSpec | Array<FileSpec>
```

Form parameter value.

**Type:** string &#124; [FileSpec](arkts-basicservices-agent-filespec-i.md) &#124; Array&lt;[FileSpec](arkts-basicservices-agent-filespec-i.md)&gt;

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-FormItem-value: string | FileSpec | Array<FileSpec>--><!--Device-FormItem-value: string | FileSpec | Array<FileSpec>-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

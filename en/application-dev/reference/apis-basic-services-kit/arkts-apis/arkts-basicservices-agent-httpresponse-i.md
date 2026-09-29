# HttpResponse

```TypeScript
interface HttpResponse
```

Describes the data structure of the task response header.

**Since:** 12

<!--Device-agent-interface HttpResponse--><!--Device-agent-interface HttpResponse-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## headers

```TypeScript
readonly headers: Map<string, Array<string>>
```

HTTP response header.

**Type:** Map&lt;string, Array&lt;string&gt;&gt;

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-HttpResponse-readonly headers: Map<string, Array<string>>--><!--Device-HttpResponse-readonly headers: Map<string, Array<string>>-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## reason

```TypeScript
readonly reason: string
```

HTTP response cause.

**Type:** string

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-HttpResponse-readonly reason: string--><!--Device-HttpResponse-readonly reason: string-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## statusCode

```TypeScript
readonly statusCode: number
```

HTTP response status code.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-HttpResponse-readonly statusCode: int--><!--Device-HttpResponse-readonly statusCode: int-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

## version

```TypeScript
readonly version: string
```

HTTP version.

**Type:** string

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-HttpResponse-readonly version: string--><!--Device-HttpResponse-readonly version: string-End-->

**System capability:** SystemCapability.Request.FileTransferAgent

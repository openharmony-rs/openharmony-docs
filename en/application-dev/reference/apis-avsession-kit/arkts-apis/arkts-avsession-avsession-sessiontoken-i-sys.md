# SessionToken (System API)

```TypeScript
interface SessionToken
```

Session token. Used to judge the legitimacy of the session.

**Since:** 9

<!--Device-avSession-interface SessionToken--><!--Device-avSession-interface SessionToken-End-->

**System capability:** SystemCapability.Multimedia.AVSession.Manager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## pid

```TypeScript
pid?: number
```

Process id of session

**Type:** number

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-SessionToken-pid?: long--><!--Device-SessionToken-pid?: long-End-->

**System capability:** SystemCapability.Multimedia.AVSession.Manager

**System API:** This is a system API.

## sessionId

```TypeScript
sessionId: string
```

The unique session id of the avsession object

**Type:** string

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-SessionToken-sessionId: string--><!--Device-SessionToken-sessionId: string-End-->

**System capability:** SystemCapability.Multimedia.AVSession.Manager

**System API:** This is a system API.

## uid

```TypeScript
uid?: number
```

User id

**Type:** number

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-SessionToken-uid?: long--><!--Device-SessionToken-uid?: long-End-->

**System capability:** SystemCapability.Multimedia.AVSession.Manager

**System API:** This is a system API.

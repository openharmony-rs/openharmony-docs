| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增错误码|类名：MessageSequence；<br>API声明：readByteArray(): number[];<br>差异内容：NA|类名：MessageSequence；<br>API声明：readByteArray(): number[];<br>差异内容：401|api/@ohos.rpc.d.ts|
|新增错误码|类名：MessageSequence；<br>API声明：readAshmem(): Ashmem;<br>差异内容：NA|类名：MessageSequence；<br>API声明：readAshmem(): Ashmem;<br>差异内容：1900004,401|api/@ohos.rpc.d.ts|
|删除错误码|类名：MessageSequence；<br>API声明：setSize(size: number): void;<br>差异内容：1900009|类名：MessageSequence；<br>API声明：setSize(size: number): void;<br>差异内容：NA|api/@ohos.rpc.d.ts|
|删除错误码|类名：MessageSequence；<br>API声明：setCapacity(size: number): void;<br>差异内容：1900009|类名：MessageSequence；<br>API声明：setCapacity(size: number): void;<br>差异内容：NA|api/@ohos.rpc.d.ts|
|删除错误码|类名：MessageSequence；<br>API声明：rewindRead(pos: number): void;<br>差异内容：1900010|类名：MessageSequence；<br>API声明：rewindRead(pos: number): void;<br>差异内容：NA|api/@ohos.rpc.d.ts|
|删除错误码|类名：MessageSequence；<br>API声明：rewindWrite(pos: number): void;<br>差异内容：1900009|类名：MessageSequence；<br>API声明：rewindWrite(pos: number): void;<br>差异内容：NA|api/@ohos.rpc.d.ts|
|删除错误码|类名：MessageSequence；<br>API声明：readAshmem(): Ashmem;<br>差异内容：1900010|类名：MessageSequence；<br>API声明：readAshmem(): Ashmem;<br>差异内容：NA|api/@ohos.rpc.d.ts|
|删除错误码|类名：IRemoteObject；<br>API声明：registerDeathRecipient(recipient: DeathRecipient, flags: number): void;<br>差异内容：1900005|类名：IRemoteObject；<br>API声明：registerDeathRecipient(recipient: DeathRecipient, flags: number): void;<br>差异内容：NA|api/@ohos.rpc.d.ts|
|删除错误码|类名：IRemoteObject；<br>API声明：unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void;<br>差异内容：1900005|类名：IRemoteObject；<br>API声明：unregisterDeathRecipient(recipient: DeathRecipient, flags: number): void;<br>差异内容：NA|api/@ohos.rpc.d.ts|
|错误码变更|类名：MessageSequence；<br>API声明：writeAshmem(ashmem: Ashmem): void;<br>差异内容：1900009,401|类名：MessageSequence；<br>API声明：writeAshmem(ashmem: Ashmem): void;<br>差异内容：1900003,401|api/@ohos.rpc.d.ts|

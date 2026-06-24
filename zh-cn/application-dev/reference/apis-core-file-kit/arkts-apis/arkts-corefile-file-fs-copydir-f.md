# copyDir

## copyDir

```TypeScript
declare function copyDir(src: string, dest: string, mode?: number): Promise<void>
```

复制源目录至目标路径下，使用promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源目录的应用沙箱路径。 |
| dest | string | 是 | 目标目录的应用沙箱路径。 |
| mode | number | 否 | 复制模式，默认值为0。<br/>- mode为0，文件级别抛异常。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则抛出异常。源目录下未冲突的文件全部移动至目标目录<br/>下，目标目录下未冲突文件将继续保留，且冲突文件信息将在抛出异常的data属性中以Array形式提供。<br/>- mode为1，文件级别强制覆盖。目<br/>标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则强制覆盖冲突目录下所有同名文件，未冲突文件将继续保留。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900004](../../errorcode-universal.md#13900004-Interrupted) | Interrupted system call |
| [13900005](../../errorcode-universal.md#13900005-IO) | I/O error |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again |
| [13900011](../../errorcode-universal.md#13900011-Out) | Out of memory |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900013](../../errorcode-universal.md#13900013-Bad) | Bad address |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900019](../../errorcode-universal.md#13900019-Is) | Is a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900030](../../errorcode-universal.md#13900030-File) | File name too long |
| [13900031](../../errorcode-universal.md#13900031-Function) | Function not implemented |
| [13900033](../../errorcode-universal.md#13900033-Too) | Too many symbolic links encountered |
| [13900034](../../errorcode-universal.md#13900034-Operation) | Operation would block |
| [13900038](../../errorcode-universal.md#13900038-Value) | Value too large for defined data type |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |
| [13900044](../../errorcode-universal.md#13900044-Network) | Network is unreachable&lt;br&gt;**适用版本：** 12+ |


## copyDir

```TypeScript
declare function copyDir(src: string, dest: string, callback: AsyncCallback<void>): void
```

复制源目录至目标路径下，使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源目录的应用沙箱路径。 |
| dest | string | 是 | 目标目录的应用沙箱路径。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步复制目录之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900004](../../errorcode-universal.md#13900004-Interrupted) | Interrupted system call |
| [13900005](../../errorcode-universal.md#13900005-IO) | I/O error |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again |
| [13900011](../../errorcode-universal.md#13900011-Out) | Out of memory |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900013](../../errorcode-universal.md#13900013-Bad) | Bad address |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900019](../../errorcode-universal.md#13900019-Is) | Is a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900030](../../errorcode-universal.md#13900030-File) | File name too long |
| [13900031](../../errorcode-universal.md#13900031-Function) | Function not implemented |
| [13900033](../../errorcode-universal.md#13900033-Too) | Too many symbolic links encountered |
| [13900034](../../errorcode-universal.md#13900034-Operation) | Operation would block |
| [13900038](../../errorcode-universal.md#13900038-Value) | Value too large for defined data type |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |


## copyDir

```TypeScript
declare function copyDir(src: string, dest: string, callback: AsyncCallback<void, Array<ConflictFiles>>): void
```

复制源目录至目标路径下，使用callback异步回调。

如果目标目录下有与源目录名冲突的目录，且冲突目录下有同名文件，则抛出异常。源目录下未冲突的文件全部移动至目标目录下，目标目录下未冲突文件将继续保留，且冲突文件信息将在抛出异常的data属性中以Array\<
[ConflictFiles](arkts-corefile-conflictfiles-i.md#ConflictFiles)>形式提供。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源目录的应用沙箱路径。 |
| dest | string | 是 | 目标目录的应用沙箱路径。 |
| callback | AsyncCallback&lt;void, Array&lt;ConflictFiles&gt;&gt; | 是 | 异步复制目录之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900015](../../errorcode-universal.md#13900015-File) | File exists |


## copyDir

```TypeScript
declare function copyDir(src: string, dest: string, mode: number, callback: AsyncCallback<void>): void
```

复制源目录至目标路径下，可设置复制模式。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源目录的应用沙箱路径。 |
| dest | string | 是 | 目标目录的应用沙箱路径。 |
| mode | number | 是 | 复制模式，默认值为0。<br/>- mode为0，文件级别抛异常。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则抛出异常。源目录下未冲突的文件全部移动至目标目录下，<br/>目标目录下未冲突文件将继续保留，且冲突文件信息将在抛出异常的data属性中以Array形式提供。<br/>- mode为1，文件级别强制覆盖。目标目<br/>录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则强制覆盖冲突目录下所有同名文件，未冲突文件将继续保留。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步复制目录之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900004](../../errorcode-universal.md#13900004-Interrupted) | Interrupted system call |
| [13900005](../../errorcode-universal.md#13900005-IO) | I/O error |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again |
| [13900011](../../errorcode-universal.md#13900011-Out) | Out of memory |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900013](../../errorcode-universal.md#13900013-Bad) | Bad address |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900019](../../errorcode-universal.md#13900019-Is) | Is a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900030](../../errorcode-universal.md#13900030-File) | File name too long |
| [13900031](../../errorcode-universal.md#13900031-Function) | Function not implemented |
| [13900033](../../errorcode-universal.md#13900033-Too) | Too many symbolic links encountered |
| [13900034](../../errorcode-universal.md#13900034-Operation) | Operation would block |
| [13900038](../../errorcode-universal.md#13900038-Value) | Value too large for defined data type |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |


## copyDir

```TypeScript
declare function copyDir(src: string, dest: string, mode: number, callback: AsyncCallback<void, Array<ConflictFiles>>): void
```

复制源目录至目标路径下，可设置复制模式。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源目录的应用沙箱路径。 |
| dest | string | 是 | 目标目录的应用沙箱路径。 |
| mode | number | 是 | 复制模式，默认值为0。<br/>- mode为0，文件级别抛异常。目标目录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则抛出异常。源目录下未冲突的文件全部移动至目标目录下，<br/>目标目录下未冲突文件将继续保留，且冲突文件信息将在抛出异常的data属性中以Array形式提供。<br/>- mode为1，文件级别强制覆盖。目标目<br/>录下存在与源目录名冲突的目录，若冲突目录下存在同名文件，则强制覆盖冲突目录下所有同名文件，未冲突文件将继续保留。 |
| callback | AsyncCallback&lt;void, Array&lt;ConflictFiles&gt;&gt; | 是 | 异步复制目录之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900015](../../errorcode-universal.md#13900015-File) | File exists |


# PrintTask

打印任务完成后的事件监听回调接口类。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-print-interface PrintTask--><!--Device-print-interface PrintTask-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## offBlock

```TypeScript
offBlock(callback?: Callback<void>): void
```

Unregister event callback when the current print task is in process.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.PRINT

<!--Device-PrintTask-offBlock(callback?: Callback<void>): void--><!--Device-PrintTask-offBlock(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | The callback function for print task change event |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';
import { fileUri } from '@kit.CoreFileKit';

let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
try {
    print.print([fileUri.getUriFromPath(filePath)]).then((printTask: print.PrintTask) => {
        printTask.offBlock(() => {
            console.info('unregister state block');
        })
        // ...
    });
} catch (error: BusinessError) {
    console.error('print err ' + JSON.stringify(error));
}
```

## offCancel

```TypeScript
offCancel(callback?: Callback<void>): void
```

Unregister event callback when the current print task is in process.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.PRINT

<!--Device-PrintTask-offCancel(callback?: Callback<void>): void--><!--Device-PrintTask-offCancel(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | The callback function for print task change event |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';
import { fileUri } from '@kit.CoreFileKit';

let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
try {
    print.print([fileUri.getUriFromPath(filePath)]).then((printTask: print.PrintTask) => {
        printTask.offCancel(() => {
            console.info('unregister state cancel');
        })
        // ...
    });
} catch (error: BusinessError) {
    console.error('print err ' + JSON.stringify(error));
}
```

## offFail

```TypeScript
offFail(callback?: Callback<void>): void
```

Unregister event callback when the current print task is in process.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.PRINT

<!--Device-PrintTask-offFail(callback?: Callback<void>): void--><!--Device-PrintTask-offFail(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | The callback function for print task change event |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';
import { fileUri } from '@kit.CoreFileKit';

let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
try {
    print.print([fileUri.getUriFromPath(filePath)]).then((printTask: print.PrintTask) => {
        printTask.offFail(() => {
            console.info('unregister state fail');
        })
        // ...
    });
} catch (error: BusinessError) {
    console.error('print err ' + JSON.stringify(error));
}
```

## offSucceed

```TypeScript
offSucceed(callback?: Callback<void>): void
```

Unregister event callback when the current print task is in process.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.PRINT

<!--Device-PrintTask-offSucceed(callback?: Callback<void>): void--><!--Device-PrintTask-offSucceed(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | The callback function for print task change event |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';
import { fileUri } from '@kit.CoreFileKit';

let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
try {
    print.print([fileUri.getUriFromPath(filePath)]).then((printTask: print.PrintTask) => {
        printTask.offSucceed(() => {
            console.info('unregister state succeed');
        })
        // ...
    });
} catch (error: BusinessError) {
    console.error('print err ' + JSON.stringify(error));
}
```

## off_block

```TypeScript
off(type: 'block', callback?: Callback<void>): void
```

取消打印任务阻塞的监听，使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**需要权限：** ohos.permission.PRINT

<!--Device-PrintTask-off(type: 'block', callback?: Callback<void>): void--><!--Device-PrintTask-off(type: 'block', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'block' | 是 | 取消监听，&lt;br/&gt;监听字段：block，&lt;br/&gt;表示打印任务阻塞。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 回调函数，取消指定的打印任务阻塞事件订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Index {
    build() {
        Scroll() {
            Column({ space: 10 }) {
                Button("打印").width('90%').height(50).onClick(() => {
                    let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
                    let context = this.getUIContext().getHostContext();
                    print.print([fileUri.getUriFromPath(filePath)], context).then((printTask: print.PrintTask) => {
                        printTask.off('block', () => {
                            console.info('unregister state block');
                        })
                        // ...
                    }).catch((error: BusinessError) => {
                        console.error('print err ' + JSON.stringify(error));
                    })
                })
            }
            .justifyContent(FlexAlign.Center)
            .constraintSize({ minHeight: '100%' })
            .width('100%')
        }
        .height('100%')
    }
}
```

## off_cancel

```TypeScript
off(type: 'cancel', callback?: Callback<void>): void
```

取消打印任务被取消的监听，使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**需要权限：** ohos.permission.PRINT

<!--Device-PrintTask-off(type: 'cancel', callback?: Callback<void>): void--><!--Device-PrintTask-off(type: 'cancel', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cancel' | 是 | 取消监听，&lt;br/&gt;监听字段：cancel，&lt;br/&gt;表示打印任务被取消。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 回调函数，取消指定的打印任务被取消事件订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Index {
    build() {
        Scroll() {
            Column({ space: 10 }) {
                Button("打印").width('90%').height(50).onClick(() => {
                    let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
                    let context = this.getUIContext().getHostContext();
                    print.print([fileUri.getUriFromPath(filePath)], context).then((printTask: print.PrintTask) => {
                        printTask.off('cancel', () => {
                            console.info('unregister state cancel');
                        })
                        // ...
                    }).catch((error: BusinessError) => {
                        console.error('print err ' + JSON.stringify(error));
                    })
                })
            }
            .justifyContent(FlexAlign.Center)
            .constraintSize({ minHeight: '100%' })
            .width('100%')
        }
        .height('100%')
    }
}
```

## off_fail

```TypeScript
off(type: 'fail', callback?: Callback<void>): void
```

取消打印任务失败的监听，使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**需要权限：** ohos.permission.PRINT

<!--Device-PrintTask-off(type: 'fail', callback?: Callback<void>): void--><!--Device-PrintTask-off(type: 'fail', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'fail' | 是 | 取消监听，&lt;br/&gt;监听字段：fail，&lt;br/&gt;表示打印任务失败。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 回调函数，取消指定的打印任务失败事件订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Index {
    build() {
        Scroll() {
            Column({ space: 10 }) {
                Button("打印").width('90%').height(50).onClick(() => {
                    let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
                    let context = this.getUIContext().getHostContext();
                    print.print([fileUri.getUriFromPath(filePath)], context).then((printTask: print.PrintTask) => {
                        printTask.off('fail', () => {
                            console.info('unregister state fail');
                        })
                        // ...
                    }).catch((error: BusinessError) => {
                        console.error('print err ' + JSON.stringify(error));
                    })
                })
            }
            .justifyContent(FlexAlign.Center)
            .constraintSize({ minHeight: '100%' })
            .width('100%')
        }
        .height('100%')
    }
}
```

## off_succeed

```TypeScript
off(type: 'succeed', callback?: Callback<void>): void
```

取消打印任务成功的监听，使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**需要权限：** ohos.permission.PRINT

<!--Device-PrintTask-off(type: 'succeed', callback?: Callback<void>): void--><!--Device-PrintTask-off(type: 'succeed', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'succeed' | 是 | 取消监听，&lt;br/&gt;监听字段：succeed，&lt;br/&gt;表示打印任务成功。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 回调函数，取消指定的打印任务成功事件订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Index {
    build() {
        Scroll() {
            Column({ space: 10 }) {
                Button("打印").width('90%').height(50).onClick(() => {
                    let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
                    let context = this.getUIContext().getHostContext();
                    print.print([fileUri.getUriFromPath(filePath)], context).then((printTask: print.PrintTask) => {
                        printTask.off('succeed', () => {
                            console.info('unregister state succeed');
                        })
                        // ...
                    }).catch((error: BusinessError) => {
                        console.error('print err ' + JSON.stringify(error));
                    })
                })
            }
            .justifyContent(FlexAlign.Center)
            .constraintSize({ minHeight: '100%' })
            .width('100%')
        }
        .height('100%')
    }
}
```

## onBlock

```TypeScript
onBlock(callback: Callback<void>): void
```

Register event callback when the current print task is in process.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.PRINT

<!--Device-PrintTask-onBlock(callback: Callback<void>): void--><!--Device-PrintTask-onBlock(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | The callback function for print task change event |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';
import { fileUri } from '@kit.CoreFileKit';

let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
try {
    print.print([fileUri.getUriFromPath(filePath)]).then((printTask: print.PrintTask) => {
        printTask.onBlock(() => {
            console.info('print state is block');
        })
        // ...
    });
} catch (error: BusinessError) {
    console.error('print err ' + JSON.stringify(error));
}
```

## onCancel

```TypeScript
onCancel(callback: Callback<void>): void
```

Register event callback when the current print task is in process.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.PRINT

<!--Device-PrintTask-onCancel(callback: Callback<void>): void--><!--Device-PrintTask-onCancel(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | The callback function for print task change event |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';
import { fileUri } from '@kit.CoreFileKit';

let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
try {
    print.print([fileUri.getUriFromPath(filePath)]).then((printTask: print.PrintTask) => {
        printTask.onCancel(() => {
            console.info('print state is cancel');
        })
        // ...
    });
} catch (error: BusinessError) {
    console.error('print err ' + JSON.stringify(error));
}
```

## onFail

```TypeScript
onFail(callback: Callback<void>): void
```

Register event callback when the current print task is in process.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.PRINT

<!--Device-PrintTask-onFail(callback: Callback<void>): void--><!--Device-PrintTask-onFail(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | The callback function for print task change event |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';
import { fileUri } from '@kit.CoreFileKit';

let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
try {
    print.print([fileUri.getUriFromPath(filePath)]).then((printTask: print.PrintTask) => {
        printTask.onFail(() => {
            console.info('print state is fail');
        })
        // ...
    });
} catch (error: BusinessError) {
    console.error('print err ' + JSON.stringify(error));
}
```

## onSucceed

```TypeScript
onSucceed(callback: Callback<void>): void
```

Register event callback when the current print task is in process.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.PRINT

<!--Device-PrintTask-onSucceed(callback: Callback<void>): void--><!--Device-PrintTask-onSucceed(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | The callback function for print task change event |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';
import { fileUri } from '@kit.CoreFileKit';

let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
try {
    print.print([fileUri.getUriFromPath(filePath)]).then((printTask: print.PrintTask) => {
        printTask.onSucceed(() => {
            console.info('print state is succeed');
        })
        // ...
    });
} catch (error: BusinessError) {
    console.error('print err ' + JSON.stringify(error));
}
```

## on_block

```TypeScript
on(type: 'block', callback: Callback<void>): void
```

注册打印任务阻塞的监听，使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**需要权限：** ohos.permission.PRINT

<!--Device-PrintTask-on(type: 'block', callback: Callback<void>): void--><!--Device-PrintTask-on(type: 'block', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'block' | 是 | 注册监听，&lt;br/&gt;监听字段：block，&lt;br/&gt;表示打印任务阻塞。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数，通知调用方打印任务阻塞。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Index {
    build() {
        Scroll() {
            Column({ space: 10 }) {
                Button("打印").width('90%').height(50).onClick(() => {
                    let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
                    let context = this.getUIContext().getHostContext();
                    print.print([fileUri.getUriFromPath(filePath)], context).then((printTask: print.PrintTask) => {
                        printTask.on('block', () => {
                            console.info('print state is block');
                        })
                        // ...
                    }).catch((error: BusinessError) => {
                        console.error('print err ' + JSON.stringify(error));
                    })
                })
            }
            .justifyContent(FlexAlign.Center)
            .constraintSize({ minHeight: '100%' })
            .width('100%')
        }
        .height('100%')
    }
}
```

## on_cancel

```TypeScript
on(type: 'cancel', callback: Callback<void>): void
```

注册打印任务被取消的监听，使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**需要权限：** ohos.permission.PRINT

<!--Device-PrintTask-on(type: 'cancel', callback: Callback<void>): void--><!--Device-PrintTask-on(type: 'cancel', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cancel' | 是 | 注册监听，&lt;br/&gt;监听字段：cancel，&lt;br/&gt;表示打印任务被取消。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数，通知调用方打印任务被取消。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Index {
    build() {
        Scroll() {
            Column({ space: 10 }) {
                Button("打印").width('90%').height(50).onClick(() => {
                    let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
                    let context = this.getUIContext().getHostContext();
                    print.print([fileUri.getUriFromPath(filePath)], context).then((printTask: print.PrintTask) => {
                        printTask.on('cancel', () => {
                            console.info('print state is cancel');
                        })
                        // ...
                    }).catch((error: BusinessError) => {
                        console.error('print err ' + JSON.stringify(error));
                    })
                })
            }
            .justifyContent(FlexAlign.Center)
            .constraintSize({ minHeight: '100%' })
            .width('100%')
        }
        .height('100%')
    }
}
```

## on_fail

```TypeScript
on(type: 'fail', callback: Callback<void>): void
```

注册打印任务失败的监听，使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**需要权限：** ohos.permission.PRINT

<!--Device-PrintTask-on(type: 'fail', callback: Callback<void>): void--><!--Device-PrintTask-on(type: 'fail', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'fail' | 是 | 注册监听，&lt;br/&gt;监听字段：fail，&lt;br/&gt;表示打印任务失败。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数，通知调用方打印任务失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Index {
    build() {
        Scroll() {
            Column({ space: 10 }) {
                Button("打印").width('90%').height(50).onClick(() => {
                    let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
                    let context = this.getUIContext().getHostContext();
                    print.print([fileUri.getUriFromPath(filePath)], context).then((printTask: print.PrintTask) => {
                        printTask.on('fail', () => {
                            console.info('print state is fail');
                        })
                        // ...
                    }).catch((error: BusinessError) => {
                        console.error('print err ' + JSON.stringify(error));
                    })
                })
            }
            .justifyContent(FlexAlign.Center)
            .constraintSize({ minHeight: '100%' })
            .width('100%')
        }
        .height('100%')
    }
}
```

## on_succeed

```TypeScript
on(type: 'succeed', callback: Callback<void>): void
```

注册打印任务成功的监听，使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**需要权限：** ohos.permission.PRINT

<!--Device-PrintTask-on(type: 'succeed', callback: Callback<void>): void--><!--Device-PrintTask-on(type: 'succeed', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'succeed' | 是 | 注册监听，&lt;br/&gt;监听字段：succeed，&lt;br/&gt;表示打印任务成功。 |
| callback | [Callback](arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 回调函数，通知调用方打印任务成功。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |

## 示例

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@ohos.base';
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Index {
    build() {
        Scroll() {
            Column({ space: 10 }) {
                Button("打印").width('90%').height(50).onClick(() => {
                    let filePath = '/data/storage/el2/base/haps/entry/files/test.pdf';
                    let context = this.getUIContext().getHostContext();
                    print.print([fileUri.getUriFromPath(filePath)], context).then((printTask: print.PrintTask) => {
                        printTask.on('succeed', () => {
                            console.info('print state is succeed');
                        })
                        // ...
                    }).catch((error: BusinessError) => {
                        console.error('print err ' + JSON.stringify(error));
                    })
                })
            }
            .justifyContent(FlexAlign.Center)
            .constraintSize({ minHeight: '100%' })
            .width('100%')
        }
        .height('100%')
    }
}
```


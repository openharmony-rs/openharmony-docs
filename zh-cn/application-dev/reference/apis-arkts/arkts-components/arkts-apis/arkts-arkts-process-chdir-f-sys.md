# chdir（系统接口）

## 导入模块

```TypeScript
import { process } from '@kit.ArkTS';
```

## chdir

```TypeScript
function chdir(dir: string): void
```

修改当前目录。

**起始版本：** 7

**系统能力：** SystemCapability.Utils.Lang

**系统接口：** 此接口为系统接口。

**测试接口：** 此接口仅在自动化测试脚本中使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dir | string | 是 | 要切换到的路径。 |

# TextInputType

文本输入类型。

**起始版本：** 10

<!--Device-inputMethod-export enum TextInputType--><!--Device-inputMethod-export enum TextInputType-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## NONE

```TypeScript
NONE = -1
```

NONE。

**使用场景：**当编辑框不希望指定特定输入类型时使用，输入法将使用默认键盘布局。

**起始版本：** 10

<!--Device-TextInputType-NONE = -1--><!--Device-TextInputType-NONE = -1-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## TEXT

```TypeScript
TEXT = 0
```

文本类型。

**使用场景：**适用于普通文本输入框，如聊天、备忘录等，输入法显示全功能键盘。

**起始版本：** 10

<!--Device-TextInputType-TEXT = 0--><!--Device-TextInputType-TEXT = 0-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## MULTILINE

```TypeScript
MULTILINE
```

多行类型。

**使用场景：**适用于需要多行文本输入的场景，如长文本编辑、评论框等。

**起始版本：** 10

<!--Device-TextInputType-MULTILINE--><!--Device-TextInputType-MULTILINE-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## NUMBER

```TypeScript
NUMBER
```

数字类型。

**使用场景：**适用于仅需要输入数字的场景，如数量输入、年龄输入等，输入法显示数字键盘。

**起始版本：** 10

<!--Device-TextInputType-NUMBER--><!--Device-TextInputType-NUMBER-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## PHONE

```TypeScript
PHONE
```

电话号码类型。

**使用场景：**适用于电话号码输入框，输入法显示电话号码键盘（包含数字和常用电话符号）。

**起始版本：** 10

<!--Device-TextInputType-PHONE--><!--Device-TextInputType-PHONE-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## DATETIME

```TypeScript
DATETIME
```

日期类型。

**使用场景：**适用于日期时间输入框，输入法显示日期相关的键盘布局。

**起始版本：** 10

<!--Device-TextInputType-DATETIME--><!--Device-TextInputType-DATETIME-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## EMAIL_ADDRESS

```TypeScript
EMAIL_ADDRESS
```

邮箱地址类型。

**使用场景：**适用于邮箱输入框，输入法键盘会突出显示"@""."等常用邮箱符号。

**起始版本：** 10

<!--Device-TextInputType-EMAIL_ADDRESS--><!--Device-TextInputType-EMAIL_ADDRESS-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## URL

```TypeScript
URL
```

链接类型。

**使用场景：**适用于网址输入框，输入法键盘会突出显示"/""."等常用URL符号。

**起始版本：** 10

<!--Device-TextInputType-URL--><!--Device-TextInputType-URL-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## VISIBLE_PASSWORD

```TypeScript
VISIBLE_PASSWORD
```

密码类型。

**使用场景：**适用于密码输入框，输入法显示可见密码键盘，不进行自动建议。

**起始版本：** 10

<!--Device-TextInputType-VISIBLE_PASSWORD--><!--Device-TextInputType-VISIBLE_PASSWORD-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## NUMBER_PASSWORD

```TypeScript
NUMBER_PASSWORD
```

数字密码类型。

**使用场景：**适用于仅需输入数字密码的场景，如PIN码输入。

**起始版本：** 11

<!--Device-TextInputType-NUMBER_PASSWORD--><!--Device-TextInputType-NUMBER_PASSWORD-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## SCREEN_LOCK_PASSWORD

```TypeScript
SCREEN_LOCK_PASSWORD
```

锁屏密码类型。

**使用场景：**适用于锁屏界面的密码输入框。

**起始版本：** 20

<!--Device-TextInputType-SCREEN_LOCK_PASSWORD--><!--Device-TextInputType-SCREEN_LOCK_PASSWORD-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## USER_NAME

```TypeScript
USER_NAME
```

用户名类型。

**使用场景：**适用于用户名输入框，输入法可根据用户名特点优化建议。

**起始版本：** 20

<!--Device-TextInputType-USER_NAME--><!--Device-TextInputType-USER_NAME-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## NEW_PASSWORD

```TypeScript
NEW_PASSWORD
```

新密码类型。

**使用场景：**适用于设置新密码的输入框，输入法可提供密码强度提示。

**起始版本：** 20

<!--Device-TextInputType-NEW_PASSWORD--><!--Device-TextInputType-NEW_PASSWORD-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## NUMBER_DECIMAL

```TypeScript
NUMBER_DECIMAL
```

带小数点的数字类型。

**使用场景：**适用于需要输入带小数点数字的场景，如金额输入。

**起始版本：** 20

<!--Device-TextInputType-NUMBER_DECIMAL--><!--Device-TextInputType-NUMBER_DECIMAL-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## ONE_TIME_CODE

```TypeScript
ONE_TIME_CODE
```

验证码类型。

**使用场景：**适用于验证码输入框，输入法可优化验证码输入体验。

**起始版本：** 20

<!--Device-TextInputType-ONE_TIME_CODE--><!--Device-TextInputType-ONE_TIME_CODE-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework


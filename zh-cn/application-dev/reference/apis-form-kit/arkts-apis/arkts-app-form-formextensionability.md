# @ohos.app.form.FormExtensionAbility

## 导入模块

```TypeScript
import { FormExtensionAbility } from '@kit.FormKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [FormExtensionAbility](arkts-form-app-form-formextensionability-formextensionability-c.md) | Widget extension class. It provides APIs to notify the widget provider that a widget is being created or the widget visibility status is being changed. |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [FormExtensionAbility](arkts-form-app-form-formextensionability-formextensionability-c-sys.md) | Widget extension class. It provides APIs to notify the widget provider that a widget is being created or the widget visibility status is being changed. |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnAcquireFormStateFn](arkts-form-onacquireformstatefn-t.md) | Called to return a FormState object. &lt;p&gt;You must override this callback if you want this ability to return the actual form state. Otherwise, this method returns DEFAULT by default.&lt;/p&gt; |
| [OnStopFn](arkts-form-onstopfn-t.md) | Called when this ability breaks the last link, notifying the provider that the provider process is about to stop. |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [OnAcquireFormDataFn](arkts-form-onacquireformdatafn-t-sys.md) | Called when the system acquire the form data. |
| [OnShareFormFn](arkts-form-onshareformfn-t-sys.md) | Called when the system shares the form. |
<!--DelEnd-->


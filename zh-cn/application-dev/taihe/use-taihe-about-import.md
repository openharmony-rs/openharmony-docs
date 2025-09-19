# 使用 Taihe 进行 import 相关开发

## 简介

在 Taihe 中，使用 `use` 语法来导入外部声明。Taihe 有两种导入方式：

1. `from ModuleA use DeclFoo;`

2. `use ModuleA;`

其中，`ModuleA` 是要导入的 Taihe IDL 文件的名称（不含文件扩展名），`DeclFoo` 是要导入的具体声明名称。

## 基本概念

使用 `use` 语句导入外部声明。

被导入的 Taihe IDL 文件 user.ohidl
```rust
interface IUser {
    @get getEmail(): String;
    @set setEmail(path: String): void;
}

function makeUser(path: String): IUser;
```

导入的 Taihe IDL 文件 notification.ohidl
```rust
from user use IUser;

interface INotificationService{
    sendMessage(a: IUser): void;
}

function makeNotificationService(): INotificationService;
```
或
```rust
use user;

interface INotificationService{
    sendMessage(a: user.IUser): void;
}

function makeNotificationService(): INotificationService;
```

为了避免重名导致无法分辨由哪个模块导入的情况，支持 `as` 语法：

1. `use A as C;`

2. `from A use B as C;`

上述被导入模块文件样例更改为
```rust
use user as userA;

interface INotificationService{
    sendMessage(a: userA.IUser): void;
}
```
或者
```rust
from user use IUser as IUserA;

interface INotificationService{
    sendMessage(a: IUserA): void;
}
```

## 使用示例

### Taihe 声明

**被导入模块文件 user.ohidl**
```rust
interface IUser {
    @get getEmail(): String;
    @set setEmail(path: String): void;
}

function makeUser(path: String): IUser;
```

**导入模块文件 notification.ohidl**
```rust
from user use IUser;

interface INotificationService{
    sendMessage(a: IUser): void;
}

function makeNotificationService(): INotificationService;
```

### C++ 实现

**user 实现文件**
```cpp
class IUserImpl {
public:
    IUserImpl(string_view path): m_email(path){}

    string getEmail() {
        return this->m_email;
    }

    void setEmail(string_view path) {
        this->m_email = path;
    }

private:
    string m_email;
};

IUser makeUser(string_view path) {
    return make_holder<IUserImpl, IUser>(path);
}
```

**notification 实现文件**
```cpp
class INotificationServiceImpl {
public:
    INotificationServiceImpl() {}

    void sendMessage(::user::weak::IUser a) {
        string_view user_email = a->getEmail(); // 使用 -> 调用Taihe对象的成员方法
        std::cout << "Welcome " << a->getEmail() << std::endl;
    }
};

INotificationService makeNotificationService() {
    return make_holder<INotificationServiceImpl, INotificationService>();
}
```

### ets 使用

```typescript
let userA = user.makeUser("12345@huawei.com");
let userB = user.makeUser("67890@outlook.com");
let noter = notification.makeNotificationService();
noter.sendMessage(userA);
noter.sendMessage(userB);
```

输出结果如下：

```sh
Welcome 12345@huawei.com
Welcome 67890@outlook.com
```

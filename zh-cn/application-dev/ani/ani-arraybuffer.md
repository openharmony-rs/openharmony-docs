# ArrayBuffer
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @wanzixuan330-->
<!--Designer: @LeechyLiang; @zengmanyi; @jcj525-->
<!--Tester: @wuhan544-->
<!--Adviser: @fang-jinxu-->

`ArrayBuffer`适合承载二进制缓冲区、图片/音频数据、协议报文等需要按字节访问的数据。native侧既可以创建`ArrayBuffer`，也可以读取ArkTS传入的`ArrayBuffer`底层数据。

`ArrayBuffer`类型支持两个主要接口：

```cpp
// 创建指定字节长度的ArrayBuffer，并返回底层数据地址。
ani_status CreateArrayBuffer(ani_env *env, size_t length, void **data_result, ani_arraybuffer *arraybuffer_result);

// 获取ArrayBuffer的底层数据地址和字节长度。
ani_status ArrayBuffer_GetInfo(ani_env *env, ani_arraybuffer arraybuffer, void **data_result, size_t *length_result);
```

**示例：**

```ts
loadLibrary("libraryName");

native function handleData(buffer: ArrayBuffer): void

function main() {
    const buffer = new ArrayBuffer(4);
    const uint8View = new Uint8Array(buffer);

    uint8View[0] = 1;
    uint8View[1] = 2;
    uint8View[2] = 0;

    console.info(uint8View);
    handleData(buffer); // Outputs: 1 + 2*256 = 513
    console.info("1*1 + 2*256 = 513");
}
```

```cpp
// 不是ani_array
static void HandleDataImpl(ani_env *env, ani_arraybuffer arraybuffer) {
    void *resultData;
    size_t resultSize;
    env->ArrayBuffer_GetInfo(arraybuffer, &resultData, &resultSize);
    std::cout << *static_cast<uint32_t*>(resultData) << std::endl;
}
```

完整示例：[ani_arraybuffer.cpp](https://gitee.com/LeechyLiang/ani_cookbook/blob/master/ani_arraybuffer/ani_arraybuffer.cpp)


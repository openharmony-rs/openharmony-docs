# OpenGL ES
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @samhu1989-->
<!--Designer: @shi-yang-2012-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->
OpenGL 是一种跨平台的图形 API，用于为 3D 图形处理硬件指定标准的软件接口。[OpenGL ES](https://www.khronos.org/opengles/) 是 OpenGL 规范的一种形式，适用于嵌入式设备。OpenHarmony 现已支持 OpenGL ES 3.2。

## 支持的能力

OpenGL ES 3.2

## 标准库中导出的符号列表

[native api中导出的OpenGL ES 3.2符号列表](openglesv3-symbol.md)

## 引入OpenGL能力

如果开发者需要使用OpenGL的相关能力，需要添加相关动态链接库和头文件。

**添加动态链接库**

CMakeLists.txt中添加以下lib。

```txt
libace_ndk.z.so
libace_napi.z.so
libGLESv3.so
libEGL.so
```

**头文件**

```c++
#include <ace/xcomponent/native_interface_xcomponent.h>
#include <EGL/egl.h>
#include <EGL/eglext.h>
#include <EGL/eglplatform.h>
#include <GLES3/gl3.h>
```

## 相关参考

针对OpenGL ES的使用和相关开发，需要同步了解NDK的开发过程，以及XComponent组件等的使用。具体可参考:

- [NDK开发参考](../../napi/ndk-development-overview.md)

- [NodeAPI参考](./napi.md)

- [XComponentNode参考](../apis-arkui/js-apis-arkui-xcomponentNode.md)

- [XComponent参考](../apis-arkui/arkui-ts/ts-basic-components-xcomponent.md)

## OpenGL ES扩展接口

- OpenGL ES扩展接口的官方参考文档：[OpenGL ES扩展接口](https://registry.khronos.org/OpenGL/index_es.php)
- 开发者可以调用`glGetString`查询芯片厂商支持的扩展接口，调用之前务必初始化上下文。具体示例如下：

```c++
EGLDisplay display;
EGLConfig config;
EGLContext context;
EGLSurface surface;
EGLint majorVersion;
EGLint minorVersion;
EGLNativeWindowType win;
display = eglGetDisplay(EGL_DEFAULT_DISPLAY);
eglInitialize(display, &majorVersion, &minorVersion);
display = eglGetDisplay(EGL_DEFAULT_DISPLAY);
eglInitialize(display, &majorVersion, &minorVersion);
EGLint attribs[] = {
    EGL_RENDERABLE_TYPE,
    EGL_OPENGL_ES2_BIT,
    EGL_BLUE_SIZE, 8,
    EGL_GREEN_SIZE, 8,
    EGL_RED_SIZE, 8,
    EGL_NONE
};
eglChooseConfig(display, attribs, &config, 1, &numConfigs);
context = eglCreateContext(display, config, EGL_NO_CONTEXT, NULL);
surface = eglCreatePbufferSurface(display, config, NULL);
eglMakeCurrent(display, surface, surface, context);

char *strTest = new char[1024];
strTest = (char *)glGetString(GL_EXTENSIONS); // 返回值strTest中会列出所有的扩展接口，并且用空格分隔开
bool isHave = strTest.find("GL_OES_matrix_palette") != -1 ?
    true :
    false; // 查询是否有某个扩展接口，有则isHave为true，没有则为false
```

## 简单示例

```cpp

EGLNativeWindowType mEglWindow;
EGLDisplay mEGLDisplay = EGL_NO_DISPLAY;
EGLConfig mEGLConfig = nullptr;
EGLContext mEGLContext = EGL_NO_CONTEXT;
EGLContext mSharedEGLContext = EGL_NO_CONTEXT;
EGLSurface mEGLSurface = nullptr;
EGLint configsNum;
mEglWindow = reinterpret_cast<EGLNativeWindowType>(window);
    
//初始化EGL Display
mEGLDisplay = eglGetDisplay(EGL_DEFAULT_DISPLAY);
EGLint eglMajVers;
EGLint eglMinVers;
eglInitialize(mEGLDisplay, &eglMajVers, &eglMinVers);

//配置EGL
EGLint attribList[] = {
    EGL_SURFACE_TYPE, EGL_WINDOW_BIT, EGL_RENDERABLE_TYPE, EGL_OPENGL_ES3_BIT,
    EGL_RED_SIZE, 8,
    EGL_GREEN_SIZE, 8,
    EGL_BLUE_SIZE, 8,
    EGL_NONE
};
eglChooseConfig(mEGLDisplay, attribList, &mEGLConfig, 1, &configsNum);

//创建EGL Surface
EGLint winAttribs[] = {EGL_GL_COLORSPACE_KHR, EGL_GL_COLORSPACE_SRGB_KHR, EGL_NONE};
mEGLSurface = eglCreateWindowSurface(mEGLDisplay, mEGLConfig, mEglWindow, winAttribs);
    
//创建EGL Context
EGLint attrib3_list[] = {
    EGL_CONTEXT_CLIENT_VERSION, 3,
    EGL_NONE
};
mEGLContext = eglCreateContext(mEGLDisplay, mEGLConfig, mSharedEGLContext, attrib3_list);
    
//绑定EGL Context和Surface
eglMakeCurrent(mEGLDisplay, mEGLSurface, mEGLSurface, mEGLContext);
    
// 创建着色点程序
const char* g_vertexShader =
    "#version 300 es\n"
    "in vec4 a_pos;\n"
    "in vec4 a_color;\n"
    "uniform mat4 a_mx;\n"
    "uniform mat4 a_my;\n"
    "out vec4 v_color;\n"
    "void main() {\n"
    "    gl_Position = a_mx * a_my * a_pos;\n"
    "    v_color = a_color;\n"
    "}";
    
const char* g_fragmentShader =
    "#version 300 es\n"
    "precision mediump float;\n"
    "in vec4 v_color;\n"
    "out vec4 fragColor;\n"
    "void main() {"
    "    fragColor = v_color;"
    "}";
    
// 创建顶点着色器
GLuint vertexShader = glCreateShader(GL_VERTEX_SHADER);
glShaderSource(vertexShader, 1, &g_vertexShader, nullptr);
glCompileShader(vertexShader);

//创建片段着色器
GLuint fragmentShader = glCreateShader(GL_FRAGMENT_SHADER);
glShaderSource(fragmentShader, 1, &g_fragmentShader, nullptr);
glCompileShader(fragmentShader);

//创建着色器程序
GLuint mProgramHandle = glCreateProgram();
glAttachShader(mProgramHandle, vertexShader);
glAttachShader(mProgramHandle, fragmentShader);
glLinkProgram(mProgramHandle);
	
//使用着色器程序
glUseProgram(mProgramHandle);
```

该示例通过EGL创建和设置整个OpenGL ES渲染环境，下面详细地解释下每个步骤。

### 使用eglGetDisplay连接渲染目标设备
```cpp
EGLDisplay eglGetDisplay(EGLNativeDisplayType display_id);
```

eglGetDisplay是EGL库中的一个函数，函数返回EGLDisplay对象，它代表了与渲染目标设备的连接，如果显示连接不可用，eglGetDisplay将返回 EGL_NO_DISPLAY，这个错误表示显示连接不可用。

display_id 参数通常是一个表示显示设备的本地显示类型，EGLNativeDisplayType是为了匹配窗口显示类型，在各个平台有不同的定义。如果您只是希望使用默认的显示设备，那么您可以直接使用 EGL_DEFAULT_DISPLAY，而不需要显式地指定 display_id。

### 使用eglInitialize初始化EGL
当成功打开连接之后则需要调用eglInitialize初始化EGL。
```cpp
EGLBoolean eglInitialize(EGLDisplay display, // 指定EGL显示连接
                         EGLint *majorVersion, // 指定EGL实现返回的主版本号，可能为NULL
                         EGLint *minorVersion);// 指定EGL实现返回的次版本号，可能为NULL
```
这个函数用于初始化EGL内部数据结构，将返回EGL的版本号，并将其保存在majorVersion、minorVersion。
如果初始化成功，则返回EGL_TRUE，否则返回EGL_FALSE。另外还可以通过EGLint eglGetError()，查询EGL的错误状态：

- EGL_BAD_DISPLAY：表示没有指定有效的EGLDisplay。

- EGL_NOT_INITIALIZED：表示EGL不能初始化。

### 使用eglChooseConfig确定渲染配置
EGL初始化成功之后，需要确定可用渲染表面的类型和配置，目前支持两种方法：
- 可以指定一组需要的配置，使用eglChooseConfig使EGL推荐最佳配置。
一般情况下使用此种方法，因为这样更容易获得最佳配置。

    ```cpp
    EGLBoolean eglChooseConfig(EGLDisplay dpy,   // EGL显示连接句柄，标识了要进行配置选择的显示连接。
                        const EGLint *attrib_list, // 一个以EGL_NONE结尾的整数数组，用于指定所需配置的属性。属性列表中的每个元素都由属性名称（如EGL_RED_SIZE）和相应的属性值组成。如{EGL_RED_SIZE, 8, EGL_GREEN_SIZE, 8, EGL_BLUE_SIZE, 8, EGL_NONE}。
                           EGLConfig *configs, // 一个用于存储选择配置的指针数组。eglChooseConfig函数将从可用配置中选择适合条件的配置，并将其存储在此数组中。
                           EGLint config_size,// configs数组的大小
                           EGLint *num_config); // 存储满足attrib_list需求，得到的满足需求的实际配置数量。
    ```

    ```cpp
    // 如以上代码所示这里指定所需配置的属性为
	EGLint attribList[] = {
            EGL_SURFACE_TYPE, EGL_WINDOW_BIT, EGL_RENDERABLE_TYPE, EGL_OPENGL_ES3_BIT,  // 指定了渲染类型为 OpenGL ES 3
            EGL_RED_SIZE, 8,    // 指定红色缓冲区的位数是8位
            EGL_GREEN_SIZE, 8,  // 指定绿色缓冲区的位数是8位
            EGL_BLUE_SIZE, 8,   // 指定蓝色缓冲区的位数是8位
            EGL_NONE
    };
    eglChooseConfig(mEGLDisplay, attribList, &mEGLConfig, 1, &configsNum);
    ```
    使用了eglChooseConfig后根据指定的配置属性attribs 将返回满足需求的配置，存放在config中。示例代码config_size传入了1，表明config数组的大小为1。只能保存一组可用配置，但那也是足够的。而numconfigs 保存满足指定配置的所有配置数量。 这样我们得到了满足我们需求的config。

- 也可以使用eglGetConfigs查询支持的所有配置，并使用eglGetConfigAttrib筛选需要的配置。
  以下提供使用此种方法得到满足需求的配置，具体可见示例：

  ```cpp
  #include <EGL/egl.h>
  #include <iostream>
  #include <vector>
  int main() {
      // 初始化 EGL
      EGLDisplay display = eglGetDisplay(EGL_DEFAULT_DISPLAY);
      eglInitialize(display, nullptr, nullptr);
  
      // 获取所有配置
      EGLint numConfigs;
      eglGetConfigs(display, nullptr, 0, &numConfigs);
      std::vector<EGLConfig> configs(numConfigs);
      eglGetConfigs(display, configs.data(), numConfigs, &numConfigs);
  
      // 选择合适的配置
      EGLConfig chosenConfig = nullptr;
      for (const auto& config : configs) {
          EGLint redSize, greenSize, blueSize;
          eglGetConfigAttrib(display, config, EGL_RED_SIZE, &redSize);
          eglGetConfigAttrib(display, config, EGL_GREEN_SIZE, &greenSize);
          eglGetConfigAttrib(display, config, EGL_BLUE_SIZE, &blueSize);
          if (redSize == 8 && greenSize == 8 && blueSize == 6) {
              chosenConfig = config;
              break;
          }
      }
  
      // 如果未选择配置，则打印错误信息并退出
      if (!chosenConfig) {
          std::cerr << "Failed to find a suitable EGL configuration." << std::endl;
          return 1;
      }
      return 0;
  }
  ```

  ```cpp
  EGLBoolean eglGetConfigs(EGLDisplay display, // EGL显示连接句柄，标识了要进行配置选择的显示连接。
                           EGLConfig *configs, // 用于保存得到配置的数组
                           EGLint config_size, // configs的数组大小
                           EGLint *num_config);// 得到的EGL所有可用配置数量
  ```
  
   eglGetConfigs接口有以下两种用法：
  
  - 当我们传递configs为nullptr时，接口会返回EGL_TRUE，并将得到的EGL所有可用配置数量保存在num_config中，这时即可根据得到的数量初始化configs来保存这些配置了，具体见如上代码。
  - 当传递configs数组接受所有配置时，将得到所有配置并保存在configs，这样即可得到所有的可用配置，接下来可以根据具体需求筛选一组config保存下来。
  
  ```cpp
  // 选择合适的配置
     EGLConfig chosenConfig = nullptr;
         for (const auto& config : configs) {
             EGLint redSize, greenSize, blueSize;
             eglGetConfigAttrib(display, config, EGL_RED_SIZE, &redSize);
             eglGetConfigAttrib(display, config, EGL_GREEN_SIZE, &greenSize);
             eglGetConfigAttrib(display, config, EGL_BLUE_SIZE, &blueSize);
             if (redSize == 8 && greenSize == 8 && blueSize == 6) {
                 chosenConfig = config;
                 break;
             }
         }
  ```
  
  如上所示遍历configs每个配置 ，使用eglGetConfigAttrib查询该配置下特定属性的值，将该值保存在第4个参数中，并判断值是否是自己需要的，如果需要则保存该配置，以待使用。调用成功则返EGL_TRUE，调用失败则返回EGL_FALSE。 如果返回EGL_FALSE，可以使用eglGetError查询失败的原因，如果返回EGL_BAD ATTRIBUTE则attribute不是有效的属性。
  
  ```cpp
  EGLBoolean eglGetConfigAttrib(EGLDisplay display, //EGL 显示连接句柄，标识了要进行配置选择的显示连接
                                     EGLConfig config,  //EGLConfig 对象，表示要查询的 EGL 配置
                                     EGLint attribute,  //EGLint 类型的属性标识符，表示要查询的属性
                                     EGLint *value);    //指向 EGLint 类型变量的指针，用于存储查询到的属性值。
  ```


### 使用eglCreateWindowSurface创建窗口表面

得到符合渲染需求的EGLConfig之后，可以使用eglCreateWindowSurface创建窗口表面。
```cpp
EGLSurface eglCreateWindowSurface(EGLDisplay dpy, // EGLDisplay对象，表示与窗口表面关联的显示连接。
                                  EGLConfig config, // EGLConfig对象，表示要创建窗口表面的EGL配置。
                                  EGLNativeWindowType win, // EGLNativeWindowType类型的参数，表示窗口的句柄或标识符，用于与EGL表面关联。
                                  const EGLint *attrib_list); // 指向EGL属性列表的指针，用于指定窗口表面的属性。是一个以EGL_NONE结尾的整数数组。
```
eglCreateWindowSurface接受的属性attrib_list的值如下所示：

```cpp
EGL_RENDER_BUFFER EGL_SINGLE_BUFFER或EGL_BACK_BUFFER
EGL_SINGLE_BUFFER // 表示渲染表面将只有一个渲染缓冲区，在绘制完成后，渲染缓冲区中的内容将直接显示到屏幕上，不会进行双缓冲，可能会出现闪烁或撕裂的现象。
EGL_BACK_BUFFER   // 表示渲染表面将具有双缓冲区，即前缓冲区和后缓冲区。在绘制完成后，渲染缓冲区中的内容首先会绘制到后缓冲区，然后通过交换缓冲区的操作将后缓冲区的内容显示到屏幕上，这样可以避免闪烁和撕裂现象。
// 默认情况下是EGL_BACK_BUFFER，当设置为null，则为默认属性。
```
eglCreateWindowSurface创建窗口表面失败的可能如下：

- EGL_BAD_MATCH：表示窗口属性与提供的 EGLConfig 不匹配。这可能是因为EGLConfig不支持渲染到窗口（即EGL_SURFACE_TYPE 属性没有设置为 EGL_WINDOW_BIT）。

- EGL_BAD_CONFIG：如果提供的EGLConfig没有得到系统的支持，则会发生这种错误。

- EGL_BAD_NATIVE_WINDOW：如果提供的窗口句柄无效，则会发生这种错误。

- EGL_BAD_ALLOC：如果eglCreateWindowSurface无法为新的EGL窗口分配资源，或者已经有与提供的窗口关联的EGLConfig，则会发生这种错误。



```cpp
EGLint attribList[] = { EGL_RENDER_BUFFER, EGL_BACK_BUFFER, EGL_NONE };
EGLSurface surface = eglCreateWindowSurface(display, config, nativeWindow, attribList);
if (surface == EGL_NO_SURFACE) {
    switch (eglGetError()) {
        case EGL_BAD_MATCH:
            // 检查窗口和 EGLConfig 属性以确定兼容性，或者验证 EGLConfig 是否支持渲染到窗口
            break;
        case EGL_BAD_CONFIG:
            // 验证提供的 EGLConfig 是否有效
            break;
        case EGL_BAD_NATIVE_WINDOW:
            // 验证提供的 EGLNativeWindow 是否有效
            break;
        case EGL_BAD_ALLOC:
            // 资源不足；处理并恢复
            break;
        default:
            // 处理任何其他错误
            break;
    }
}
```
在使用XComponent获取nativeWindow的过程中，通常涉及以下步骤：
1. 首先需要在ArkTS 中定义XComponent并设置 XComponentController。XComponent组件用于在UI中嵌入渲染内容如OpenGL或Vulkan。
```typescript
Column() {
    XComponent({
        id: 'myXComponent',
        type: XComponentType.SURFACE,
        controller: this.xComponentController
    })
}
```
2. 创建 XComponentController子类，实现回调方法：
```typescript
class MyXComponentController extends XComponentController {
    onSurfaceCreated(surfaceId: string): void {
        console.info(`onSurfaceCreated surfaceId: ${surfaceId}`);
        nativeRender.SetSurfaceId(BigInt(surfaceId));
        // 之后会使用 surfaceId 关联 native window
    }

    onSurfaceChanged(surfaceId: string, rect: SurfaceRect): void {
        console.info(`onSurfaceChanged surfaceId: ${surfaceId}`);
    }
    
    onSurfaceDestroyed(surfaceId: string): void {
        console.info(`onSurfaceDestroyed surfaceId: ${surfaceId}`);
    }
}
```
3. 使用surfaceId获取NativeWindow：
surfaceId是在XComponent创建过程中生成的。在onSurfaceCreated 回调中，可以使用OH_NativeWindow_CreateNativeWindowFromSurfaceId函数通过surfaceId获取nativeWindow。
```cpp
napi_value PluginManager::SetSurfaceId(napi_env env, napi_callback_info info)
{
    int64_t surfaceId = ParseId(env, info);
    OHNativeWindow *nativeWindow;
    PluginRender *pluginRender;
    if (windowMap_.find(surfaceId) == windowMap_.end()) {
        OH_NativeWindow_CreateNativeWindowFromSurfaceId(surfaceId, &nativeWindow);
        windowMap_[surfaceId] = nativeWindow;
    } else {
        return nullptr;
    }
    if (pluginRenderMap_.find(surfaceId) == pluginRenderMap_.end()) {
        pluginRender = new PluginRender(surfaceId);
        pluginRenderMap_[surfaceId] = pluginRender;
    }
    pluginRender->InitNativeWindow(nativeWindow);
    return nullptr;
}
```
<!--Del-->
有关ArkTS XComponent 组件的使用，请参考：[ArkTS XComponent组件使用示例](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/Native/XComponent/README_zh.md#)。
<!--DelEnd-->

### 使用eglCreateContext创建渲染上下文 

eglCreateContext函数用于创建一个新的EGL上下文，并将其与特定的显示设备（display）和配置（config）关联起来。允许指定共享上下文（shareContext），以便与已经存在的OpenGL上下文共享状态信息。该函数的参数说明如下：

```cpp
EGLContext eglCreateContext(EGLDisplay display, // EGLDisplay类型，表示要创建上下文的EGL显示连接。
                            EGLConfig config,   // EGLConfig类型，表示与上下文关联的EGL配置。
                            EGLContext shareContext, // EGLContext类型，表示要与新创建的上下文共享状态信息的现有上下文。如果不想共享状态信息，可以传递EGL_NO_CONTEXT。
                            const EGLint *attribList); // 指向属性列表的指针，用于指定上下文的属性。属性列表是以EGL_NONE结尾的一系列属性值对。
```
eglCreateContext 的attribList属性列表如下：
```cpp
EGLint attrib3_list[] = {
    EGL_CONTEXT_CLIENT_VERSION, 3, //指定使用的openglES版本3相关的上下文类型
    EGL_NONE
};
```

eglCreateContext 创建渲染上下文失败的可能为：EGL_BAD_CONFIG，即提供的EGLconfig无效。

### 使用eglMakeCurrent将EGL上下文与绘图表面进行关联

```cpp
EGLBoolean eglMakeCurrent(EGLDisplay display, // EGL显示连接的句柄，用于标识渲染设备。
                          EGLSurface draw,    // EGL绘图表面的句柄，指定要渲染到的目标表面。
                          EGLSurface read,    // EGL读取表面的句柄，用于像素读取等操作。通常情况下，可以将其设为与 draw 相同的值。
                          EGLContext context);// 要与指定表面关联的 EGL 上下文的句柄。
```

### 创建并使用着色器程序

```cpp
// 创建顶点着色器
GLuint vertexShader = glCreateShader(GL_VERTEX_SHADER);
glShaderSource(vertexShader, 1, &g_vertexShader, nullptr);
glCompileShader(vertexShader);

// 创建片段着色器
GLuint fragmentShader = glCreateShader(GL_FRAGMENT_SHADER);
glShaderSource(fragmentShader, 1, &g_fragmentShader, nullptr);
glCompileShader(fragmentShader);

// 创建着色器程序
mProgramHandle = glCreateProgram();
glAttachShader(mProgramHandle, vertexShader);
glAttachShader(mProgramHandle, fragmentShader);
glLinkProgram(mProgramHandle);

// 使用着色器程序
glUseProgram(mProgramHandle);
```

```cpp
GLuint glCreateShader(GLenum shaderType);
```
glCreateShader用于创建一个指定类型（顶点着色器、片段着色器等）的着色器对象，并返回该对象的句柄。其中shaderType参数指定要创建的着色器类型，可以是GL_VERTEX_SHADER（顶点着色器）或 GL_FRAGMENT_SHADER（片段着色器）等。

```cpp
void glShaderSource(GLuint shader, GLsizei count, const GLchar \**string, const GLint *length);
```

glShaderSource函数用于设置着色器对象的源代码。其中各参数含义如下：

- shader：要设置源代码的着色器对象的标识符。
- count：源代码字符串的数量。
- string：指向源代码字符串的指针数组。
- length：指向包含每个源代码字符串长度的整数数组，可以为nullptr，表示每个字符串都以null结尾。

```cpp
void glCompileShader(GLuint shader);
```

glCompileShader函数用于编译指定的着色器对象，其中shader参数是要编译的着色器对象的标识符。

```cpp
GLuint glCreateProgram(void);
```

glCreateProgram函数用于创建一个新的着色器程序对象，该函数返回一个新创建的着色器程序对象的标识符。

```cpp
void glAttachShader(GLuint program, GLuint shader);
```

glAttachShader函数用于将一个着色器对象附加到一个着色器程序对象上，参数program是目标着色器程序对象的标识符，参数shader是要附加的着色器对象的标识符。

```cpp
void glLinkProgram(GLuint program);
```

glLinkProgram函数用于链接一个着色器程序对象，将附加到该程序对象的着色器链接成一个可执行的渲染管线。

参数program是要链接的着色器程序对象的标识符。链接着色器程序时，OpenGL将会执行以下操作：将各个着色器对象中的代码合并成一个可执行的渲染管线。执行连接器优化，以优化渲染管线的性能。并将Uniform变量和Uniform块的信息进行绑定。

```cpp
void glUseProgram(GLuint program);
```
glUseProgram函数用于激活指定的着色器程序对象。在调用glUseProgram 之后，所有的渲染调用将会使用该着色器程序进行处理。

在使用glCompileShader时可以使用以下代码检查是否正常。

```cpp
// 编译着色器
glCompileShader(shader);

// 检查编译状态
glGetShaderiv(shader, GL_COMPILE_STATUS, &compiled);

if (!compiled)
{
    GLint infoLen = 0;

    // 获取着色器信息日志的长度
    glGetShaderiv(shader, GL_INFO_LOG_LENGTH, &infoLen);

    if ( infoLen > 1 )
    {
        // 分配存储信息日志的内存
        char *infoLog = malloc(sizeof(char) * infoLen);

        // 获取并打印着色器信息日志
        glGetShaderInfoLog(shader, infoLen, NULL, infoLog);
        esLogMessage("Error compiling shader:\n%s\n", infoLog);

        // 释放分配的内存
        free(infoLog);
    }

    // 删除编译失败的着色器
    glDeleteShader(shader);
    return 0;
}
```

在使用glLinkProgram可使用如下代码检查是否正常。

```cpp
// 链接程序对象
glLinkProgram(programObject);

// 检查链接状态
glGetProgramiv(programObject, GL_LINK_STATUS, &linked);

if (!linked)
{
    GLint infoLen = 0;

    // 获取程序对象信息日志的长度
    glGetProgramiv(programObject, GL_INFO_LOG_LENGTH, &infoLen);

    if (infoLen > 1)
    {
        // 分配存储信息日志的内存
        char *infoLog = malloc(sizeof(char) * infoLen);

        // 获取并打印程序对象的信息日志
        glGetProgramInfoLog(programObject, infoLen, NULL, infoLog);
        esLogMessage("Error linking program:\n%s\n", infoLog);

        // 释放分配的内存
        free(infoLog);
    }

    // 删除链接失败的程序对象
    glDeleteProgram(programObject);
    return FALSE;
}
```

<!--RP1--><!--RP1End-->

## 相关实例

针对OpenGL ES的使用和相关开发，有以下相关实例可供参考：

- [简易Native C++示例](https://gitcode.com/openharmony/codelabs/tree/master/NativeAPI/NativeTemplateDemo)
- [Native XComponent组件的使用](https://gitcode.com/openharmony/codelabs/tree/master/NativeAPI/XComponent)
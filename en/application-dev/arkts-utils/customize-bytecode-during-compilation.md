---
kits: ["ArkTS Kit"]
description: "Introduces the capability configuration, execution mechanism, and development examples for loading a shared library through the transformLib compilation option to perform custom modifications such as instrumentation on the generated Ark bytecode file during compilation."
keywords: [Ark bytecode, compile-time modification, transformLib, bytecode instrumentation, Transform method, shared library, build-profile.json5]
doctype: guide
status: active
---

# Customizing Ark Bytecode During Compilation
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @oatuwwutao-->
<!--Designer: @oatuwwutao-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=17ae88719a2d37a0c07e3b6e33ddb120ebd3dbc5 translatedAt=2026-11-06T10:33:39.551Z pushedAt=2026-11-12T03:42:54.795Z nl=1 -->

You can modify Ark bytecode files using the customization capabilities provided by the ArkTS compilation toolchain.

## Configuration

Prepare a shared library file that operates on Ark bytecode files, and configure the [transformLib compilation option](arkoptions-guide.md#transformlib) in the project configuration file build-profile.json5, with the option value set to the path of this shared library. During compilation, the compiler loads the shared library, invokes its Transform method, and unloads the shared library after the Transform method finishes executing.

## Execution

If transformLib is configured and the corresponding dynamic library file can be loaded correctly, the compiler first generates the Ark bytecode file to the default target location, then invokes the Transform method in the dynamic library and passes the path of the Ark bytecode file as a parameter. The Transform method contains developer-defined modification logic for instrumenting or otherwise modifying the Ark bytecode file passed in by the compiler. In the Transform method, developers need to write the modified content back to the Ark bytecode file passed in by the compiler through the bytecode file write interface. When a single compilation generates multiple Ark bytecode files, the compiler invokes the Transform method separately for each Ark bytecode file and passes the path of the current file. In projects that include cards, the Ark bytecode files corresponding to the cards also support instrumentation.

Below is a template for a dynamic library, which you can use to implement the specific logic for the **Transform** method as required.

## How to Develop

1. Create the source code for the dynamic library.

   example.cpp:

   ```c++
   #include <cstdlib>

   /**
    * @brief Entry method for modifying the Ark bytecode file.
    * @param abc_path Path for storing the Ark bytecode file to be processed.
    * @return Returns 0 (EXIT_SUCCESS) if the bytecode file is modified successfully, and returns a non-zero value if the modification fails.
    */
   extern "C" int Transform(const char *abc_path)
   {
       // You can read the Ark bytecode file corresponding to abc_path, modify related data based on the Ark bytecode format, and generate a new Ark bytecode file.
       return EXIT_SUCCESS;
   }
   ```

2. Use a C language compiler (g++) to compile the dynamic library.

   Windows:

   ```bash
   g++ --shared -o example.dll example.cpp
   ```

   Linux:

   ```bash
   g++ --shared -o example.so example.cpp
   ```

   macOS:

   ```bash
   g++ --shared -o example.so example.cpp
   ```

3. In DevEco Studio, configure the **transformLib** option in the **build-profile.json5** file. (The following uses the Windows environment as an example.)

   Set the option to the path of the link library file generated in step 2. In this example, the path is in the **dll** directory.

   ![image_0000002079773605](figures/image_0000002079773605.png)

4. Recompile the project to customize the Ark bytecode.

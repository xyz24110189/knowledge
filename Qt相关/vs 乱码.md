## visual stdio 与 qt 集成乱码问题
* vs2015 及之后版本解决方案
  * **Specifies both the source character set and the execution character set as UTF-8.**

    ### Syntax
    `/utf-8`
    
    ### Remarks
    You can use the /utf-8 option to specify both the source and execution character sets as encoded by using UTF-8. It is equivalent to specifying /source-charset:utf-8 /execution-charset:utf-8 on the command line. Any of these options also enables the /validate-charset option by default. For a list of supported code page identifiers and character set names, see Code Page Identifiers.

    By default, Visual Studio detects a byte-order mark to determine if the source file is in an encoded Unicode format, for example, UTF-16 or UTF-8. If no byte-order mark is found, it assumes the source file is encoded using the current user code page, unless you have specified a code page by using /utf-8 or the /source-charset option. Visual Studio allows you to save your C++ source code by using any of several character encodings. For information about source and execution character sets, see Character Sets in the language documentation.

    **To set this compiler option in the Visual Studio development environment**
    
    Open the project Property Pages dialog box. For more information, see Set C++ compiler and build properties in Visual Studio.

    Expand the Configuration Properties, C/C++, Command Line folder.

    In Additional Options, add the /utf-8 option to specify your preferred encoding.

    Choose OK to save your changes.
    
    
* vs2010中作为编译器和IDE编写Qt程序时，中文会出现乱码，解决方法如下：

  * 在头文件中包含如下语句

  ```
    #if _MSC_VER >= 1600
    #pragma warning(disable:4068)                /** 去unknown pragma警告 */
    #pragma execution_character_set("utf-8")
    #endif
  ```

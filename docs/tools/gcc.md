# GCC

> GCC mean is  GNU C Compiler 
 GNU Compiler Collection
 support Ada、C、C++、Java、Objective C、Pascal 、COBOLas well as support functional programming and logic programing Mercury and more!

### 编译过程是分为四个阶段进行:
- 预处理(也称预编译，Preprocessing)
- 编译(Compilation)
- 汇编 (Assembly)
- 连接(Linking)

usage command gcc or cc; 
gcc one.c -o test
### Preprocessing
    gcc -E one.c -o test.i 或 gcc -E test.c
>可以输出test.i文件中存放着test.c经预处理之后的代码。打开test.i文件，看一看，就明白了。后面那条指令，是直接在命令行窗口中输出预处理后的代码.预处理之后，可直接对生成的test.i文件编译，生成汇编代码

### 编译为汇编代码(Compilation)
    gcc -S test.i -o test.s
>gcc的-E选项，可以让编译器在预处理后停止，并输出预处理结果。在本例中，预处理结果就是将stdio.h 文件中的内容插入到test.c中了。

    gcc -c source_file.c
-c，只执行到编译，输出目标文件。

-s, 生成与运用strip同样效果的可执行文件删除了所有符号信息。
-O（大写的字母O），编译器对代码进行自动优化编译，输出效率更高的可执行文件。
-O 后面还可以跟上数字指定优化级别，如：-O2 default O2 O3 have risk

gcc one.c -L/path/to/lib -lxxx -I/path/to/include
-l, 指定所使用到的函数库，本例中链接器会尝试链接名为libxxx.a的函数库。
-L，指定函数库所在的文件夹，本例中链接器会尝试搜索/path/to/lib文件夹。
-I, 指定头文件所在的文件夹，本例中预编译器会尝试搜索/path/to/include文件夹。
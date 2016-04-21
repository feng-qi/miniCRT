#《程序员的自我修养》中miniCRT源码分析
window 下
>cl /c /DWIN32 /GS- entry.c malloc.c printf.c stdio.c string.c

>lib entry.obj malloc.obj printf.obj stdio.obj string.obj /OUT:minicrt.lib
>cl /c /DWIN32 test.c
>link test.obj minicrt.lib kernel32.lib /NODEFAULTLIB /entry:mini_crt_entry

linux 下

# gcc -c -fno-builtin -nostdlib  entry.c malloc.c stdio.c string.c printf.c
# ar -rs minicrt.a malloc.o printf.o stdio.o string.o
# gcc -c -ggdb -fno-builtin -nostdlib test.c
# ld -static -e mini_crt_entry entry.o test.o minicrt.a -o test

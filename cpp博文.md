
[const T、const T*、T *const、const T&、const T*& 的区别](http://www.bubuko.com/infodetail-794302.html)<br>
[malloc、calloc、realloc以及new的区别与联系](https://blog.csdn.net/jiejinquanil/article/details/51793315)<br>
malloc：头文件stdlib.h/malloc.h。函数原型void* malloc (size_t size)。动态申请size大小的内存，**不初始化**，返回指针。</br>
calloc：头文件stdlib.h/malloc.h。函数原型void* calloc (size_t num, size_t size)。动态申请num个大小为size的内存，
**初始化为0**，返回指针。</br>
realloc：头文件stdlib.h/malloc.h。函数原型void* realloc (void* ptr, size_t size)。


[const T、const T*、T *const、const T&、const T*& 的区别](http://www.bubuko.com/infodetail-794302.html)<br>
1.const T：定义一个**常量**，声明时*必须初始化*，一旦声明不能改变。<br>
2.const T* ：指向常量的**指针**，不能改变所指对象的值。<br>
const int* a和int* const b的区别：a本身可以改变，但是* a不可以改变，b本身不可以改变，但是* b可以改变。const int* const c:则c和* c都不能改变<br>
3.const T&：常量引用，一个别名，本身的值不能有自己赋值改变，但是所引用的对象（也许）可以改变。<br>
const T*& a和 T* const& b:和上面的a，b性质相同，尽多了个引用符，初始化时需要赋值为不带引用符的对象。<br>

[malloc、calloc、realloc以及new的区别与联系](https://blog.csdn.net/jiejinquanil/article/details/51793315)<br>
malloc：头文件stdlib.h/malloc.h。函数原型void* malloc (size_t size)。动态申请size大小的内存，**不初始化**，返回指针。</br>
calloc：头文件stdlib.h/malloc.h。函数原型void* calloc (size_t num, size_t size)。动态申请num个，大小为size的内存，
**初始化为0**，返回指针。</br>
realloc：头文件stdlib.h/malloc.h。函数原型void* realloc (void* ptr, size_t size)。动态申请大小为size的内存，返回一个指针，可能指向**新**的地址，也可能指向**原来**的地址。如果ptr是空，则等同于malloc函数。即使块被移动到新的位置，内存块的内容也被**保留**到（新和旧中）较小的块中。<br>
new：c++关键字。获得内存空间，调用构造函数，返回正确的指针。如果说简单变量，不调用构造函数。<br>

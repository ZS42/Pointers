# Pointers

Types of Pointers

restrict
example in memcpy it means you are promising the computer that dst and src dont overap ie there is no 'aliasing' of the pointer 
see
https://www.quora.com/What-is-restrict-in-C-programming-Can-you-explain-and-give-an-example

constant char*
This is read pointer to constant char. It means value pointed to b pointer is constant but pointer can point to another const char*
ie the value of the pointer can be changed

char* const
This is read constant pointer to char. It means value pointed at can change  but pointer value cant change ie it cant point to another char.

const char* const
This is read as constant pointer to constant char. In tis case both value and value of pointer cant be changed

Purpose of pointer to pointer:
https://stackoverflow.com/questions/20281669/why-and-when-is-a-double-pointer-required
https://stackoverflow.com/questions/20281669/why-and-when-is-a-double-pointer-required

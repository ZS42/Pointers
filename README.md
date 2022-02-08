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

Function pointers
// fun_ptr is a pointer to function fun() 
    void (*fun_ptr)(int) = &fun;
  
    /* The above line is equivalent of following two
       void (*fun_ptr)(int);
       fun_ptr = &fun; 
    */
  
    // Invoking fun() using fun_ptr
    (*fun_ptr)(10);
       
     void (*fun_ptr)(int) = fun;  // & removed
  
    fun_ptr(10);  // * removed 
    see
    https://www.geeksforgeeks.org/function-pointer-in-c/
    
    C
In C, double pointers are more common, since C does not have a reference type. Therefore, you also use a pointer to "pass by reference." Where & is used in a parameter type in the C++ examples above, * would be used in C (and dereferenced when manipulating the parameter). One example:

void squareRoots(double in, double *plus, double *minus)  //pass double "by reference"
{
  *plus = sqrt(in);
  *minus = -*plus;
}

6

You pass a pointer to pointer as argument when you want the function to set the value of the pointer.

You typically do this when the function wants to allocate memory (via malloc or new) and set that value in the argument--then it will be the responsibility of the caller to free it. It is better than returning it as a function return value, because there is no possibility of the caller ignoring the return value by mistake and causing a leak by not freeing it.

You might also want to use this if you are returning multiple values.

Another reason to do this is when you want to make want to return the value optionally (ie the pointer to pointer can be NULL). For example, look at strtol() it has an optional endptr.

Note: you should never set this pointer to a stack variable.



3

You would use <type>** when you want to pass an array of pointers.
Example:

int main(int argc, char **argv) {   // argv is an array of char*
You would also use it if you want to be able to change the pointer address (in C++ you could pass a pointer reference instead in this case).

What hasn't been mentioned is dynamically allocating 2D array - essentially, you would have an array of pointers pointing to other pointers.



This maybe my opinions. But pointers should be used for a variable when you expect that you will use NULL as a perfect value, e.g., in a linked list. References should be used when you don't expect to initialize your value to NULL. Otherwise, references and pointers are similar in many ways. You can change value of a pointer or by-reference parameter from inside a function. They are both polymorphic. ...


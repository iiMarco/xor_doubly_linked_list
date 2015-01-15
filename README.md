# XOR Doubly Linked List

Implementation of a generic 'XOR Doubly Linked List', or 'Memory Efficient Doubly Linked List', in C.
The default storage type is ```c void *``` but can be changed to any other data type pointer for simplicity
by editting the ```xordll.h``` file and changing the following line:

```c
/** @XORItem Generic Type **
 *
 *  Change as needed!
 *  N.B. Only store pointers since @XORList does not
 *  store local copies.
 */
typedef void XORItem;
```

This implementation also comes with a bi-directional iterator to make traversals simplified.

Example of use:

```c
#include "xordll.h"
int main()
{
    int  a = 1,b = 2,c = 3, d = 4, e =5;
    XORList * list = xorlist_create();

    xorlist_push_back(list, &a);
    xorlist_push_back(list, &b);
    xorlist_push_back(list, &c);
    xorlist_push_back(list, &d);
    xorlist_push_back(list, &e);

    printf("%p %p %p %p %p\n",&a,&b,&c,&d,&e);

    XORListIterator itr = xorlist_iterator_reverse(list);

    for( ;
        xorlist_iterator_has_next(&itr);
        xorlist_iterator_next(&itr)) {

        printf("Current : %p\n",xorlist_iterator_curr(&itr));
    }

    for(xorlist_iterator_prev(&itr);
        xorlist_iterator_has_prev(&itr);
        xorlist_iterator_prev(&itr)) {

        printf("Current : %p\n",xorlist_iterator_curr(&itr));
    }

    xorlist_destroy(list);

    return 0;
}
```

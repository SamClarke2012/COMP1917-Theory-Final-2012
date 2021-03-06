# COMP1917-Theory-Final-2012

= COMP1917 Final Exam 2012s1 =

== Afternoon ==

== Time allowed: 2.5 Hours ==

== Total number of questions: 21 ==

== Total number of marks: 100 ==


Write your answers in the text boxes in this application.
Your answers can be submitted by pressing save on this application.

You may submit your solutions as many times as you like. The last submission
ONLY will be marked.

You have to check that the answers are saved successfully by looking
at the line at the bottom which should say "Saved and Submitted".
If it say "Saving..." call the invigilator for assistance.

Write your name on the top of each sheet of rough working paper you use,
this will not be marked.

You must hand in ALL writing paper at the end of the exam.

You may only use this application for entering your answers and the
pdf viewer for the textbook. Compilers or other software tools may not be used.
Calculators may not be used. The eating of toast in the exam room is prohibited.
You must not attempt to communicate with any other person, or access other computers
or any internet resources. If you do not follow these instructions you will get
zero marks for the exam and a possible charge of academic misconduct.

Unless advised otherwise you may not use any language features or library
functions not covered in class. Code which does not comply with the course
style guide, or which is overly complex or unclear will be penalised.

Questions (and sub-questions) are not worth equal marks. Answer all
questions.

== PART A: Multiple Choice and Short Answer Questions ==

Your working is not marked in Part A. Questions are not all of equal value.
Keep your answers clear and very brief. Messy or long answers will not be
marked.

=== Question 0 ===
(2 Marks)

Consider the following C definition:


```c
char str[] = "Hello World?";
```

The size of the array str in characters is:
 
+ [A] 12
+ **[B] 13 - Don't forget double quotes come with a '\0' char**
+ [C] 24
+ [D] 26
+ [E] None of the above

 
=== Question 1 ===
(2 Marks)

Consider the following C code:
```c
char *s = "dcba";
```

What is the value of s[4]?

+ [A] 'a'
+ [B] 0
+ [C] segmentation violation
+ [D] 4
+ **[E] None of the above - resolves the NULL char '\0'. Technically this is zero, but the type of value is undefined.  Assuming value as char**


=== Question 2 ===

(2 Marks)

Consider the following C code:
```c
int i;
int *x = malloc(10*sizeof(int));
for(i=0; i<5; i++) {
   x[i] = i*i;
}
```

What is the value of *(&x[2]+1)? 

+ [A] 0
+ [B] 1
+ [C] 4
+ **[D] 9 - Dereferenced value at pointer (x[2])+1)**
+ [E] None of the above


=== Question 3 ===

(2 Marks)

Given the following fragment of code

```c
int b = 2;
int a = 1;
int *p = NULL;
p = &a;
*p = 3;
p =&b;
*p = b;
printf("%d\n",a);
```

What will this program print out?

+ [A] 1
+ [B] 2
+ **[C] 3**
+ [D] 4
+ [E] None of the above

=== Question 4 ===

(3 Marks)

Given the following fragment of code

```c
typedef struct _complex *Complex;
typedef struct _complex {
   double real;
   double imaginary;
} complex;

Complex add (complex a, complex b){
   complex answer;
   answer.real = a.real + b.real;
   answer.imaginary = a.imaginary + b.imaginary;
   return &answer;
}

complex a = {1.0,2.0};
complex b = {3.0,4.0};
Complex c;
Complex d;
c = add(b,a);
d = add(*c,a);
```


What will the value of d->real after executing this code?

+ [A] 1.0
+ [B] 3.0
+ [C] 5.0
+ **[D] It is undefined - New struct created in function stack frame, destroyed upon return**
+ [E] None of the above


=== Question 5 ===

(3 Marks)

Consider the following code fragment:

```c
   int x[] = {0, 1, 2, 3};
   int temp;
   int i;
   int j = (sizeof (x)/sizeof (int)) - 1;
   for (i = 0; i < j; i++) {
      temp = x[i];
      x[i] = x[j];
      x[j] = 2*temp;
      j--;
   }
```

After this code is executed, array x contains the values:

+ **[A] {3, 2, 2, 0}**
+ [B] {0, 1, 2, 3}
+ [C] {3, 2, 1, 0}
+ [D] It is undefined
+ [E] None of the above

=== Question 6 ===

(3 Marks)

Consider the following definitions for a List (note that we are keeping
track of the last element of the list).
```c
typedef struct _list *List;
typedef struct _node *nodePointer;

typedef struct _node {
  item value;
  nodePointer next; 
} node;

typedef struct _list {
  nodePointer first; 
  nodePointer last; 
} list;
```

Here is a fragment of code that I wrote to add a value `v` to the end
of the list in the case where the list has at least one element.
```c
addToEndOfNonemptyList(List l, int v){
   nodePointer temp;
   assert(l->last != NULL);

   temp->value = v;             //Line 1
   temp = malloc(sizeof(node)); //Line 2 
   l->last = temp;              //Line 3
   l->last->next = temp;        //Line 4
   temp->next = NULL;           //Line 5
}
```

Of course, as you all know I make lots of mistakes in my programs and
the five numbered lines in the code above might have to be rearranged
to make my function work properly.  What is an ordering of the five
numbered lines of code that makes the function correct?

+ [A] 1, 2, 3, 4, 5
+ **[B] 2, 1, 3, 4, 5**
+ [C] 2, 5, 1, 4, 3
+ [D] 2, 1, 5, 3, 4
+ [E] None of the above


=== Question 7 ===

(3 Marks)

Which of the following code fragments calculates the product of the
first N values in a an array declared like this:
```c
int a[N];
int product;
int i;
```

+ [A]  
```c
product = 1;
for (i = 0; i <= N; i++) {
   product *= a[i];
}
```
+ [B] 
```c
product = 0;
for (i = 0; i <= N; i++) {
   product *= a[i];
}
```
+ [C] 
```c
product = 0;
for (i = 1; i <= N-1; i++) {
   product *= a[i];
}
```
+ **[D] - Watch the fence posts! - zero goes with less than, and product must = 1.**
```c
product = 1;
for (i = 1; i <= N-1; i++) {
   product *= a[i];
}
```
+ [E] None of the above



=== Question 8 ===

(3 Marks)

What is the output of the following 4003 program? (I've added comments
giving the address and meaning of each instruction.)
```asm
1 //0 R0++
1 //1 R0++
3 //2 R1++
3 //3 R1++
2 //4 R0--
3 //5 R1++
3 //6 R1++
8 4 //7 if R0 != 0 goto 4
5 //9 R0<->R1
7 //10 Print R0
0 //11 Halt
```

+ [A] 0
+ [B] 2
+ [C] 4
+ **[D] 6**
+ [E] None of the above

=== Question 9 ===

(3 Marks)

Given the following fragment of code

```c
#define N 6
int i;
char a[N];
for (i = 0; i < N-1; i++){
    a[i] = 'A' + i;
}
a[2] = '\0';
printf("%c\n",a[1+strlen(a)]);
```

What will this program print out?

+ [A] A
+ [B] B
+ [C] C
+ **[D] D - strlen counts to NULL, chars still in memory**
+ [E] None of the above

=== Question 10 ===

(3 Marks)

Consider the following code fragment:

```c
int g(int *x, int y, int z){
   z = *x;
   *x = y;
   y = z*z;
   return z+y;
}

int f(int *x, int y, int *z) {
   return g(&y, *z, *x);
}

int x = 1;
int y = 2;
int z = 3;
x = f(&z, x, &y);
```

After this code is executed, x has the value:
+ [A] 1
+ **[B] 2 - Follow the the values, g() simplifies to x+x^2 - f() just swaps things around 1+1^2 = 2**
+ [C] 3
+ [D] 4
+ [E] None of the above


=== Question 11 ===

(3 Marks)

Consider the following code:
```c
// insert a value into the first position in an array,
//moving everthing else up to make room
void insert(int a[], int *size, int value) {
   int i;
   for(i=0; i < *size; i++){
      a[i+1] = a[i];
   }
   a[0] = value;
   *size++;
}
```

What is the main point you would raise in reviewing the above code?

**a[i+1] will overflow when i reaches size-1 since i is used to index array directly - Fence post error**



=== Question 12 ===

(4 Marks)

Given the following code:

```c
char str[] = "a dog!";
int len = strlen(str);
str[len] = '\n';
str[len+1] = '\0';
printf("%s\n",str);
```

What is the main point you would raise in reviewing the above code?

**'\0' is overwritten with '\n', will run mostly because of '\0' left in following memory addr, however it isn't defined**
**as part of str any more, therefore if that particular addr is overwritten, it will break**

What result would you expect from compiling/running the program and why?
**As above, will run at first, but future reliability is undefined**


== PART B: Programming I ==

Make your answers as clear and easy to understand as possible. Provide brief
comments in your code where necessary. Confusing or illegible solutions will
lose marks.

If you do not wish your answer for a question to be marked, write 1 SYMPATHY
MARK PLEASE in the space for the answer. If you do this you will be awarded
one sympathy mark and your answer for that question will not be marked.

=== Question 13 ===

(6 Marks)

Write a function with prototype
```c
int drawBox(int n);
```

that draws a hollow box n characters wide and high using '*' and ' '
characters.
For example `drawBox(4)` should produce
```c
****
*  *
*  *
****
```

```c
void draw( int n ){
    int i = 0;
    // For each row
    while( i < n ){
        // If first or last 
        if( i == 0 || i == n-1){
            int c = 0;
            // Print bar of stars
            while( c < n ){
                printf("*");
                c++;
            }
            // New row
            printf("\n");
        // Otherwise, for mid sections
        } else {
            int c = 0;
            // Do stars and spaces
            while( c < n ){
                if( c == 0 || c == (n-1)){
                    printf("*");
                } else {
                    printf(" ");
                }
                c++;
            }
            // New row
            printf("\n");
        }
        i++;
    }
}
```

=== Question 14 ===

(5 Marks)

C has a library function called isalnum that returns 1 if a character
is a letter or a number.  Without using isalnum or any other functions from
the ctype.h library, write a function that tests if a character is a
letter or a number. You should use the following
prototype.

```c
int isAlNum (char c);
```

```c
int isAlNum( char c ){
    int ans;
    // Numerical?
    if( c >= '0' && c <= '9'){
        ans = 1;
    // Uppercase?
    } else if( c >= 'A' && c <= 'Z'){
        ans = 1;
    // Lowercase?
    } else if( c >= 'a' && c <= 'z'){
        ans = 1;
    // None of those...
    } else {
        ans = 0;
    }
    return ans;
}
```
Or alternatively  (style guide dependant)

```c
int isAlNum( char c ){
    int ans;
    if( ( c >= '0' && c <= '9' ) ||
        ( c >= 'A' && c <= 'Z' ) ||
        ( c >= 'a' && c <= 'z'))  {
        ans = 1;
    } else {
        ans = 0;
    }
    return ans;
}
```
=== Question 15 ===

(7 Marks)

Write out the contents of a small file twos.c which complies with the course
style guide and, when compiled and executed on a lab machine with the
commands:
{{{
gcc -Wall -Werror -o twos twos.c
./twos
}}}

reads in a number N and prints out the number of times it can be halved
before obtaining an odd number.

For example given 5 it would print 0 (as 5 is itself odd), and given 12 it
would print 2 (as half of twelve is six, and half of six is three, which is
odd, hence 12 can be halved twice.)

{{{
$ ./twos 
5
0
$ ./twos 
6
1
$ ./twos 
12
2
$ ./twos 
64
6
}}}

You may assume that N is a positive integer between 1 and 1,000,000.

```c
int main( int argc, char **argv ){
    long long cnt = 0;
    long long val = 0;
    // Get number from User
    scanf("%lld", &val);
    // Whilst it's even
    while( (val % 2) == 0 ){
        // Divide it and count
        val /= 2;
        cnt++;
    }
    // Print the count
    printf("%lld\n",cnt);
    return EXIT_SUCCESS;
}
```

# EECS 183 Style Guide

Following consistent code style guidelines:

- Helps other people read and understand your code
- Helps you make fewer mistakes
- Is important when more than one person is working on a project

**The code style in EECS 183 projects will be graded against the following guidelines**:

[TOC]

省流版本:

1. project开头要注释
2. 所有注释单独写一行，不允许和代码写在同一行
3. 运算符前后空格，括号和变量间不允许空格
4. **一行只允许定义一个变量，只允许写一个statement (if(...)和{...}不能写同一行)**
5. 一行字符数量太多了要换行(超过80)
6. 变量如果有初始值一定要在定义的时候assign，不要后面再assign
7. 嵌套的虚拟变量顺序一定要先 `i` 再 `j` 再 `k`.
8. 不允许 `if(...==True/Flase)`，必须 `if(...)` 或者 `if(!...)`.
9. 不允许 `if(...){return True} else(){return False}`, 必须 `return ...` (直接根据bool value来返回)
10. 有精度变化或者意义变化的constant必须单独定义, 不能在变量表达式里看见constant直接和variable运算
11. 定义变量名必须是 “snake-case”形式 (`int course_credits = 4;`) 或者 “camel case” 形式 ( `int courseCredits = 4;`).
12. 定义常数必须所有字母大写
13. 定义类的类名首字母必须大写 (`class CityBus { };`).
14. 不允许用global variable, 但可以用global constant.
15. **函数一定要有RME**, 并且一定要在prototype而不是definition前面.
16. 长函数必须要写成很多子函数.

## Comments

1. At the top of each file, include a comment with your (and your partner’s) name, your (and your partner’s) uniqname, and a small description of the program or file. This is included in all the starter code.(**ok**)

```C++
/**
 * hello.cpp
 *
 * EECS 183: Project 0, Fall 2023
 *
 * Natalie Emcard
 * natalie@umich.edu
 *
 * Says hello to the world.
 */

```

2. Add a comment describing code that would not be clear to you if you were reading it for the first time.(**ok**)

```c++
// This comment is not necessary because the code is clear on its own:
// Print out number the user enters
int x;
cin >> x;
cout << "You entered: " << x << endl;

// This comment is necessary:
// Find the base 3 logarithm of x
int log3 = 0;
while (x > 1) {
    x /= 3;
    log3++;
}

```

3. Comments must be on their own lines.(**ok this is new**)

```C++
int y = 4; // this comment is bad style

// this comment is good style
int x = 3;

```

4. **It’s normal to comment out code you used for testing and isn’t needed anymore, but do not hand in code with commented-out regions.**

```C++
int y = 4; // this comment is bad style

// this comment is good style
int x = 3;

```

## Whitespace and Indentation

1. There must be single space between operators and their operands.(**ok**)

```C++
 // bad style
 count+=(a+b)*c/d+random();

 // good style
 count += (a + b) * c / d + random();
```

2. There must not be a space around parentheses.(**ok**)

```C++
 // bad style
 pluralize ( "person" ,"people" , numberOfPeople );

 // good style
 pluralize("person", "people", numberOfPeople);
```

3. There must be only one statement on each line.(**ok**)

```C++
 // bad style
 int x = 3; int y = 2;

 // good style
 int x = 3;
 int y = 2;
```

4. There must be a line break after every `{`. (**ok**)

```C++
 // bad style
 if (x > 3) { y = 2; }

 // good style
 if (x > 3) {
     y = 2;
 }
```

5. **Indent(缩进)** your code in a consistent way that shows which blocks of code are inside others. (**ok**)

```C++
 // bad style
 int main() {
 int x = 0;

 if (x > 0) {
     cout << "x is positive." << endl;
     } 
 else { for (int i = 0; i < 3; i++) {
         cout << "*";
     }}
 return 0;
 }

 // good style
 int main() {
     int x = 0;

     if (x > 0) {
         cout << "x is positive." << endl;
     } else { 
         for (int i = 0; i < 3; i++) {
             cout << "*";
         }
     }
     return 0;
 }

```

6. No lines may be longer than 80 characters. Visual Studio and XCode have ways to show you how long your lines are. You can break long statements into multiple lines like this: (**ok**)

```c++
 // bad style
 cout << "a = " << a << " b = " << b << " c = " << c << " d = " << d << " e = " << e << " f = " << f;
    
 // good style
 cout << "a = " << a << " b = " << b 
      << " c = " << c << " d = " << d 
      << " e = " << e << " f = " << f;
```

## Variables and Constants

1. Variables must have names that describe their purpose. `i` and `j` used as loop counters do describe their purpose! (**ok, my style**)

```C++
 // bad style
 int var1;
 int var2;
    
 // good style
 int num_students;
 int num_classes;
```

2. Whenever possible, initialize variables in their declaration. (**ok, my style**)

```C++
 // bad style
 int x;
 x = 2;
    
 // good style
 int x = 2;
```

3. Use captialization for identifiers that matches the type of thing that is being identified. 

- Variables must either be “snake-case” like `int course_credits = 4;` or “camel case” like `int courseCredits = 4;`. Choose the one you prefer and use it consistently. (**ok, my style, both used often**)
- **Constants must be in all capital letters** like `const int MAX_CREDITS = 18;`. (**ok, not used before, Ill do it**)
- **Class names must have their first letter capitalized**, like `class CityBus { };`. (**ok, never noticed before, Ill do it**)

4. **Do not use global variables. Global constants are acceptable.** **(ok and I do not even know how to use them so don't worry)**

5. **Magic numbers (numbers that do not have an immediately obvious meaning to another programmer) must be stored in constants. 0, 1, and 2 are never considered magic numbers.**(**kind of confusing but ok**)

```C++
 // bad style
 double area = 3.141592 * radius * radius;
    
 // good style
 const double PI = 3.141592;
 double area = PI * radius * radius;
```

## Conditionals

1. Test `bool` variables directly, not using expressions like `== true` or `== false`. (**kind of unnecessary but ok**)

```c++
 // bad style
 // isValid is a bool
 if (isValid == true) {}
 if (isValid == false) {}
    
 // good style
 if (isValid) {}
 if (!isValid) {}
```

2. In functions returning `bool`, simplify if/else expressions that compute the return value to expressions whenever possible. (**ok my bad**)

```C++
 // bad style
 if (score1 == score2) {
     return true;
 } else {
     return false;
 }
    
 // good style
 return score1 == score2;
```

## Loops

1. Whenever you need temporary variables for iteration, **use `i`, then `j`, then `k`**, unless more specific names would make your code more readable. (**ok I will pay attention**)

```c++
 // can be good style
 for (int column = 0; column < numberOfColumns; column++) {
     for (int row = 0; row < numberOfRows; row++) {
         // do something
     }
 }

```

If you find yourself in need of more than three variables inside a loop, you should reconsider your design!

## Functions

1. **Every function you create must have an RME comment above it**. The format of an RME comment will be described in lecture. If a function has a prototype (declaration), the RME must come before the prototype, not the definition. (**ok and that will be important**)

RME如下: 就是Requires, Modifies, Effects

```C++
/**
* Requires: errorNumber be either 1 or 2
* Modifies: cout
* Effects: If errorNumber is 1, prints an error message indicating
* an illegal name was entered.
* If errorNumber is 2, prints an error message indicating
* an illegal move was entered.
*/
void printErrorMessage(int errorNumber);
```



2. **Very long functions should be broken into smaller functions**. Try to limit your functions to 50 lines of code. This does not apply to `main()` in Project 1. (**ok kind of hard**)

## Other

1. **Do not use `ignore()` to get past characters in an input stream. `getline()` will cause far fewer problems.** **(ok both command idk)**
2. C++ contains an `exit()` function that immediately exits your entire program. Do not call this function in any 183 projects 1-4. **Your program must always exit naturally by reaching the end of your main function and returning.**
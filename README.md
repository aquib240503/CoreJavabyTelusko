#Core Java 
#Java Tutorial For beginners 2023 by Telusko
<br />
link : https://www.youtube.com/playlist?list=PLsyeobzWxl7pe_IiTfNyr55kwJPWbgxB5 <br />
Repo link : https://github.com/aquib240503/CoreJavabyTelusko.git

#Notes from https://www.youtube.com/watch?app=desktop&v=8cm1x4bC610 video
Operators in Java
1. Arithmetic + - * / % += ++ --
2. Bitwise << >>
3. Relational
4. Logical AND OR
5. Ternary condition ? expr1 : expr2

Array
1. 1D Array
   int num[] = new int[4];  //declare array <br />
   int num2 = {8,12,76,54}; //initialise array
2. 2D Array
   int d[][] = new int[3][4];
   int d[][] = {
   {1,2,3,4}, <br />
   {2,4,6,8}, <br />
   {1,3,5,7} <br />
   };
3. Jagged Array
   int d[][] = {
   {1,2,3,4}, <br />
   {2,4,6}, <br />
   {1,3,5,7,8} <br />
   }; <br />
   no. of rows = d.length <br />
   no. of columns(in ith column) =d[i].length

For each(or Enhanced For loop)

Varargs //Variable Length Arguments
int ... n (n will become an array) <br />
ex: public int sum(int ... n) { <br />
int sum = 0; <br />
for(int k : n) { <br />
sum += k; <br />
} <br />
return sum;
}

Inheritance

Inheritance is IS-A relationship <br />
Java doesn't support multiple inheritance
Single level <br />
Multi level

Sub class extends Super class

Super class(used in Java)/Parent/Base <br />
Sub class(used in Java)/Child/Derived

Super Method

super() // this super method presents in all type of constructors
to make a call to super class constructor.

Multiple Inheritance <br />
Java doesn't support multiple inheritance directly, check for indirect support.

Method Overriding | Super Keyword

subclass method overrides the superclass method <br />
@Override annotation to override a method <br />
super.override_method() <br />
super.<var/method> to access and call super class methods from sub class.

Dynamic Method Dispatch <br />

class A {
show(){};
} <br />
class B extends A {
show(){}; <br />
config(){};
} <br />

A obj = new B(); //here reference is of super class A and object(IMPLEMENTATION) is of sub class B
obj.show(); //show method of B will be executed
obj.config(); //error

in above obj we can call only those methods of class B which are in class A(override methods)

A obj = new B(); // runtime polymorphism

Encapsulation - binding data with methods

Use of getters and setters to access variables.
Make variables as private and write public methods(getters and setters) to access those variables.

Wrapper Class | AutoBoxing

int i=5; //Primitive datatype float double etc. <br />
Integer i1 = new Integer(i); //Boxing - Wrapping
int j = i1.intValue(); //Unboxing - Unwrapping
Integer ii = new Integer(5); //Integer wrapper class

int i=5;
Integer ii = i; //Auto Boxing
int j = ii; //Auto Unboxing

Abstract Keyword

We cannot create object of abstract class. <br />

abstract class Human { //Human class is called Abstract class <br />
public abstract void eat(); // To declare a method without defining it we need to make it as abstract method. <br />

    public void walk() { };        
}

class Man extends Human { //Man class is called Concrete class

    public void eat() {
    };

public class AbstractDemo {

    public static void main(String a[]) {
    
    Human a = new Man(); //reference of Human & object of Man
    
    }
}

Why do we need Abstract class?

1. If a class doesn't require any object of it to be created.
2. To use abstract class instead of concrete class to avoid method overloading of
   different concrete class. Ex below.

abstract class Number
class Integer extends Number
class Double extends Number
class Float extends Number

class Printer {
public void show(Number i)
{
sout(i);
}
} <br />
public class AbstractDemo {

    public static void main(String a[]) {
    
    Printer p = new Printer();
    p.show(5); //int
    p.show(1.2); //double
    p.show(4.5f);//float
    
    }
}

Final keyword

Final keyword can be used with variable, method, class.

final int DAY=0; //cannot change the value of DAY CONSTANT after assigning it once

final class A{ } // class A cannot be extended(inherit) by other class

final void show() { sout("in show") } // sub class cannot override the method show() of super
class if super class's method is final.

Interface

diff b/w Interface & Abstract class

Abstract class can have both abstract and non-abstract methods. <br />
Interface is like an abstract class but interface will only have abstract methods in it(only declared methods no definition). <br />
By default all the methods of an interface are public abstract so no need to write it. <br />
We can create reference of interface but NOT object of interface. <br />
We don't have constructor in interfaces.

interface Writer {
void write();
}

class Pen implements Writer {
void write(){
sout("I am a Pen");
}
}

class Pencil implements Writer {
void write(){
sout("I am a Pencil");
}
}

class Kit {
void doSomething(Writer wr){
wr.write();
}
}

public class InterfaceDemo {
Kit k = new Kit();
Writer pen_wr = new Pen(); // reference of Writer interface but object of Pen class
Writer pencil_wr = new Pencil(); // reference of Writer interface but object of Pencil class

    k.doSomething(pen_wr);
    k.doSomething(pencil_wr);

Anonymous Inner Class

class A {
public void show() {
sout("in class A");
}
}

class AnonymousDemo {

    public static void main(String[] a){
            A obj = new A(){
                            public void show(){
                                sout("I am the best");
                            }
                        };
            obj.show();
obj.show() calls show method of Anonymous Inner Class

Anonymous Class with Interface

We can create object of interface using anonymous class. Ex below

interface Abc{
void show();
}

public class InterfaceDemo{
public static void main(String[] a){
Abc obj = new Abc(){
public void show()
{sout("In show method of anonymous class with interface");}
};
obj.show();
}
}

Functional Interface | Lambda Expression

Types of Interfaces

1. Normal Interface - have more than 1 methods
2. Single abstract method(Sam) Interface - has 1 method
   Sam also called Functional Interface | Lambda Expression(adapted from Scala) in Java 1.8
3. Marker Interface - no method, ex. Serializable interface

Functional Interface has 1 abstract method(declare) & any number of default methods(define)

@FunctionalInterface
interface Abc{
void show();
}

public class FunctionalInterfaceDemo{

        public static void main(String[] a){
            Abc obj = () -> sout("in lambda exp");
                                    
            obj.show();
        }
}

Default method in Interface

From Java 1.8 we can define methods in interface using default keyword in method

@FunctionalInterface <br />
interface Demo{ <br />
void abc(); <br />
default void show(){ //defined method <br />
sout("in show"); <br />
}
}

class DemoImpl implements Demo <br />
{
public void abc(){
sout("In abc");
}
public void show(){
sout("In new show");
}
}

public class InterfaceDemo{

        public static void main(String[] a){
            Demo obj = new DemoImpl();
                                    
            obj.show(); //calls show of DemoImpl
            obj.abc();
        }
}

Multiple Inheritance issue with Interface

interface Demo{ <br />
default void show(){ //defined method <br />
sout("in Demo show"); <br />
}
}

interface MyDemo{ <br />
default void show(){ //defined method <br />
sout("in MyDemo show"); <br />
}
}

class DemoImpl implements Demo, MyDemo <br />
{
public void show(){// 1 way to remove ambiguity to call which show method
sout("In DemoImpl show");
}
@Override
public void show(){
Demo.super.show();// calls show method of Demo class
}
}

public class InterfaceDemo{

        public static void main(String[] a){
            Demo obj = new DemoImpl();
                                    
            obj.show(); //calls show of DemoImpl
        }
}


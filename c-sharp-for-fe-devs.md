# C# Programming for Javascript Developers 

## Topics

1. [C# Basics](#1-c-basics)
   - [Creating you first console application](#creating-your-first-console-applicaiton)
   - [Control structures (loops and conditional statements)](#control-structures-loops-and-conditional-statements)

2. [Object-Oriented Principles](#2-object-oriented-principles)
   - [Classes and objects](#classes-and-objects)
   - [Constructors](#constructors) TODO
   - [Methods](#methods)
   - [Properties](#properties) 
   - [Encapsulation with C#](#encapsulation-with-c)
   - [Inheritance with C#](#inheritance-with-c)
   - [Interfaces with C#](#interfaces-with-c)
   - [Polymorphism](#polymorphism)
   - [Records](#records) TODO

3. [Building Application with ASP.NET](#3-building-web-applications-with-aspnet)
   - [Overview of ASP.NET](#creating-your-first-web-project)
   - [Creating a simple web application using ASP.NET Core](#creating-your-first-web-project)
   - [Routing, controllers, and views](#controllers-and-routing)

4. [C# Equivalents of Common TypeScript Operations](#4-c-equivalents-of-typescript-operations)
   - [Array map](#array-map)
   - [Array reduce](#array-reduce)
   - [Destructuring](#destructuring)

5. [Project Structure](#5-project-structure) TODO
    - Anatomy of a c# project
        - Solutions
        - Projects
        - References
        - Nuget packages

6. [Tooling and Debugging](#6-ps-projects-tooling-and-debugging)
    - [VS code](#vs-code)
    - [Rider](#rider)

7. [Additional Resources](#6-additional-resources)
    - [.NET documentation](#net-documentation)
    - [Replit](#replit)

### Prerequisites      

For the purpose of this documentation it is necessary to first run through the developer machine setup up documented [here](https://dev.azure.com/principlestudios/FirstAmericanHomeWarranty/_wiki/wikis/First-American-Home-Warranty.wiki/131/Development-Environment-Setup).


### 1. C# Basics

C# is a powerful programming language that is used to build a wide variety of applications. To get started with C#, it's important to understand the basics of its syntax and data types. Here is the anatomy of a simple C# program:

```csharp
//definies the namespaces from which the code will be using classes. In our case we will be using the System namespace.
using System;

//defines the namespace for the class we are writing
namespace ConsoleTest
{
    //defines the class
    class Program
    {
        //defines the entry point for the application
        static void Main(string[] args)
        {
            //writes everybody's favorite greeting to the console, using System.Console
            Console.WriteLine("Hello, World!");
        }
    }
}
```



#### Syntax and Data Types
C# has a rich set of built-in data types, including integers, floating-point numbers, characters, strings, booleans, and more.

* `int` is a 32-bit signed integer. 
* `double` is a 64-bit floating-point number.
* `char` is a single 16-bit Unicode character.
* `string` is a sequence of Unicode characters.
* `bool` is a Boolean value that can be either `true` or `false`.


C# also has support for user-defined data types through the use of classes and structures. C# syntax is similar to other C-style languages, with semicolons used to terminate statements and curly braces used to group statements into blocks.


#### Control Structures (Loops and Conditional Statements)
C# provides a range of control structures for looping and making decisions in code. For loops and while loops are used for repetitive tasks, and conditional statements like if, switch, and ternary operators are used for making decisions based on conditions.


```csharp

//defining a variable using an explicit type
int count = 0;

//defining a variable using type inference
var otherCount = 0;

//defining a constant variable
const int max = 10;

// For loop
for (int i = 0; i < 10; i++)
{
    Console.WriteLine(i);
}
// While loop
while (count < max)
{
    Console.WriteLine(count);
    count++;
}

// If statement
int num = 10;
if (num > 5)
{
    Console.WriteLine("Number is greater than 5");
}
else
{
    Console.WriteLine("Number is less than or equal to 5");
}

```

#### Creating your first console applicaiton

 Let's create a simple console application and see how some of the core C# concepts are impelemented.


1. Open a command prompt or terminal window.

2. Navigate to the directory where you want to create your project.

3. Type ```dotnet new console -n ConsoleTest``` and hit enter

3. Type ```cd ConsoleTest```

4. Type ```dotnet run```

4. You should see the output of ```Hello, World!```



#### Console Application Initial State

The initial state of the generated application code should be as follows.

``` Console.WriteLine("Hello, World!"); ```

This line is executed with a Top Level Statment. A top-level statement is a new feature introduced in C# 9.0 that allows you to write code outside of a [method](#methods) or [class](#classes-and-objects).


#### Exercise 
Now that we have created our first simple .net console application we can alter the code in program.cs to demonstrate some core C# concepts. As an exerise, implement the code in the above [control structures](#control-structures) section in the program.cs file generated by the dotnet


---

### 2. Object Oriented Principles 

Object-Oriented Programming (OOP) is a programming paradigm that is used to organize code and data into reusable components.  


#### Classes and Objects
Classes and objects are the building blocks of C# programming. A class is a blueprint for creating objects that share common properties and methods. Objects are instances of a class that contain data and can perform actions. 

```csharp
class Person
{
    //property
    public string Name { get; set; }
    //property
    public int Age { get; set; }

    //method
    public void SayHello()
    {
        Console.WriteLine("Hello, my name is " + Name + " and I am " + Age + " years old.");
    }
}

Person john = new Person();
john.Name = "John";
john.Age = 30;
john.SayHello(); // Output: Hello, my name is John and I am 30 years old.

```


#### Methods
Methods are a fundamental part of C# programming. A function is a standalone piece of code that performs a specific task and returns a value. A method is similar to a function but is associated with an object or class. 

```csharp

class Calculator
{
    
    // Method with parameters and return value
    public int Add(int x, int y)
    {
        return x + y;
    }
}

Calculator calc = new Calculator();
int result = calc.Add(3, 5);
Console.WriteLine(result); // Output: 8
```

#### Encapsulation with C#

Encapsulation is a fundamental concept in object-oriented programming that allows the hiding of the internal details of an object and restricting direct access to its data and methods from outside the object. In C#, encapsulation is achieved through the use of access modifiers.

There are three main types of access modifiers in C#:

-   `public`: allows a member to be accessed from anywhere within the application, including outside the class.
-   `private`: limits the access of a member to only within the class it is defined.
-   `protected`: allows access to the member within the class and derived classes.

#### Inheritance with C#

Inheritance is a fundamental concept in object-oriented programming that allows a new class to be based on an existing class, inheriting its properties, methods, and other members. In C#, inheritance is achieved through the use of the `:` symbol followed by the name of the base class.

For example, consider a base class `Vehicle` with properties and methods common to all vehicles, such as `NumberOfWheels`, `MaxSpeed`, and `Drive()`. We can create a derived class `Car` that inherits from `Vehicle` and adds its own properties and methods, such as `Brand`, `Model`, and `Accelerate()`. 

Inheritance allows for code reuse and the ability to create specialized classes that inherit from a more general base class. Derived classes can also override or extend the behavior of the base class through [polymorphism](#polymorphism).


```csharp

// Base class
public class Vehicle
{
    protected int NumberOfWheels { get; set; }
    protected int MaxSpeed { get; set; }
    
    public virtual void Drive()
    {
        Console.WriteLine("The vehicle is driving.");
    }
}

// Derived class
public class Car : Vehicle
{
    public string Brand { get; set; }
    public string Model { get; set; }
    
    private int _currentSpeed = 0;
    
    public void Accelerate()
    {
        _currentSpeed += 10;
        Console.WriteLine($"The car is accelerating to {_currentSpeed} mph.");
    }
    
    public override void Drive()
    {
        Console.WriteLine($"The {Brand} {Model} is driving.");
    }
}

// Example usage
Car myCar = new Car();
myCar.NumberOfWheels = 4;
myCar.MaxSpeed = 200;
myCar.Brand = "Toyota";
myCar.Model = "Camry";
myCar.Accelerate();
myCar.Drive();

```

#### Interfaces with C#

In object oriented programming, an interface is a construct that is used to specify the methods and properties a class must contain. Think of this as a contract that specifies a minimum set of data and behavior a class must be able to satisfy. This is useful for writing reusable code leveraging [polymorphism](#polymorphism). 
#### Polymorphism

Polymorphism is the practice of writing a single piece of code that can be used by objects of different types, such that the types have a *polymorphic* relationship. A polymorphic relationship is a relationship between two classes that are related to each other through inheritance, or a relationship between a class and an interface that it implements.

Consider the above examples of `Vehicle` and `Car`. We could introduce a third object type called a `RepairShop` that has a method called `RepairVehicle()` that takes a `Vehicle` object as a parameter. The `RepairVehicle()` method could then be used to repair any type of vehicle, regardless of whether it is a `Car` or a `Truck`. This is an example of polymorphism, where the `RepairVehicle()` method can be used with objects of different types, but still have a polymorphic relationship with the `Vehicle` class.

```csharp
public class RepairShop
{
    public void RepairVehicle(Vehicle vehicle)
    {
        Console.WriteLine($"The {vehicle.Brand} {vehicle.Model} has been repaired.");
    }
}

// Example usage
RepairShop myShop = new RepairShop();
myShop.RepairVehicle(myCar);
```


---
### 3. Building web applications with ASP.Net 

ASP.NET is a popular framework for building web applications using C#. It provides a wide range of features and tools to help you create modern, high-performance, and secure web applications. 

#### Creating Your First Web Project
 Now that we've been through some of the core concepts with .net, let's create a fresh asp.net web api project and take a look at the generated code.

1.  Open a command prompt or terminal window.

2.  Navigate to the directory where you want to create your project.

3.  Run the following command to create a new .NET Core Web API project:

    `dotnet new webapi -n MyWebApi`

    This will create a new .NET Core Web API project named `MyWebApi` in the current directory.

4.  Navigate to the project directory by running the following command:

    `cd MyWebApi`

5.  Run the following command to build the project:

    `dotnet build`

6.  Run the following command to run the project:

    `dotnet run`

    This will start the web API on `http://localhost:5065`.

7.  Open your HTTP client, such as Postman or Thunder Client, and create a new request with the URL `http://localhost:5065/weatherforecast`. Since this is a GET request, you can actually hit the URL directly in your browser to test it out. For any POST or PUT requests, you will need to use an HTTP client.

8.  Send the request to the server by clicking the Send button.

9. The API should respond with a JSON object containing some example values. You can modify the example code in the `WeatherForecastController.cs` file to return different data.

That's it! You now have a running .NET Core Web API that you can test with an HTTP client.

#### Controllers and Routing

TODO: Blurb on controllers and routing with link to the appropriate ms documentation 


---
### 4. C# Equivalents of TypeScript Operations

C# provides a wide range of tools and libraries that are similar to those found in TypeScript. For example, C# has a built-in method for mapping arrays, which is similar to the `map` method in TypeScript. Similarly, C# provides a built-in method for reducing arrays, which is similar to the `reduce` method in TypeScript. Finally, C# also provides support for destructuring, which allows you to extract properties from objects and store them in variables. 

#### Array Filter
In TypeScript, the filter method is used to return a new array with all the elements that pass a certain condition:


```typescript
const numbers = [1, 2, 3, 4, 5];
const evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers); // Output: [2, 4]
```

In C#, you can achieve the same result using the Where method from LINQ:

```csharp
var numbers = new[] { 1, 2, 3, 4, 5 };
var evenNumbers = numbers.Where(num => num % 2 == 0);
Console.WriteLine(string.Join(", ", evenNumbers)); // Output: 2, 4

```

#### Array Map

In TypeScript, the `map` method is used to transform each element of an array into a new element:

```typescript
const numbers = [1, 2, 3, 4];
const doubledNumbers = numbers.map(num => num * 2);
console.log(doubledNumbers); // Output: [2, 4, 6, 8]
```
In C#, you can achieve the same result using the Select method from LINQ:



```csharp
var numbers = new int[] { 1, 2, 3, 4 };
var doubledNumbers = numbers.Select(num => num * 2);
Console.WriteLine(string.Join(", ", doubledNumbers)); // Output: 2, 4, 6, 8
```

#### Array Reduce

In TypeScript, the `reduce` method is used to reduce an array to a single value by applying a function to each element of the array:

```typescript
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((acc, num) => acc + num, 0);
console.log(sum); // Output: 10
```
In C#, you can achieve the same result using the Aggregate method from LINQ:

```csharp
var numbers = new int[] { 1, 2, 3, 4 };
var sum = numbers.Aggregate(0, (acc, num) => acc + num);
Console.WriteLine(sum); // Output: 10
```


### Destructuring
In TypeScript, you can use destructuring to extract properties from objects and store them in variables:
 
 ```typescript
 const person = { name: "John", age: 30 };
const { name, age } = person;
console.log(name, age); 
```
In C#, you can achieve the same result using the var keyword and the object initializer syntax:

```csharp
var person = new { Name = "John", Age = 30 };
var (name, age) = person;
Console.WriteLine($"{name} {age}"); // Output: John 30
```

---
### 5. Project Structure

#### Projects and Solutions
___
### 6. PS projects, Tooling and Debugging

#### VS Code

VS code is the most popular cross platform tool for writing and debugging .net projects.

#### Rider

Jetbrains Rider is another solid option for working on .net projects. While not a free tool, it provides a more traditional Integratred Development Environment (IDE) experience for .net application development. 
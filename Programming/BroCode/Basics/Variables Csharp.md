---
Created: 2025-07-28T19:50
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            int age = 0;
            int newAge = 4;
            int result = age + newAge;

            double height = 100.055;
            float weight = 50.53f;

            string name = "Acob";
            char symbol = '@';
            String newName = "Andy";
            string concatString = name + symbol;

            bool isStudent;
            isStudent = true;

            Console.WriteLine($"Normal age is: {age}");
            Console.WriteLine($"Age result is: {result}");
            Console.WriteLine($"Name is: {name}");
            Console.WriteLine($"Height is: {height}");
            Console.WriteLine($"Your Symbol is: {symbol}");
            Console.WriteLine($"Your weight is: ${weight}");
            Console.WriteLine($"isStudent: {isStudent}");
            Console.WriteLine($"New name is {newName}");
            Console.WriteLine($"Concat string is {concatString}");

            Console.ReadKey();
        }
    }
}
```
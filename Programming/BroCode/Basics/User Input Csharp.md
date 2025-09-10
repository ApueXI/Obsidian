---
Created: 2025-07-28T20:16
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Write("Enter your Name: ");
            string name = Console.ReadLine();

            Console.Write("Enter your Age: ");
            int age = Convert.ToInt32(Console.ReadLine());

            Console.WriteLine($"Your are: {name}");
            Console.WriteLine($"Your are: {age} years old");


            Console.WriteLine($"Your name is: {name}");

            Console.ReadKey();
        }
    }
}
```
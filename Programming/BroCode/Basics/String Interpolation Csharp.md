---
Created: 2025-07-30T12:00
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            string firstName = "Laren";
            string lastName = "Acob";
            int age = 16;

            Console.WriteLine($"I am {firstName} {lastName,-10} and i am {age,10} years old.");

            Console.ReadKey();

        }
    }
}
```
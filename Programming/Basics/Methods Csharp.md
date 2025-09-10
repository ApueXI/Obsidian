---
Created: 2025-07-29T19:55
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            string name = "Acob";
            int age = 21;

            happyBirthday(name, age);
            Console.WriteLine();
            happyBirthday(name, age);
            Console.WriteLine();
            happyBirthday(name, age);
            Console.WriteLine();

            Console.ReadKey();
        }

        static void happyBirthday(string name, int age)
        {
            Console.WriteLine($"Happy Birthday to you {name}");
            Console.WriteLine($"Happy Birthday to you {name}");
            Console.WriteLine($"Your are {age} years old");
            Console.WriteLine($"Thank me {name}");
        }
    }
} 
```
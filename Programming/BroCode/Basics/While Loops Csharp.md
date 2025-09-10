---
Created: 2025-07-29T09:54
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            string name = "";

            while (name == "")
            {
                Console.Write("Enter your name: ");
                name = Console.ReadLine();
            }

            Console.WriteLine($"Hello {name}");

            Console.ReadKey();
        }
    }
}
```
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
            string[] cars = { "BMW", "Mustang", "Corvette" };

            string[] names = new string[3];
            names[0] = "Acob";
            names[1] = "Andy";
            names[2] = "Goco";

            foreach (var car in cars)
            {
                Console.WriteLine(car);
            }
            Console.WriteLine();
            foreach (var name in names)
            {
                Console.WriteLine(name);
            }

            Console.ReadKey();
        }
    }
}
```
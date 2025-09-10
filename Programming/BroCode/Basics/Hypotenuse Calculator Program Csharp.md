---
Created: 2025-07-29T08:36
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Write("Enter Side A: ");
            double a = Convert.ToDouble(Console.ReadLine());

            Console.Write("Enter Side B: ");
            double b = Convert.ToDouble(Console.ReadLine());

            double c = Math.Sqrt((a * a) + (b * b));

            Console.WriteLine($"The hypotenuse is: {c}");

            Console.ReadKey();
        }
    }
}
```
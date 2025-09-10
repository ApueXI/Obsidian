---
Created: 2025-07-30T09:23
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            double total;
            double total2;

            total = Multiply(2, 3, 4);
            total2 = Multiply(2, 3);

            Console.WriteLine(total);
            Console.WriteLine(total2);

            Console.ReadKey();
        }

        static double Multiply(double x, double y)
        {
            return x * y;
        }
        static double Multiply(double a, double b, double c)
        {
            return a * b * c;
        }
    }
}
```
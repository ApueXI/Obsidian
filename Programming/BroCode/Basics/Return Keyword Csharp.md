---
Created: 2025-07-29T20:06
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            double x;
            double y;
            double result;

            Console.Write("Enter number 1: ");
            x = Convert.ToDouble(Console.ReadLine());

            Console.Write("Enter number 2: ");
            y = Convert.ToDouble(Console.ReadLine());

            result = Multiply(x, y);

            Console.WriteLine($"The result is: {result}");

            Console.ReadKey();
        }

        static double Multiply(double x, double y)
        {
            double z = x * y;
            return z;
        }
    }
}
```
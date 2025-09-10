---
Created: 2025-07-29T07:53
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            double x = 9.152;
            int y = 2;
            int z = -10;

            // x to the power of y
            double a = Math.Pow(x, y);

            double b = Math.Sqrt(x);

            double c = Math.Abs(z);

            double d = Math.Round(x);

            double e = Math.Ceiling(x);

            double f = Math.Floor(x);

            double g = Math.Max(x, y);

            double h = Math.Min(x, y);

            Console.WriteLine(a);

            Console.WriteLine(b);

            Console.WriteLine(c);

            Console.WriteLine(d);

            Console.WriteLine(e);

            Console.WriteLine(f);

            Console.WriteLine(g);

            Console.WriteLine(h);

            Console.ReadKey();
        }
    }
}
```
---
Created: 2025-07-30T09:29
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            double total = CheckOut(3.99, 5.75, 15);

            Console.WriteLine(total);

            Console.ReadKey();
        }

        static double CheckOut(params double[] prices)
        {
            double total = 0;
            foreach (var price in prices)
            {
                total += price;
            }

            return total;
        }
    }
}
```
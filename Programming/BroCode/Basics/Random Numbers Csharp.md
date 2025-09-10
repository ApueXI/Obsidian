---
Created: 2025-07-29T08:28
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            Random random = new Random();

            int num = random.Next(1, 7);
            Console.WriteLine(num);

            double numD = random.NextDouble();
            Console.WriteLine(numD);

            Console.ReadKey();
        }
    }
}
```
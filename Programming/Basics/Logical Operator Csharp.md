---
Created: 2025-07-29T09:40
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("What is the temperature outside(C):");
            double temp = Convert.ToDouble(Console.ReadLine());

            if (temp >= 10 && temp <= 25)
            {
                Console.WriteLine("Today is warm");
            }
            else if (temp <= -50 || temp >= 50)
            {
                Console.WriteLine("Do not go outside");
            }
            else
            {
                Console.WriteLine("Please enter a temperature");
            }

            Console.ReadKey();
        }
    }
}
```
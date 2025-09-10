---
Created: 2025-07-30T11:54
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            double temperature = 20;
            string message;

            message = (temperature >= 15) ? "It is warm outside" : "It is cold outside";

            Console.WriteLine(message);
            
            Console.ReadKey();

        }
    }
}
```
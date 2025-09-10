---
Created: 2025-07-29T10:14
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Write("How mant rwos?: ");
            int rows = Convert.ToInt32(Console.ReadLine());

            Console.Write("How mant columns?: ");
            int columns = Convert.ToInt32(Console.ReadLine());

            Console.Write("What sumbol?: ");
            string symbol = Console.ReadLine();

            for (int i = 0; i < rows; i++)
            {
                for (int j = 0; j < columns; j++)
                {
                    Console.Write(symbol);
                }
                Console.WriteLine();
            }

            Console.ReadKey();
        }
    }
}
```
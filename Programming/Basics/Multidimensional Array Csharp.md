---
Created: 2025-07-30T12:05
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            string[,] parkingLot = {
            { "Toyota", "Honda" },
            { "Ford", "Chevrolet" },
            { "BMW", "Mercedes" }
            };

            parkingLot[0, 1] = "Something";

            for (int i = 0; i < parkingLot.GetLength(0); i++)
            {
                for (int j = 0; j < parkingLot.GetLength(1); j++)
                {
                    Console.Write(parkingLot[i,j] + " ");
                }
                Console.WriteLine();
            }

            Console.ReadKey();

        }
    }
}
```
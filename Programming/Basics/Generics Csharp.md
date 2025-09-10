---
Created: 2025-08-01T07:22
tags:
  - OOP
---
```C#
using System;
using System.Collections.Generic;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            int[] intArray = { 1, 2, 3 };
            double[] doubles = { 1.0, 2.0, 3.0 };
            string[] strings = { "1", "2", "3" };

            DisplayElements(intArray);
            DisplayElements(doubles);
            DisplayElements(strings);

            Console.ReadKey();
        }
        public static void DisplayElements<Thing>(Thing[] array)
        {
            foreach (Thing item in array)
            {
                Console.Write(item + " ");
            }
            Console.WriteLine();
        }
    }
}
```
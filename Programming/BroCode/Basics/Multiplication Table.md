---
Created: 2025-08-01T16:31
tags:
  - Simple-Challenge
---
```C#
using System;

namespace MyProgram
{
    class Program
    {
        static void Main(string[] args)
        {
            int number;
            int gap;

            while (true)
            {
                Console.Write("Enter a number: ");
                if (int.TryParse(Console.ReadLine(), out number)) break;

                Console.WriteLine($"Invalid Input please try again");
            }

            gap = (number * 10).ToString().Length;

            MultiplicationTable(number, gap);
        }
        static void MultiplicationTable(int number, int gap)
        {
            Console.WriteLine("Multiplication Table \n");
            for (int i = 1; i <= 10; i++)
            {
                Console.WriteLine($"{i,-2} : {(number * i).ToString().PadLeft(gap)}");
            }
        }
    }
}
```
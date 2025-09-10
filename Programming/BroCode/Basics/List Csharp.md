---
Created: 2025-07-31T20:16
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
            List<string> foods = new List<string>();

            foods.Add("hotdog");
            foods.Add("pizza");
            foods.Add("hamburger");
            foods.Add("hotdog");
            foods.Add("fries");

            foods.Remove("fries");
            foods.Insert(0, "sushi");

            Console.WriteLine(foods[0]);
            Console.WriteLine(foods.Count);
            Console.WriteLine(foods.IndexOf("pizza"));
            Console.WriteLine(foods.LastIndexOf("hotdog"));
            Console.WriteLine(foods.Contains("pizza"));

            foods.Sort();
            foods.Reverse();
            //foods.Clear();

            string[] foodArray = foods.ToArray();

            foreach (string food in foods)
            {
                Console.WriteLine(food);
            }

            Console.ReadKey();
        }
    }
}
```
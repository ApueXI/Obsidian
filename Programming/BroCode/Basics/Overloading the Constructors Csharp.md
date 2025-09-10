---
Created: 2025-07-31T08:37
tags:
  - OOP
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            Pizza pizza1 = new Pizza("Stuffed Crust", "Red sauce", "Mozorella", "Pepperoni");
            Pizza pizza2 = new Pizza("Stuffed Crust", "Red sauce", "Mozorella");

            Console.ReadKey();
        }
    }
    class Pizza
    {
        string bread;
        string sauce;
        string cheese;
        string topping;

        public Pizza(string bread, string sauce, string cheese, string topping)
        {
            this.bread = bread;
            this.sauce = sauce;
            this.cheese = cheese;
            this.topping = topping;
        }
        public Pizza(string bread, string sauce, string cheese)
        {
            this.bread = bread;
            this.sauce = sauce;
            this.cheese = cheese;
        }
    }
}
```
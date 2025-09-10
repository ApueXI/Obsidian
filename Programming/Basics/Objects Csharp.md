---
Created: 2025-07-30T15:35
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
            Human human1 = new Human();
            Human human2 = new Human();

            human1.name = "Acob";
            human1.age = 17;

            human2.name = "Andy";
            human2.age = 21;

            human1.Eat();
            human1.Sleep();

            human2.Eat();
            human2.Sleep();

            Console.ReadKey();
        }
    }
    class Human
    {
        public string name;
        public int age;

        public void Eat()
        {
            Console.WriteLine($"{name} is eating");
        }
        public void Sleep()
        {
            Console.WriteLine($"{name} is sleeping");
        }
    }
}
```
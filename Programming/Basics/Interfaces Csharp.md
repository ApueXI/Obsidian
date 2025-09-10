---
Created: 2025-07-31T20:00
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
            Rabbit rabbit = new Rabbit();
            Hawk hawk = new Hawk();
            Fish fish = new Fish();

            rabbit.Flee();
            hawk.Hunt();
            fish.Hunt();
            fish.Flee();

            Console.ReadKey();
        }
    }
    interface IPrey
    {
        void Flee();
    }
    interface IPredator
    {
        void Hunt();
    }
    class Rabbit : IPrey
    {
        public void Flee()
        {
            Console.WriteLine("The rabbit runs away");
        }
    }
    class Hawk : IPredator
    {
        public void Hunt()
        {
            Console.WriteLine("The hawk is seaching for food");
        }
    }
    class Fish : IPrey, IPredator
    {
        public void Flee()
        {
            Console.WriteLine("The fist is swimming away");
        }
        public void Hunt()
        {
            Console.WriteLine("The fish hunting for smalls");
        }
    }
}
```
---
Created: 2025-07-31T09:56
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
            Dog dog = new Dog();
            Cat cat = new Cat();

            dog.Speak();
            cat.Speak();

            Console.ReadKey();
        }


    }

    class Animal
    {
        public virtual void Speak()
        {
            Console.WriteLine("The aniumal goes brrr");
        }
    }
    class Dog : Animal
    {
        public override void Speak()
        {
            Console.WriteLine("The dog goes woof");
        }
    }
    class Cat : Animal
    {
        public override void Speak()
        {
            Console.WriteLine("The cat goes meow");
        }
    }
}
```
---
Created: 2025-07-31T08:15
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
            Human human1 = new Human("Acob", 17);
            Human human2 = new Human("Andy", 20);

            human1.Eat();
            human1.Sleep();
            human1.Intro();

            human2.Eat();
            human2.Sleep();
            human2.Intro();


            Console.ReadKey();
        }
    }
    class Human
    {
        string name;
        int age;

        public Human(string name, int age)
        {
            this.name = name;
            this.age = age;
        }

        public void Eat()
        {
            Console.WriteLine($"{name} is eating");
        }
        public void Sleep()
        {
            Console.WriteLine($"{name} is sleeping");
        }
        public void Intro()
        {
            Console.WriteLine($"I am {name} and i am {age} years old");
        }
    }
}
```

```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            Car car1 = new Car("Ford","Mustang", 2022,"Red");
            Car car2 = new Car("Chevy", "Corvette", 2021, "Blue");

            car1.drive();
            car2.drive();

            Console.ReadKey();
        }
    }
    class Car
    {
        string make;
        string model;
        int year;
        string color;

        public Car(string make, string model, int year, string color)
        {
            this.make = make;
            this.model = model;
            this.year = year;
            this.color = color;
        }

        public void drive()
        {
            Console.WriteLine($"You drive the {make} {model}");
        }
    }
}
```
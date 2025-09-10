---
Created: 2025-07-31T08:30
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
            Car car1 = new Car("Ford");
            Car car2 = new Car("Chevy");
            Car car3 = new Car("Chevy");

            Console.WriteLine(Car.numberCars);

            Car.StartRace();

            Console.ReadKey();
        }
    }
    class Car
    {
        string make;

        public static int numberCars;

        public Car(string make)
        {
            this.make = make;
            numberCars++;
        }

        public void drive()
        {
            Console.WriteLine($"You drive the {make}");
        }

        public static void StartRace()
        {
            Console.WriteLine($"The race has begun");
        }

    }
}
```
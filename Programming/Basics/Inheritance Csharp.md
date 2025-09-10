---
Created: 2025-07-31T08:54
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
            Car car = new Car();
            Bycicle bycicle = new Bycicle();
            Boat boat = new Boat();

            Console.WriteLine(car.speed);
            Console.WriteLine(car.wheels);
            car.Go();
            Console.WriteLine();

            Console.WriteLine(bycicle.speed);
            Console.WriteLine(bycicle.wheels);
            bycicle.Go();
            Console.WriteLine();

            Console.WriteLine(boat.speed);
            Console.WriteLine(boat.wheels);
            boat.Go();
            Console.WriteLine();

            Console.ReadKey();
        }
    }
    class Vehicle
    {
        public int speed = 0;
        public void Go()
        {
            Console.WriteLine("This vehicle is moving");
        }
    }
    class Car : Vehicle
    {
        public int wheels = 4;

    }
    class Bycicle: Vehicle
    {
        public int wheels = 2;

    }
    class Boat: Vehicle
    {
        public int wheels = 0;

    }
}
```
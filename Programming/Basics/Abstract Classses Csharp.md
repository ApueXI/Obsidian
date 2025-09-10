---
Created: 2025-07-31T09:16
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

            //cannot work
            Vehicle vehicle = new Vehicle();

            Console.ReadKey();
        }
    }
    abstract class Vehicle
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
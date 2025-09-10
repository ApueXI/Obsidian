---
Created: 2025-08-01T06:59
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
            Car car = new Car("Prsche");

            Console.WriteLine(car.Model);

            Console.ReadKey();
        }
    }
    class Car
    {
        public string Model { get; set; }

        public Car(string model)
        {
            Model = model;
        }

    }
}
```
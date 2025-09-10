---
Created: 2025-07-31T09:43
tags:
  - OOP
---
```C#
using System;
using System.Security.Cryptography;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            Car car1 = new Car("Mustang", "Ford");

            Car car2 = Copy(car1);

            Console.WriteLine(car2.make + " " + car2.model);

            Console.ReadKey();
        }

        public static Car Copy(Car car) {
            return new Car(car.model, car.make);
        }
    }
    class Car
    {
        public string model;
        public string make;
        public Car(string model, string make)
        {
            this.model = model;
            this.make = make;
        }
    }

}
```
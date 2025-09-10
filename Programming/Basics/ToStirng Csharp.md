---
Created: 2025-07-31T19:38
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
            Car car = new Car("Chevy", "Corvette", 2022, "Blue");

            Console.WriteLine(car);
            Console.WriteLine(car.ToString());

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
        public override string ToString()
        {
            string message = $"This is a  {make} {model}";

            return message;
        }
    }
}
```
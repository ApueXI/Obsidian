---
Created: 2025-07-31T09:23
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
            Car[] garage = new Car[3];

            Car car1 = new Car("Mustang");
            Car car2 = new Car("Corvette");
            Car car3 = new Car("Lambo");

            garage[0] = car1;
            garage[0] = car2;
            garage[0] = car3;

            foreach (Car car in garage)
            {
                Console.WriteLine(car.model);
            }

            Console.ReadKey();
        }
    }
    class Car
    {
        public string model;
        public Car(string model)
        {
            this.model = model;
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
            Car[] garage = { new Car("Mustang"), new Car("Corvette"), new Car("Lambo") };

            foreach (Car car in garage)
            {
                Console.WriteLine(car.model);
            }

            Console.ReadKey();
        }
    }
    class Car
    {
        public string model;
        public Car(string model)
        {
            this.model = model;
        }
    }

}
```
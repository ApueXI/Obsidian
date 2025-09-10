---
Created: 2025-08-01T07:10
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
            Console.WriteLine($"{Planets.Pluto} is a planet number {(int)Planets.Pluto}");
            Console.WriteLine($"{Planets.Mercury} is a planet Number {(int)Planets.Mercury}");



            Console.ReadKey();
        }
    }
    enum Planets
    {
        Mercury = 1,
        Venus = 2,
        Earth = 3,
        Mars = 4,
        Jupiter = 5,
        Saturn = 6,
        Uranus = 7,
        Neptune = 8,
        Pluto = 9
    }
    enum PlanetRadius
    {
        Mercury = 2439,
        Venus = 6051,
        Earth = 6371,
        Mars = 3389,
        Jupiter = 69911,
        Saturn = 58232,
        Uranus = 25362,
        Neptune = 24622,
        Pluto = 1188
    }
}
```

```C#
using System;
using System.Collections.Generic;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            string name = PlanetRadius.Earth.ToString();
            int radius = (int)PlanetRadius.Earth;

            Console.WriteLine(name);
            Console.WriteLine(radius);

            Console.ReadKey();
        }
    }
    enum Planets
    {
        Mercury = 1,
        Venus = 2,
        Earth = 3,
        Mars = 4,
        Jupiter = 5,
        Saturn = 6,
        Uranus = 7,
        Neptune = 8,
        Pluto = 9
    }
    enum PlanetRadius
    {
        Mercury = 2439,
        Venus = 6051,
        Earth = 6371,
        Mars = 3389,
        Jupiter = 69911,
        Saturn = 58232,
        Uranus = 25362,
        Neptune = 24622,
        Pluto = 1188
    }
}
```

```C#
using System;
using System.Collections.Generic;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            string name = PlanetRadius.Earth.ToString();
            int radius = (int)PlanetRadius.Earth;

            double volume = Volume(PlanetRadius.Earth);

            Console.WriteLine(name);
            Console.WriteLine(radius);
            Console.WriteLine($"Volume is {volume}");

            Console.ReadKey();
        }
        public static double Volume(PlanetRadius radius)
        {
            double volume = (4.0 / 3.0) * Math.PI * Math.Pow((int)radius, 3);
            return volume;
        }
    }
    enum Planets
    {
        Mercury = 1,
        Venus = 2,
        Earth = 3,
        Mars = 4,
        Jupiter = 5,
        Saturn = 6,
        Uranus = 7,
        Neptune = 8,
        Pluto = 9
    }
    enum PlanetRadius
    {
        Mercury = 2439,
        Venus = 6051,
        Earth = 6371,
        Mars = 3389,
        Jupiter = 69911,
        Saturn = 58232,
        Uranus = 25362,
        Neptune = 24622,
        Pluto = 1188
    }
}
```
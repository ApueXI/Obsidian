---
Created: 2025-07-29T09:33
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Write("What is the day Today? ");
            string day = Console.ReadLine();

            switch (day)
            {
                case "Monday":
                    Console.WriteLine("Today is Monday");
                    break;
                case "Tueday":
                    Console.WriteLine("Today is Monday");
                    break;
                case "Wednesday":
                    Console.WriteLine("Today is Monday");
                    break;
                case "Thursday":
                    Console.WriteLine("Today is Monday");
                    break;
                case "Friday":
                    Console.WriteLine("Today is Monday");
                    break;
                case "Saturday":
                    Console.WriteLine("Today is Monday");
                    break;
                case "Sunday":
                    Console.WriteLine("Today is Monday");
                    break;
                default:
                    Console.WriteLine("You did not write a day");
                    break;
            }

            Console.ReadKey();
        }
    }
}
```
---
Created: 2025-07-30T11:45
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {

            double x;
            double y;
            double result;

            try
            {
                Console.Write("Enter a number: ");
                x = Convert.ToDouble(Console.ReadLine());

                Console.Write("Enter a number: ");
                y = Convert.ToDouble(Console.ReadLine());

                result = x / y;

                Console.WriteLine($"Results: {result}");
            }
            catch (DivideByZeroException e)
            {
                Console.WriteLine($"You cant divide by zerp");
            }
            catch (Exception ex) {
                Console.WriteLine($"Error: {ex}");
            }
            Console.ReadKey();
        }
    }
}
```
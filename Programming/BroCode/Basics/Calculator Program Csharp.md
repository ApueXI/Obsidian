---
Created: 2025-07-29T19:26
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            do
            {
                double num1 = 9;
                double num2 = 0;
                double result = 0;

                Console.WriteLine("---------------------");
                Console.WriteLine("Calculator Program");
                Console.WriteLine("---------------------");

                Console.Write("Enter number 1: ");
                num1 = Convert.ToDouble(Console.ReadLine());

                Console.Write("Enter number 2: ");
                num2 = Convert.ToDouble(Console.ReadLine());

                Console.Write("Enter an option( + - * / ): ");


                switch (Console.ReadLine())
                {
                    case "+":
                        result = num1 + num2;
                        Console.WriteLine($"Resilt: {result}");
                        break;
                    case "-":
                        result = num1 - num2;
                        Console.WriteLine($"Reslt: {result}");
                        break;
                    case "*":
                        result = num1 * num2;
                        Console.WriteLine($"Reslt: {result}");
                        break;
                    case "/":
                        result = num1 / num2;
                        Console.WriteLine($"Reslt: {result}");
                        break;
                    default:
                        Console.WriteLine("That was not a valid option");
                        break;
                }
                Console.Write("Would you like to contninue? (Y/N): ");
            } while (Console.ReadLine().ToUpper() == "Y");

            Console.ReadKey();
        }
    }
}
```
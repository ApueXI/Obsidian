---
Created: 2025-07-29T12:41
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            Random random = new Random();

            bool isPlayAgain = true;
            string response;
            int min = 1;
            int max = 101;
            int guess;
            int number;
            int guesses;


            while (isPlayAgain)
            {
                response = "";
                guess = 0;
                guesses = 0;
                number = random.Next(min, max);

                while (guess != number)
                {
                    Console.Write($"Guess a number between {min} - {max -1}: ");
                    guess = Convert.ToInt32(Console.ReadLine());
                    Console.WriteLine($"Guess: {guess}");

                    if (guess > number)
                    {
                        Console.WriteLine("Too high");
                    }
                    else if (guess < number)
                    {
                        Console.WriteLine("Too low");
                    }
                    guesses++;
                }
                Console.WriteLine($"Number: {number}");
                Console.WriteLine("You win");
                Console.WriteLine($"Guesses: {guesses}");

                Console.Write("Would you like to play again? (y/n): ");
                response = Console.ReadLine().ToUpper();
                if (response != "Y") isPlayAgain = false;

            }
            Console.WriteLine("-------------------");
            Console.WriteLine("Thanks for playing");
            Console.WriteLine("-------------------");


            Console.ReadKey();
        }
    }
}
```
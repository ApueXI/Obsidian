---
Created: 2025-07-29T13:04
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
            string player;
            string computer;

            while (isPlayAgain)
            {
                player = "";
                computer = "";
                while (player != "ROCK" && player != "PAPER" && player != "SCISSORS")
                {
                    Console.Write("Enter ROCK, PAPER, SCISSORS: ");
                    player = Console.ReadLine().ToUpper();
                }

                switch (random.Next(1, 4))
                {
                    case 1:
                        computer = "ROCK";
                        break;
                    case 2:
                        computer = "PAPER";
                        break;
                    case 3:
                        computer = "SCISSORS";
                        break;
                }

                Console.WriteLine($"Player {player}");
                Console.WriteLine($"Computer: {computer}");

                switch (player)
                {
                    case "ROCK":
                        if (computer == "ROCK")
                        {
                            Console.WriteLine("Its a draw");
                        }
                        else if (computer == "PAPER")
                        {
                            Console.WriteLine("You lost");
                        }
                        else
                        {
                            Console.WriteLine("You won");
                        }
                        break;
                    case "PAPER":
                        if (computer == "ROCK")
                        {
                            Console.WriteLine("You won");
                        }
                        else if (computer == "PAPER")
                        {
                            Console.WriteLine("its a Draw");
                        }
                        else
                        {
                            Console.WriteLine("You lost");
                        }
                        break;
                    case "SCISSORS":
                        if (computer == "ROCK")
                        {
                            Console.WriteLine("Its a lost");
                        }
                        else if (computer == "PAPER")
                        {
                            Console.WriteLine("you won");
                        }
                        else
                        {
                            Console.WriteLine("its a draw");
                        }
                        break;
                }

            }

            Console.ReadKey();
        }
    }
}
```
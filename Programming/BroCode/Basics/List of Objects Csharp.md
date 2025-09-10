---
Created: 2025-07-31T20:27
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
            List<Player> players = new List<Player>();

            players.Add(new Player("Chad"));
            players.Add(new Player("Steve"));
            players.Add(new Player("Karen"));

            foreach (Player player in players)
            {
                Console.WriteLine(player);
            }

            Console.ReadKey();
        }
    }
    class Player
    {
        public string username;

        public Player(string username)
        {
            this.username = username;
        }
        public override string ToString()
        {
            return username;
        }

    }
}
```
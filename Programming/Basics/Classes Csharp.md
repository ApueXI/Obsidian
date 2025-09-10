---
Created: 2025-07-30T12:21
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
            Messages.Hello();
            Messages.Waiting();
            Messages.Bye();

            Console.ReadKey();
        }
    }
}
```

```C#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace BroCode
{
    static class Messages
    {
        public static void Hello()
        {
            Console.WriteLine("Welcome to the program");
        }
        public static void Waiting()
        {
            Console.WriteLine("Thanks for Waiting");
        }
        public static void Bye()
        {
            Console.WriteLine("Goodbye");
        }
    }
}
```
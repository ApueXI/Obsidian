---
Created: 2025-07-29T08:58
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Write("Please enter your age: ");
            int age = Convert.ToInt32(Console.ReadLine());

            if (age > 100)
            {
                Console.WriteLine("You are too old to sign up");
            }
            else if (age >= 18)
            {
                Console.WriteLine("You are eligible to vote");
            }
            else if (age < 0)
            {
                Console.WriteLine("You havent been born yet");
            }
            else
            {
                Console.WriteLine("You are not eigible to vote");
            }

            Console.ReadKey();
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
            Console.Write("Please enter your name: ");
            string name = Console.ReadLine();

            if (name != "")
            {
                Console.WriteLine($"Hello {name}");
            }
            else
            {
                Console.WriteLine("You did not enter your name");
            }

            Console.ReadKey();
        }
    }
}
```
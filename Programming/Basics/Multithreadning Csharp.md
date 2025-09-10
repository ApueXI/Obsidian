---
Created: 2025-08-01T07:34
tags:
  - OOP
---
```C#
using System;
using System.Collections.Generic;
using System.Threading;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            Thread mainThread = Thread.CurrentThread;
            mainThread.Name = "Main Thread";
            Console.WriteLine(mainThread.Name);

            Thread thread1 = new Thread(() => CountDown("acob"));
            Thread thread2 = new Thread(CountUp);
                
            thread1.Start();
            thread2.Start();

            Console.WriteLine($"{mainThread.Name} is Complete");

            Console.ReadKey();
        }
        public static void CountDown(string name)
        {
            for (int i = 10; i >= 0; i--)
            {
                Console.WriteLine($"Timer #1: {i} seconds");
                Thread.Sleep(1000);
            }
            Console.WriteLine("Timer #1 is sleep");
        }
        public static void CountUp()
        {
            for (int i = 0; i <= 10; i++)
            {
                Console.WriteLine($"Timer #2: {i} seconds");
                Thread.Sleep(1000);
            }
            Console.WriteLine("Timer #2 is sleep");
        }
    }
}
```
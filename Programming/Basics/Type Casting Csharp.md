---
Created: 2025-07-28T20:06
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            double a = 3.14;
            int b = Convert.ToInt32(a);

            string name = "Acob";

            int e = 321;
            string f = Convert.ToString(e);

            string z = "$";
            char x = Convert.ToChar(z);

            string y = "true";
            bool isTrue = Convert.ToBoolean(y);


            Console.WriteLine(b);
            Console.WriteLine(a.GetType());
            Console.WriteLine(b.GetType());
            Console.WriteLine(name.GetType());
            Console.WriteLine(f);
            Console.WriteLine(f.GetType());
            Console.WriteLine(x.GetType());
            Console.WriteLine(isTrue);
            Console.WriteLine(isTrue.GetType());

            Console.ReadKey();
        }
    }
}
```
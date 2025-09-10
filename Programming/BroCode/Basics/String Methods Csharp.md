---
Created: 2025-07-29T08:42
---
```C#
using System;

namespace BroCode
{
    class Program
    {
        static void Main(string[] args)
        {
            string fullName = "Bro Code";
            string phoneNumber = "123-456-7890";

            string toUpper = fullName.ToUpper();
            string toLower = fullName.ToLower();

            string replaced = phoneNumber.Replace("-", "/");

            string insert = fullName.Insert(0, "@");
            string insertMore = fullName.Insert(0, "Mr. ");

            int length = fullName.Length;

            string firstName = fullName.Substring(0, 3);
            string lastName = fullName.Substring(4, 4);

            Console.WriteLine(toUpper);
            Console.WriteLine(toLower);
            Console.WriteLine(replaced);
            Console.WriteLine(insert);
            Console.WriteLine(insertMore);
            Console.WriteLine(fullName.Length);
            Console.WriteLine(firstName);
            Console.WriteLine(lastName);

            Console.ReadKey();
        }
    }
}
```
---
Created: 2025-08-01T20:24
tags:
  - Simple-Challenge
---
```C#
using System;

namespace MyProgram
{
    class Program
    {
        static void Main(string[] args)
        {
            string password;
            bool isPasswordCorrect = false;

            while (!isPasswordCorrect)
            {
                Console.Write("Enter your secure password: ");
                password = Console.ReadLine();

                if (!lengthChecker(password)) continue;
                if (!CaseChecker(password)) continue;
                if (!SymbolChecker(password)) continue;

                Console.WriteLine("correct");
                isPasswordCorrect = true;
            }
        }

        static bool lengthChecker(string passowrd)
        {
            if (passowrd.Length < 8)
            {
                Console.WriteLine("\tPassword's length must be 8+");
                return false;
            }
            return true;
        }

        static bool CaseChecker(string password)
        {
            bool isContainsUpper = false;
            bool isContainsLower = false;
            foreach (char c in password)
            {
                if (char.IsUpper(c)) isContainsUpper = true;
                if (char.IsLower(c)) isContainsLower = true;
                if (isContainsUpper && isContainsLower) break;
            }

            if (!isContainsUpper || !isContainsLower)
            {
                Console.WriteLine("Code must contain uppercase and lowercase");
                return false;
            }
            return true;
        }

        static bool SymbolChecker(string password)
        {
            bool isContainsSymbol = false;
            foreach (char c in password)
            {
                if (char.IsSymbol(c) || char.IsPunctuation(c))
                {
                    isContainsSymbol = true;
                    break;
                }
            }

            if (!isContainsSymbol)
            {
                Console.WriteLine("Code must contain symbols");
                return false;
            }

            return true;
        }
    }
}
```
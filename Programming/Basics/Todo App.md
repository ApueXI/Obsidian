---
Created: 2025-08-02T15:25
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
            List<Task> tasks = new List<Task>();
            int choices = 0;
            bool isChoiceSuccess = false;
            bool isNavigate = true;

            while (isNavigate)
            {
                Console.WriteLine("\nOptions (1, 2, 3, 4)");
                Console.WriteLine("\t(1) Add Task");
                Console.WriteLine("\t(2) Remove Task");
                Console.WriteLine("\t(3) View all task");
                Console.WriteLine("\t(4) Exit");

                Console.Write("\nEnter choice: ");
                isChoiceSuccess = int.TryParse(Console.ReadLine(), out choices);

                if (!isChoiceSuccess) { Console.WriteLine("\nPlease choose within the options\n"); continue; }

                switch (choices)
                {
                    case 1:
                        TaskAdd(ref tasks);
                        break;

                    case 2:
                        if (tasks.Count == 0) { Console.WriteLine("\nThere is no task to rmeove\n"); continue; }
                        else { TaskRemove(ref tasks); }

                        break;

                    case 3:
                        TaskView(ref tasks);
                        break;

                    case 4:
                        Console.WriteLine("\nYou have chosen to exit\n");
                        isNavigate = false;
                        break;

                    default:
                        Console.WriteLine("\nPlease choose within the options\n");
                        break;
                }
            }
        }
        static void TaskAdd(ref List<Task> tasks)
        {
            string taskAdd;

            Console.WriteLine("\nYou have chosen Add task\n");
            Console.Write("Add a task: ");
            taskAdd = Console.ReadLine();

            tasks.Add(new Task(taskAdd));
            Console.WriteLine("\nTask added Succesfully\n");
        }

        static void TaskRemove(ref List<Task> tasks)
        {
            int taskRemove;

            Console.WriteLine("\nChoose a task to remove\n");

            for (int i = 0; i < tasks.Count; i++)
            {
                Console.WriteLine($"{i}. {tasks[i].TaskName}");
            }

            while (true)
            {
                Console.Write("Choose the number of the task you wish to remove (enter -1 to exit): ");

                if (int.TryParse(Console.ReadLine(), out taskRemove))
                {
                    if (taskRemove == -1) break;

                    if (taskRemove < tasks.Count)
                    {
                        tasks.RemoveAt(taskRemove);
                        Console.WriteLine("\nTask has been removed\n");
                        break;
                    }
                }

                Console.WriteLine("Please chooe the correct number");
            }
        }

        static void TaskView(ref List<Task> tasks)
        {
            Console.WriteLine("\nYou have chosen View all task\n");

            if (tasks.Count > 0)
            {
                for (int i = 0; i < tasks.Count; i++)
                {
                    Console.WriteLine($"{i + 1}. {tasks[i].TaskName}");
                }
                Console.WriteLine();
            }

            else
            {
                Console.WriteLine("Please add come task\n");
            }
        }

    }
    class Task
    {
        public string? TaskName { get; set; }
        public Task(string taskName)
        {
            TaskName = taskName;
        }
    }
}
```
---
Created: 2025-08-18T08:59
tags:
  - Simple-Challenge
---
```C#
class Nodes
{
    public Nodes Next { get; set; }
    public int Value { get; set; }

    public Nodes(int value)
    {
        Next = null;
        Value = value;
    }
}

class LinkedList
{
    private Nodes Head { get; set; }
    private Nodes Tail { get; set; }
    private int size;

    public LinkedList()
    {
        Head = Tail = null;
        size = 0;
    }

    public void Insert(int value)
    {
        if (Head == null)
        {
            Head = Tail = new Nodes(value);
            size++;
        }
        else
        {
            Nodes newNode = new Nodes(value);
            newNode.Next = Head;
            Head = newNode;
            size++;
        }
    }

    public void InsertTail(int value)
    {
        if (Tail == null)
        {
            Head = Tail = new Nodes(value);
        }
        else
        {
            Nodes newNode = new Nodes(value);
            Tail.Next = newNode;
            Tail = newNode;
            size++;
        }
    }

    public void Search(int value)
    {
        Nodes current = Head;
        while (current != null)
        {
            if (current.Next == null) break;
            if (current.Value == value) Console.WriteLine($"True: {current.Value}");

            current = current.Next;
        }
    }
    public void Delete(int value)
    {
        Nodes current = Head;
        while (current != null)
        {
            if (current.Next == null) break;
            if (current.Next.Value == value && current.Next != null)
            {
                Nodes deleted = current.Next;
                current.Next = current.Next.Next;
                Console.WriteLine($"{deleted.Value} was Deleted");
                size--;
            }

            current = current.Next;
        }
    }

    public void Edit(int value, int update)
    {
        Nodes current = Head;
        while (current != null)
        {
            if (current.Next == null) break;
            if (current.Value == value)
            {
                int edited = current.Value;
                current.Value = update;
                Console.WriteLine($"Succesfully edited {edited} to {current.Value}");
            }

            current = current.Next;
        }
    }

    public void Print()
    {
        Nodes current = Head;
        while (current != null)
        {
            Console.WriteLine($"Value: {current.Value}");

            if (current.Next == null) break;
            current = current.Next;
        }
    }

    public void Size() => Console.WriteLine($"Size is {size}");
    public void TailNode() => Console.WriteLine($"Tail is {Tail.Value}");

}

class Program
{
    public static void Main(string[] args)
    {
        LinkedList ll = new LinkedList();
        ll.Insert(10);
        ll.Insert(20);
        ll.Insert(30);
        ll.Insert(40);
        ll.Insert(50);
        ll.Insert(60);
        ll.Print();
        ll.Size();
        ll.Search(30);
        ll.Delete(40);
        ll.Edit(10, 90);
        ll.InsertTail(150);
        ll.InsertTail(120);
        ll.InsertTail(130);
        ll.Print();
        ll.Size();
        Console.WriteLine($"");
        ll.TailNode();
    }
}
```
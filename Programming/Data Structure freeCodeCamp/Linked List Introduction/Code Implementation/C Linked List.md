---
Created: 2025-08-12T06:46
---
### C# — LinkedList.cs

```C#
using System;
using System.Collections.Generic;
using System.Text;

public class Node<T>
{
    public T Data { get; set; }
    public Node<T> Next { get; set; }
    
    public Node(T data)
    {
        Data = data;
        Next = null;
    }
}

public class SinglyLinkedList<T>
{
    private Node<T> head;
    private int size;
    
    public SinglyLinkedList()
    {
        head = null;
        size = 0;
    }
    
    public int Count => size;
    public bool IsEmpty => head == null;
    
    public void Append(T data)
    {
        Node<T> newNode = new Node<T>(data);
        if (head == null)
        {
            head = newNode;
        }
        else
        {
            Node<T> current = head;
            while (current.Next != null)
            {
                current = current.Next;
            }
            current.Next = newNode;
        }
        size++;
    }
    
    public void Prepend(T data)
    {
        Node<T> newNode = new Node<T>(data);
        newNode.Next = head;
        head = newNode;
        size++;
    }
    
    public void Insert(int index, T data)
    {
        if (index < 0 || index > size)
            throw new IndexOutOfRangeException("Index out of range");
        
        if (index == 0)
        {
            Prepend(data);
            return;
        }
        
        Node<T> newNode = new Node<T>(data);
        Node<T> current = head;
        for (int i = 0; i < index - 1; i++)
        {
            current = current.Next;
        }
        
        newNode.Next = current.Next;
        current.Next = newNode;
        size++;
    }
    
    public T RemoveFirst()
    {
        if (head == null)
            throw new InvalidOperationException("List is empty");
        
        T data = head.Data;
        head = head.Next;
        size--;
        return data;
    }
    
    public T RemoveLast()
    {
        if (head == null)
            throw new InvalidOperationException("List is empty");
        
        if (head.Next == null) // Only one element
        {
            T data = head.Data;
            head = null;
            size--;
            return data;
        }
        
        // Find second to last node
        Node<T> current = head;
        while (current.Next.Next != null)
        {
            current = current.Next;
        }
        
        T lastData = current.Next.Data;
        current.Next = null;
        size--;
        return lastData;
    }
    
    public T RemoveAt(int index)
    {
        if (index < 0 || index >= size)
            throw new IndexOutOfRangeException("Index out of range");
        
        if (index == 0)
            return RemoveFirst();
        
        Node<T> current = head;
        for (int i = 0; i < index - 1; i++)
        {
            current = current.Next;
        }
        
        T data = current.Next.Data;
        current.Next = current.Next.Next;
        size--;
        return data;
    }
    
    public bool Remove(T data)
    {
        if (head == null)
            return false;
        
        if (head.Data.Equals(data))
        {
            RemoveFirst();
            return true;
        }
        
        Node<T> current = head;
        while (current.Next != null)
        {
            if (current.Next.Data.Equals(data))
            {
                current.Next = current.Next.Next;
                size--;
                return true;
            }
            current = current.Next;
        }
        
        return false;
    }
    
    public int IndexOf(T data)
    {
        Node<T> current = head;
        int index = 0;
        while (current != null)
        {
            if (current.Data.Equals(data))
                return index;
            current = current.Next;
            index++;
        }
        return -1;
    }
    
    public T Get(int index)
    {
        if (index < 0 || index >= size)
            throw new IndexOutOfRangeException("Index out of range");
        
        Node<T> current = head;
        for (int i = 0; i < index; i++)
        {
            current = current.Next;
        }
        return current.Data;
    }
    
    public T this[int index]
    {
        get { return Get(index); }
    }
    
    public bool Contains(T data)
    {
        return IndexOf(data) != -1;
    }
    
    public List<T> ToList()
    {
        List<T> result = new List<T>();
        Node<T> current = head;
        while (current != null)
        {
            result.Add(current.Data);
            current = current.Next;
        }
        return result;
    }
    
    public override string ToString()
    {
        if (head == null)
            return "[]";
        
        StringBuilder sb = new StringBuilder();
        Node<T> current = head;
        while (current != null)
        {
            sb.Append(current.Data);
            if (current.Next != null)
                sb.Append(" -> ");
            current = current.Next;
        }
        sb.Append(" -> null");
        return sb.ToString();
    }
}

class Program
{
    static void Main()
    {
        var ll = new SinglyLinkedList<int>();
        
        // Test append
        for (int i = 0; i < 5; i++)
        {
            ll.Append(i * 10);
        }
        Console.WriteLine($"After appending 0-40: {ll}");
        
        // Test prepend
        ll.Prepend(-10);
        Console.WriteLine($"After prepending -10: {ll}");
        
        // Test insert
        ll.Insert(2, 99);
        Console.WriteLine($"After inserting 99 at index 2: {ll}");
        
        // Test removal
        int removed = ll.RemoveFirst();
        Console.WriteLine($"Removed first element {removed}: {ll}");
        
        removed = ll.RemoveLast();
        Console.WriteLine($"Removed last element {removed}: {ll}");
        
        // Test find
        int index = ll.IndexOf(20);
        Console.WriteLine($"Index of 20: {index}");
        
        // Test get
        int value = ll.Get(1);
        Console.WriteLine($"Element at index 1: {value}");
        
        Console.WriteLine($"List as array: [{string.Join(", ", ll.ToList())}]");
        Console.WriteLine($"Length: {ll.Count}");
    }
}
```

### C# — DoublyLinkedList.cs

```C#
using System;
using System.Collections.Generic;
using System.Text;

public class Node<T>
{
    public T Data { get; set; }
    public Node<T> Next { get; set; }
    public Node<T> Prev { get; set; }
    
    public Node(T data)
    {
        Data = data;
        Next = null;
        Prev = null;
    }
}

public class DoublyLinkedList<T>
{
    private Node<T> head;
    private Node<T> tail;
    private int size;
    
    public DoublyLinkedList()
    {
        head = null;
        tail = null;
        size = 0;
    }
    
    public int Count => size;
    public bool IsEmpty => head == null;
    
    public void Append(T data)
    {
        Node<T> newNode = new Node<T>(data);
        if (head == null)
        {
            head = tail = newNode;
        }
        else
        {
            newNode.Prev = tail;
            tail.Next = newNode;
            tail = newNode;
        }
        size++;
    }
    
    public void Prepend(T data)
    {
        Node<T> newNode = new Node<T>(data);
        if (head == null)
        {
            head = tail = newNode;
        }
        else
        {
            newNode.Next = head;
            head.Prev = newNode;
            head = newNode;
        }
        size++;
    }
    
    public void Insert(int index, T data)
    {
        if (index < 0 || index > size)
            throw new IndexOutOfRangeException("Index out of range");
        
        if (index == 0)
        {
            Prepend(data);
            return;
        }
        
        if (index == size)
        {
            Append(data);
            return;
        }
        
        Node<T> newNode = new Node<T>(data);
        Node<T> current;
        
        // Choose direction based on which is closer
        if (index <= size / 2)
        {
            // Traverse from head
            current = head;
            for (int i = 0; i < index; i++)
            {
                current = current.Next;
            }
        }
        else
        {
            // Traverse from tail
            current = tail;
            for (int i = 0; i < size - index - 1; i++)
            {
                current = current.Prev;
            }
        }
        
        // Insert before current
        newNode.Next = current;
        newNode.Prev = current.Prev;
        current.Prev.Next = newNode;
        current.Prev = newNode;
        size++;
    }
    
    public T RemoveFirst()
    {
        if (head == null)
            throw new InvalidOperationException("List is empty");
        
        T data = head.Data;
        if (head == tail) // Only one element
        {
            head = tail = null;
        }
        else
        {
            head = head.Next;
            head.Prev = null;
        }
        
        size--;
        return data;
    }
    
    public T RemoveLast()
    {
        if (tail == null)
            throw new InvalidOperationException("List is empty");
        
        T data = tail.Data;
        if (head == tail) // Only one element
        {
            head = tail = null;
        }
        else
        {
            tail = tail.Prev;
            tail.Next = null;
        }
        
        size--;
        return data;
    }
    
    public T RemoveAt(int index)
    {
        if (index < 0 || index >= size)
            throw new IndexOutOfRangeException("Index out of range");
        
        if (index == 0)
            return RemoveFirst();
        
        if (index == size - 1)
            return RemoveLast();
        
        Node<T> current;
        
        // Choose direction based on which is closer
        if (index <= size / 2)
        {
            current = head;
            for (int i = 0; i < index; i++)
            {
                current = current.Next;
            }
        }
        else
        {
            current = tail;
            for (int i = 0; i < size - index - 1; i++)
            {
                current = current.Prev;
            }
        }
        
        T data = current.Data;
        current.Prev.Next = current.Next;
        current.Next.Prev = current.Prev;
        size--;
        return data;
    }
    
    public bool Remove(T data)
    {
        Node<T> current = head;
        while (current != null)
        {
            if (current.Data.Equals(data))
            {
                if (current == head)
                {
                    RemoveFirst();
                }
                else if (current == tail)
                {
                    RemoveLast();
                }
                else
                {
                    current.Prev.Next = current.Next;
                    current.Next.Prev = current.Prev;
                    size--;
                }
                return true;
            }
            current = current.Next;
        }
        return false;
    }
    
    public int IndexOf(T data)
    {
        Node<T> current = head;
        int index = 0;
        while (current != null)
        {
            if (current.Data.Equals(data))
                return index;
            current = current.Next;
            index++;
        }
        return -1;
    }
    
    public T Get(int index)
    {
        if (index < 0 || index >= size)
            throw new IndexOutOfRangeException("Index out of range");
        
        Node<T> current;
        
        // Choose direction based on which is closer
        if (index <= size / 2)
        {
            current = head;
            for (int i = 0; i < index; i++)
            {
                current = current.Next;
            }
        }
        else
        {
            current = tail;
            for (int i = 0; i < size - index - 1; i++)
            {
                current = current.Prev;
            }
        }
        
        return current.Data;
    }
    
    public T this[int index]
    {
        get { return Get(index); }
    }
    
    public bool Contains(T data)
    {
        return IndexOf(data) != -1;
    }
    
    public List<T> ToList()
    {
        List<T> result = new List<T>();
        Node<T> current = head;
        while (current != null)
        {
            result.Add(current.Data);
            current = current.Next;
        }
        return result;
    }
    
    public List<T> ToListReverse()
    {
        List<T> result = new List<T>();
        Node<T> current = tail;
        while (current != null)
        {
            result.Add(current.Data);
            current = current.Prev;
        }
        return result;
    }
    
    public override string ToString()
    {
        return ToStringForward();
    }
    
    public string ToStringForward()
    {
        if (head == null)
            return "[]";
        
        StringBuilder sb = new StringBuilder();
        Node<T> current = head;
        while (current != null)
        {
            sb.Append(current.Data);
            if (current.Next != null)
                sb.Append(" <-> ");
            current = current.Next;
        }
        return sb.ToString();
    }
    
    public string ToStringBackward()
    {
        if (tail == null)
            return "[]";
        
        StringBuilder sb = new StringBuilder();
        Node<T> current = tail;
        while (current != null)
        {
            sb.Append(current.Data);
            if (current.Prev != null)
                sb.Append(" <-> ");
            current = current.Prev;
        }
        return sb.ToString();
    }
}

class Program
{
    static void Main()
    {
        var dll = new DoublyLinkedList<int>();
        
        // Test append
        for (int i = 0; i < 5; i++)
        {
            dll.Append(i * 10);
        }
        Console.WriteLine($"After appending 0-40: {dll}");
        
        // Test prepend
        dll.Prepend(-10);
        Console.WriteLine($"After prepending -10: {dll}");
        
        // Test insert
        dll.Insert(2, 99);
        Console.WriteLine($"After inserting 99 at index 2: {dll}");
        
        // Test removal
        int removed = dll.RemoveFirst();
        Console.WriteLine($"Removed first element {removed}: {dll}");
        
        removed = dll.RemoveLast();
        Console.WriteLine($"Removed last element {removed}: {dll}");
        
        // Test bidirectional traversal
        Console.WriteLine($"Forward: {dll.ToStringForward()}");
        Console.WriteLine($"Backward: {dll.ToStringBackward()}");
        
        // Test optimized access
        Console.WriteLine($"Element at index 1: {dll.Get(1)}");
        Console.WriteLine($"Element at index {dll.Count - 1}: {dll.Get(dll.Count - 1)}");
        
        Console.WriteLine($"List as array: [{string.Join(", ", dll.ToList())}]");
        Console.WriteLine($"List reversed: [{string.Join(", ", dll.ToListReverse())}]");
        Console.WriteLine($"Length: {dll.Count}");
    }
}
```
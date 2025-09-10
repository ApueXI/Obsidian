---
Created: 2025-08-16T09:53
tags:
  - BroCode
---
```Java
public class Main {

    public static void main(String[] args) throws InterruptedException{
    	
    	long start = System.nanoTime();
    	
    	// -------- program --------
    	
    	Thread.sleep(3000);
    	
    	// -------------------------------
    	
    	long duration = (System.nanoTime() - start)/1000000;
    	System.out.println(duration + "ms");
    }
}
```

```C#
using System;
using System.Diagnostics;
using System.Threading;

class Program
{
    static void Main(string[] args)
    {
        // Start timer
        Stopwatch stopwatch = Stopwatch.StartNew();

        // -------- program --------
        Thread.Sleep(3000);
        // -------------------------

        // Stop timer
        stopwatch.Stop();

        // Duration in milliseconds
        Console.WriteLine($"{stopwatch.ElapsedMilliseconds}ms");
    }
}
```
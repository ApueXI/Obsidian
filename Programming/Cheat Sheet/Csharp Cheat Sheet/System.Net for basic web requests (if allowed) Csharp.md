---
Created: 2025-08-07T20:10
tags:
  - Optional
---
## ✅ 1. Concept Overview

The `System.Net` namespace provides classes to interact with web servers, fetch or send data over HTTP/HTTPS.

- **Modern preferred way:** `HttpClient` (in `System.Net.Http`)
- Older legacy: `WebRequest` / `HttpWebRequest`

`HttpClient` supports async calls, easier to use and recommended for new projects.

---

## 🔧 2. Common Classes & Methods

|Class|Purpose|Notes|
|---|---|---|
|`HttpClient`|Send HTTP requests asynchronously|Use with async/await|
|`HttpRequestMessage`|Customize request (method, headers)|For advanced scenarios|
|`HttpResponseMessage`|Holds HTTP response details|Status code, headers, content|
|`WebRequest`|Older HTTP requests|Synchronous by default|
|`WebResponse`|Response from `WebRequest`||

---

## 🧾 3. Summary Table of Common `HttpClient` Methods

|Method|Description|Returns|
|---|---|---|
|`GetStringAsync(url)`|Sends GET, returns response as string|`Task<string>`|
|`GetAsync(url)`|Sends GET, returns full response message|`Task<HttpResponseMessage>`|
|`PostAsync(url, content)`|Sends POST with content|`Task<HttpResponseMessage>`|
|`SendAsync(request)`|Sends custom request|`Task<HttpResponseMessage>`|
|`PutAsync(url, content)`|Sends PUT with content|`Task<HttpResponseMessage>`|
|`DeleteAsync(url)`|Sends DELETE request|`Task<HttpResponseMessage>`|

---

## 💡 4. Real-World Example: Simple GET Request

```C#
using System;
using System.Net.Http;
using System.Threading.Tasks;

class Program {
    static async Task Main() {
        using HttpClient client = new HttpClient();

        try {
            string url = "https://jsonplaceholder.typicode.com/posts/1";
            string response = await client.GetStringAsync(url);

            Console.WriteLine(response);
        }
        catch (HttpRequestException e) {
            Console.WriteLine($"Request error: {e.Message}");
        }
    }
}
```

---

## 🔧 5. Real-World Example: POST JSON Data

```C#
using System;
using System.Net.Http;
using System.Text;
using System.Threading.Tasks;

class Program {
    static async Task Main() {
        using HttpClient client = new HttpClient();

        var json = "{\"title\":\"foo\",\"body\":\"bar\",\"userId\":1}";
        var content = new StringContent(json, Encoding.UTF8, "application/json");

        HttpResponseMessage response = await client.PostAsync("https://jsonplaceholder.typicode.com/posts", content);

        string responseBody = await response.Content.ReadAsStringAsync();

        Console.WriteLine($"Status: {response.StatusCode}");
        Console.WriteLine(responseBody);
    }
}
```

---

## 🧾 6. Summary Table for Older `WebRequest`

|Usage|Code Example|
|---|---|
|Create request|`WebRequest request = WebRequest.Create("http://example.com");`|
|Get response|`WebResponse response = request.GetResponse();`|
|Read response stream|Use `StreamReader` on `response.GetResponseStream()`|

Example:

```C#
WebRequest request = WebRequest.Create("http://example.com");
using WebResponse response = request.GetResponse();
using Stream dataStream = response.GetResponseStream();
using StreamReader reader = new StreamReader(dataStream);
string responseFromServer = reader.ReadToEnd();
Console.WriteLine(responseFromServer);
```

---

## ⚠️ 7. Gotchas & Tips

|Tip|Reason|
|---|---|
|Prefer `HttpClient` over `WebRequest`|Easier async support and better API|
|Reuse `HttpClient` instance if possible|Avoid socket exhaustion|
|Always `Dispose()` clients or use `using`|Clean up resources|
|Handle exceptions (`HttpRequestException`)|Network failures and non-success status codes|
|Set timeouts explicitly|Avoid hanging requests|
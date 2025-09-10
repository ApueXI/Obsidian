---
Created: 2025-06-23T18:34
---
### HTTP methods (also called **verbs**) define the type of action performed when sending a request to a server (like GETting data or POSTing new data).

  

## **GET**

- **Use:** Retrieve data from the server.
- **Safe:** ✅ Yes
- **Idempotent:** ✅ Yes
- **Body:** 🚫 No
- **Example:**
    
    ```Plain
    GET /users/1
    ```
    

🗒️ _Use GET when you just want to read data. It shouldn't change anything._

  

## **POST**

- **Use:** Submit new data to the server (create).
- **Safe:** 🚫 No
- **Idempotent:** 🚫 No
- **Body:** ✅ Yes (sends data)
- **Example:**
    
    ```Plain
    POST /users
    {
      "name": "Alice"
    }
    ```
    

🗒️ _Use POST when you want to create a new resource._

  

## **PUT**

- **Use:** Replace an entire resource.
- **Safe:** 🚫 No
- **Idempotent:** ✅ Yes
- **Body:** ✅ Yes (full object)
- **Example:**
    
    ```Plain
    PUT /users/1
    {
      "name": "Bob",
      "age": 30
    }
    ```
    

🗒️ _Use PUT to fully update a resource. Sends the full object._

  

## **PATCH**

- **Use:** Partially update a resource.
- **Safe:** 🚫 No
- **Idempotent:** ✅ Usually
- **Body:** ✅ Yes (partial data)
- **Example:**
    
    ```Plain
    PATCH /users/1
    {
      "age": 31
    }
    ```
    

🗒️ _Use PATCH to update only specific fields of a resource._

  

## **DELETE**

- **Use:** Remove a resource.
- **Safe:** 🚫 No
- **Idempotent:** ✅ Yes
- **Body:** ❌ Usually not used
- **Example:**
    
    ```Plain
    DELETE /users/1
    ```
    

🗒️ _Use DELETE to permanently remove a resource._

  

## **HEAD**

- **Use:** Like GET, but only retrieves headers (no body).
- **Safe:** ✅ Yes
- **Idempotent:** ✅ Yes
- **Body:** 🚫 No
- **Example:**
    
    ```Plain
    HEAD /users
    ```
    

🗒️ _Use HEAD to check if a resource exists or for metadata (like size, type) without downloading the body._

  

## **OPTIONS**

- **Use:** Returns allowed HTTP methods on a resource (CORS preflight).
- **Safe:** ✅ Yes
- **Idempotent:** ✅ Yes
- **Body:** ✅ Optional
- **Example:**
    
    ```Plain
    OPTIONS /users
    ```
    

🗒️ _Use OPTIONS to see what methods the server supports for a resource._

  

# Idempotent & Safe – Quick Guide

|   |   |   |   |
|---|---|---|---|
|Method|Safe|Idempotent|Changes Data?|
|GET|✅|✅|❌|
|POST|❌|❌|✅|
|PUT|❌|✅|✅|
|PATCH|❌|✅|✅|
|DELETE|❌|✅|✅|
|HEAD|✅|✅|❌|
|OPTIONS|✅|✅|❌|
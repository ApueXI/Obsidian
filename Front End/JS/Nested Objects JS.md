---
Created: 2025-06-21T20:33
---
### **What Is a Nested Object?**

A **nested object** is an object that contains another object as one of its properties.

```JavaScript
const user = {
  name: "Alice",
  contact: {
    email: "alice@example.com",
    phone: "123-4567"
  }
};
```

- `contact` is a **nested object** inside `user`.

  

### **Accessing Nested Properties**

```JavaScript
console.log(user.contact.email);        // "alice@example.com"
console.log(user["contact"]["phone"]); // "123-4567"
```

- Use **dot notation** or **bracket notation**.

  

### **Modifying Nested Values**

```JavaScript
user.contact.email = "newemail@example.com";
user.contact.phone = "987-6543";
```

- Navigate to the property and assign a new value.

  

### **Adding to a Nested Object**

```JavaScript
user.contact.address = "123 Street";
console.log(user.contact.address); // "123 Street"
```

- You can add new keys to nested objects anytime.

  

### **Creating Deeply Nested Objects**

```JavaScript
const data = {
  user: {
    profile: {
      name: "Bob",
      location: {
        city: "Manila",
        zip: 1000
      }
    }
  }
};

console.log(data.user.profile.location.city); // "Manila"
```

- You can nest as many levels as needed.

  

### **Optional Chaining (Safe Access)**

```JavaScript
console.log(data.user?.profile?.location?.zip); // 1000
console.log(data.user?.account?.balance);       // undefined (no error)
```

- Use `?.` to avoid **errors if a property doesn’t exist**.

  

### **Destructuring Nested Objects**

```JavaScript
const {
  user: {
    profile: {
      name,
      location: { city }
    }
  }
} = data;

console.log(name); // "Bob"
console.log(city); // "Manila"
```

- You can **pull out nested values** in one line using destructuring.

  

### **Looping Through Nested Objects**

```JavaScript
const grades = {
  math: { midterm: 90, final: 95 },
  science: { midterm: 85, final: 80 }
};

for (let subject in grades) {
  for (let exam in grades[subject]) {
    console.log(`${subject} ${exam}: ${grades[subject][exam]}`);
  }
}
```

- Use nested `for...in` loops to iterate through levels.

  

### Summary Table

|   |   |   |
|---|---|---|
|Action|Example|Description|
|Access nested|`obj.a.b.c`|Dot or bracket notation|
|Modify nested|`obj.a.b = newVal`|Assign like normal|
|Add nested|`obj.a.b = {}` / `obj.a.b.c = val`|Create properties as needed|
|Destructure nested|`const { a: { b } } = obj`|Pull values from deep inside|
|Optional chaining|`obj?.a?.b`|Prevents errors from `undefined`|
|Loop nested|`for (let k in obj.a)`|Use nested loops for nested props|

  

```JavaScript
const person = {
    fullname: "Laren Jau Acob",
    age: 19,
    isStudent: true,
    hobbies: ["gaming", "sleeping", "eating"],
    address: {
        street: "1234 pakil street",
        city: "Laguna",
        country: "Philiippines",
    },
};

console.log(person.fullname);
console.log(person.age);
console.log(person.isStudent);
console.log(person.hobbies);
console.log(person.hobbies[2]);
console.log(person.address);
console.log(person.address.country);
```

  

```JavaScript
const person = {
    fullname: "Laren Jau Acob",
    age: 19,
    isStudent: true,
    hobbies: ["gaming", "sleeping", "eating"],
    address: {
        street: "1234 pakil street",
        city: "Laguna",
        country: "Philiippines",
    },
};

for (let property in person.address) {
    console.log(person.address[property]);
    
    
}
```

  

```JavaScript
class Address {
    constructor(street, city, country) {
        this.street = street;
        this.city = city;
        this.country = country;
    }
}

class Person {
    constructor(name, age, ...address) {
        this.name = name;
        this.age = age;
        this.address = new Address(...address);
    }
}

const person1 = new Person(
    "Timothy",
    19,
    "1234 pakil st,",
    "Laguna",
    "Philippines"
);

const person2 = new Person(
    "Laren Jay",
    25,
    "1234 Bubukal st,,",
    "Batangas",
    "North Korea"
);

const person3 = new Person("Red", 35, "1234 Calios st,,", "Quezon", "China");

console.log(person1);
console.log(person2);
console.log(person3);
```
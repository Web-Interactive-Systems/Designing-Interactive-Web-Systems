---
type: NoteCard
tags: []
---

# JavaScript Objects Fundamentals
*   **Object Literal**: A way to create objects in JavaScript using the **`{}`** syntax.

    ```js
    const bar = {
      name: 'foo',
      city: 'Laval',
      greet: function() {
        console.log('Bonjour, my name is ' + this.name);
      }
    };
    ```

*   **Properties and Methods**: Objects in JavaScript can have properties (keys and values) and methods (functions).

    ```js
    const bar = {
      name: 'foo',
      city: 'Laval',
      greet: function() {
        console.log('Bonjour, my name is ' + this.name);
      }
    };

    // name is a property
    console.log(person.name); // Output: ??

    // greet is a function
    console.log(person.greet()); // Output: ??
    ```

*   **Getters and Setters**: A way to define computed properties that are accessed like regular properties.

    ```js
    const person = {
      name: 'foo',
      city: 'Laval',
      get title() {
        return 'Bonjour, my name is ' + this.name + ' from ' + this.city;
      },
      set title(title) {
        const parts = title.split(' ');
        this.name = parts[0];
        this.city = parts[1];

      this.name = name;
      }
    };

    person.title = 'Bar Lyon';
    console.log(person.name); // ??
    console.log(person.city); // ??
    console.log(person.title); // ??
    ```

*   **Classes**: A more formal way of defining objects in JavaScript, introduced in ES6.

    ```js
    class Person {
      constructor(name, city) {
        this.name = name;
        this.city = city;
      }

      greet() {
         console.log('Bonjour, my name is ' + this.name + ', I\'m from ' + this.city);
      }
    }

    const john = new Person('John', 'Laval');
    john.greet();
    ```

*   **Extends**: A keyword used in classes to inherit from a parent class.

    ```js
    class Animal {
      constructor(name) {
        this.name = name;
      }

      speak() {
        console.log(this.name + ' makes a ??.');
      }
    }

    // see the use of `extends`
    class Cat extends Animal {
      speak() {
        console.log(this.name + ' Meow.');
      }
    }

    const c = new Cat('Mjay');

    c.speak(); // ??
    ```

*   **Super**: A keyword used in classes to call the parent constructor or method.

    ```js
    class Animal {
      constructor(name) {
        this.name = name;
      }

      speak() {
        console.log(this.name + ' makes a ??.');
      }
    }

    class Cat extends Animal {
      constructor(name) {
        super(name);
      }

      speak() {
        super.speak();
        console.log(this.name + ' Meow.');
      }
    }

    const c = new Cat('Mjay');

    c.speak(); // ??
    ```

*   **Prototypes**: A mechanism for inheritance in JavaScript where objects inherit properties and methods from a prototype object.

    ```js
    function Person(name) {
      this.name = name;
    }

    Person.prototype.greet = function() {
      console.log('Hello, my name is ' + this.name);
    };

    const bar = new Person('Foo');
    bar.greet();
    ```

*   **Inheritance**: The process of defining a new object based on an existing object, inheriting its properties and methods.

    ```js
    function Student(name, grade) {
      Person.call(this, name);
      this.grade = grade;
    }

    // see Person above
    Student.prototype = Object.create(Person.prototype);
    Student.prototype.constructor = Student;

    Student.prototype.study = function() {
      console.log(this.name + ' is coding js.');
    };

    const sara = new Student('Sara', 9);

    sara.greet();
    sara.study();
    ```

## Other concepts

*   **Polymorphism**: The ability of objects to take on many forms or types, depending on context.

    ```js
    // Todo: provide an example of polymorphism
    ```
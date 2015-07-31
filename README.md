# JavaScript Style Guide

PHP Style Guide to maintain readable code, that looks like it was written by one person, even if a whole team was working on it.
Highly inspired by [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript/tree/8d2a83385795b8a3763890a344f9592e36ed9407/es5)

## Table of contents
1. [Tabs](#tabs)
2. [Whitespace](#whitespace)
3. [Semicolons](#semicolons)
4. [Commas](#commas)
5. [Naming conventions](#naming-conventions)
6. [Variables](#variables)
7. [Objects](#objects)
8. [Accessors](#accessors)
9. [Arrays](#arrays)
10. [Strings](#strings)
11. [Events](#events)
12. [Functions](#functions)
13. [Iterators](#iterators)
14. [Type casting](#type-casting)
15. [Comparison Operators & Equality](#comparison-operators--equality)
16. [Blocks](#blocks)
17. [Comments](#comments)
18. [jQuery](#jquery)


### Tabs
- [1.1](#1.1) Use soft spaces instead of tabs.
- [1.2](#1.2) Use an intendation of 2 spaces.

**[⬆ back to top](#table-of-contents)**


### Whitespace
- [2.1](#2.1) Place one space before the leading brace.
```javascript
  var test = function() {};
  person.set('attr', {
      age: 21
  });
```

- [2.2](#2.2) Place one space before the opening paranthesis in control statements (`if`, `while` etc.)
```javascript
  if (person.name === 'John Doe') {}
```

- [2.3](#2.3) Place no space before the argument list in function calls and declarations.
```javascript
  var test = function(firstParameter) {};
```

- [2.4](#2.4) Set off operators with spaces.
```javascript
  var x = 1 + 2;
```

- [2.5](#2.5) Use indentation when making long method chains. Use a leading dot, which emphasizes that the line is a method call, not a new statement.
```javascript
  $('.items')
      .addClass('.additional-class')
      .attr('width', '110')
      .attr('height', '150')
```

**[⬆ back to top](#table-of-contents)**


### Semicolons
- [3.1](#3.1) Use them.
```javascript
  var age = 21; //use semicolons
```

**[⬆ back to top](#table-of-contents)**


### Commas
- [4.1](#4.1) Use trailing commas.
```javascript
  var numbers = [
      1,
      2,
      3,
  ]
```

- [4.2](#4.2) Use additional trailing commas for the last elements in arrays.
```javascript
  var numbers = [
      1,
      2,
      3, // additional trailing comma
  ]
```

**[⬆ back to top](#table-of-contents)**


### Naming conventions
- [5.1](#5.1) Use camelCase when naming objects, functions, variables, and instances.
```javascript
  var firstName = 'John';
  var myObject = {};
  var testFunction = function() {};
```

- [5.2](#5.2) Use SNAKE_CASE and uppercase for constants.
```javascript
  const API_URL = '/api';
```

- [5.3](#5.3) Use PascalCase when naming constructors or classes.
```javascript
  function Person(options) {
      this.name = options.name;
  }
  var person = Person({
      name: 'John Doe'
  });
```

- [5.4](#5.4) Use a leading underscore `_` when naming private properties.
```javascript
  this._firstName = 'John';
```

- [5.5](#5.5) Don't use reserved words.
```javascript
  // bad
  var default = 42;
  // good
  var defaultNumber = 42;
```

**[⬆ back to top](#table-of-contents)**


### Variables
- [6.1](#6.1) Always use `var` to declare variables. Not doing so will result in global variables. We want to avoid polluting the global namespace. Captain Planet warned us of that.
```javascript
  var name = 'John Doe';
```

- [6.2](#6.2) Use one `var` per scope. Declare them at the top of their scope.
```javascript
  var name = 'John Doe',
      age = '21',
      createPerson;
  createPerson = function(name, age) {
      var person,
          adult = 18;
      age = adult;
      person = new Person({
          name: name, 
          age:age
      });
      return person;
  };
  createPerson(name, age);
```

- [6.3](#6.3) Declare unassigned variables last. This is helpful when later on you might need to assign a variable depending on one of the previous assigned variables.
```javascript
  var name = 'John Doe',
      age = '21',
      createPerson;
```

**[⬆ back to top](#table-of-contents)**


### Objects
- [7.1](#7.1) Use the literal syntax for object creation.
```javascript
  var person = {
      name: 'John Doe'
  };
```

- [7.2](#7.2) Methods can return this to help with method chaining.
```javascript
  Person.prototype.walk = function(meters) {
      console.log('I walked ${meters}m');
      return this;
  }:
  Person.prototype.jump = function() {
      console.log('I jumped very high');
      return this;
  };

  var person = new Person();
  person.walk().jump();
```

- [7.3](#7.3) Use dot notation when accessing properties.
```javascript
  var person = {
      name: 'John Doe'
  };
  var name = person.name;
```

- [7.4](#7.4) Use subscript notation `[]` when accessing properties with a variable.
```javascript
  var person = {
      name: 'John Doe'
  },
  property = 'name';
  var name = person[property];
```

**[⬆ back to top](#table-of-contents)**


### Accessors
- [8.1](#8.1) Accessor functions for properties are not required.

- [8.2](#8.2) If you do make accessor functions use `getVal()` and `setVal('hello')`.
```javascript
  person.setAge(21);
  var age = person.getAge();
```

- [8.3](#8.3) If the property is a `boolean`, use `isVal()` or `hasVal()`.
```javascript
  if (person.hasCoffee()) {}
  if (person.isAlive()) {}
```

- [8.4](#8.4) It's okay to create `get()` and `set()` functions, but be consistent.
```javascript
  function Person(options) {
      this.set('name', options.name);
  }
  Person.prototype.set = function(key, val) {
      this[key] = val;
  };
  Person.prototype.get = function(key) {
      return this[key];
  };
```

**[⬆ back to top](#table-of-contents)**


### Arrays
- [9.1](#9.1) Use the literal syntax for array creation.
```javascript
  var persons = [];
```

- [9.2](#9.2) Array#push instead of direct assignment to add items to an array.
```javascript
  var persons = [];
  persons.push(person);
```

- [9.3](#9.3) Use `slice` to copy arrays.
```javascript
  var numbers = [4, 2];
  var numbersCopy = numbers.slice();
```

**[⬆ back to top](#table-of-contents)**


### Strings
- [10.1](#10.1) Use single quotes `''` for strings.
```javascript
  var name = 'John Doe';
```

- [10.2](#10.2) Strings longer than 100 characters should be written across multiple lines using string concatenation.
```javascript
  var description = 'I'm a very long text and need to be written across multiple lines using string ' + 
    'concatenation.';
```

- [10.3](#10.3) **Note**: If overused, long strings with concatenation could impact performance. [jsPerf](http://jsperf.com/ya-string-concat) & [Discussion](https://github.com/airbnb/javascript/issues/40). 

- [10.4](#10.4) When programmatically building up strings, use template strings instead of concatenation.
```javascript
  var person = {
      name: 'John Doe',
      walk(meters) {
          return '${this.name} walked ${meters}m.';
      }
  };
```


### Functions
- [11.1](#11.1) Use function expressions instead of function declarations.
```javascript
  var createPerson = function() {};
```

- [11.2](#11.2) Never declare a function in a non-function block (if, while, etc). Assign the function to a variable instead. Browsers will allow you to do it, but they all interpret it differently, which is bad news bears.
```javascript
  // Don't do this!
  if (isTrue) {
      var createPerson = function() {};
  }
```

- [11.3](#11.3) Use default parameter syntax rather than mutating function arguments.
```javascript
  var createPerson = function() {};
```

**[⬆ back to top](#table-of-contents)**


### Events
- [12.1](#12.1) When attaching data payloads to events (whether DOM events or something more proprietary like Backbone events), pass a hash instead of a raw value. This allows a subsequent contributor to add more data to the event payload without finding and updating every handler for the event.
```javascript
  $(this).trigger('productBought', {
      productId: 42
  });
  $(this).on('productBought', function(e, data) {
      productId = data.productId;
  });
```

**[⬆ back to top](#table-of-contents)**


### Iterators
- [13](#13.1) Don't use iterators. Prefer JavaScript's higher-order functions like map() and reduce() instead of loops like for-of.
```javascript
  var numbers = [4, 2];
  numbers.forEach(function(num) {
      console.log(num);
  });
```

**[⬆ back to top](#table-of-contents)**


### Type Casting
- [14.1](#14.1) Use `String` for strings.
```javascript
  var stringValue = String(42);
```

- [14.2](#14.2) Use `parseInt` for Numbers and always with a radix for type casting.
```javascript
  var intValue = parseInt('42', 11);
```

- [14.3](#14.3) Use `Boolean` for booleans.
```javascript
  var isTrue = Boolean(0);
```

**[⬆ back to top](#table-of-contents)**


### Comparison Operators & Equality
- [15.1](#15.1) Use `===` and `!==` over `==` and `!=`.

- [15.2](#15.2) **Note:** Conditional statements such as the if statement evaluate their expression using coercion with the ToBoolean abstract method and always follow these simple rules:
    + Objects evaluate to true
    + Undefined evaluates to false
    + Null evaluates to false
    + Booleans evaluate to the value of the boolean
    + Numbers evaluate to false if +0, -0, or NaN, otherwise true
    + Strings evaluate to false if an empty string '', otherwise true
    ```javascript
      if ([0]) {
          // true
          // An array is an object, objects evaluate to true
      }
    ```
    
- [15.3](#15.3) Use shortcuts.

- [15.4](#15.4) **Note:** For more information see [Truth Equality](https://javascriptweblog.wordpress.com/2011/02/07/truth-equality-and-javascript/#more-2108) and JavaScript by Angus Croll.

**[⬆ back to top](#table-of-contents)**

### Blocks
- [16.1](#16.1) Use braces with all multi-line blocks.
```javascript
  if (!age) return false; 
  // or
  if (!age) {
      return false;
  }
  // but NOT
  if (!age) { return false; }
  // or
  if (!age)
      return false;
```

- [16.2](#16.2) If you're using multi-line blocks with if and else, put else on the same line as your if block's closing brace.
```javascript
  if (age) {
      console.log('You have an age.');
  } else {
      console.log('Uups! Looks like you are an unborn');
  }
```

**[⬆ back to top](#table-of-contents)**


### Comments
- [17.1](#17.1) Use /** ... */ for multi-line comments. Include a description, specify types and values for all parameters and return values.
```javascript
  /**
   * Create a new person.
   *
   * @param {string} name
   * @return {Person}
   */
   var createPerson = function(name) {
      return new Person({
          name: name
      });
   }
```

- [17.2](#17.2) **Note:** For more information see [JSDoc](http://usejsdoc.org/).

- [17.3](#17.3) Use `//` for single line comments. Place single line comments on a newline above the subject of the comment. Put an empty line before the comment.
```javascript
  console.log('Make pretty comments!');

  // Create a new person
  var person = new Person();
```

- [17.4](#17.4) Use `// FIXME:` to annotate problems.
```javascript
  // FIXME: Something is wrong here, please fix it
```

- [17.5](#17.5) Use `// TODO:` to annotate solutions to problems.
```javascript
  // TODO: Write more code!
```

**[⬆ back to top](#table-of-contents)**


### jQuery
- [18.1](#18.1) Cache jQuery lookups.
```javascript
  var setSidebar = function() {
      var sidebar = $('.sidebar');
      sidebar.hide();
      sidebar.show();
  };
```

**[⬆ back to top](#table-of-contents)**

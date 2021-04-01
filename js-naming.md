# VARIABLES
A variable should be self-descriptive. It shouldn't be needed a comment for additional documentation:
```javascript
// bad
var value = 'John Smith';
var x = 'John Smith';
 
// good
var userName = 'John Smith';
```

Use camelCase to name variable:
```javascript
// bad
var firstname;
var first_name;
var FIRSTNAME;
var FIRST_NAME;
 
// good
var firstName;
```
> With exceptions for constants, privates, and classes/components.

## VARIABLES: BOOLEAN
Use prefix like _is_, _are_, or _has_ to distinguish a boolean from another variable by just looking at it:
```javascript
// bad
var activeUser = true;
var equal = false; 
var loaded = true;

// good
var isActiveUser = true;
var areEqual = false;
var hasLoaded = true;
```

## VARIABLES: COLLECTIONS
Use plural to show that variable contains collection:
```javascript
// bad
var activeUser = [{id: 1, name: 'John Smith'}, {id: 2, name: 'Peter Strom'}];
var activeUserList = [{id: 1, name: 'John Smith'}, {id: 2, name: 'Peter Strom'},];

// good
var activeUsers = [{id: 1, name: 'John Smith'}, {id: 2, name: 'Peter Strom'}];
```

# FUNCTION
Name functions in camel case. 
> Best practices: tell what the function is doing by giving the function name a verb as prefix.
```javascript
// bad
function name(firstName, lastName) {
  return `${firstName} ${lastName}`;
}
 
// good
function getName(firstName, lastName) {
  return `${firstName} ${lastName}`;
}
```
> Best practices: if you doubt - favor descriptive over concise
```javascript
//bad
function filterUsers(conditions) {}

// good
function filterUsersByNameOrEmail(conditions) {}
```

> Best practices: do not use generic names for specific cases.
```javascript
// bad 
function loadData() {}

// good
function loadPassengers() {}
```

# Factory
Even thought factory return object instances it is not constructor so name it as regular function but add suffix `Factory`

```javascript
// bad
const user = () => { ... }
const User = () => { ... }
const makeUser = () => { ... }

//good
const userFactory = () => { ... }
```

# Class
When constructor is called to instantiate a new instance of a class, its name should appear in Pascal Case, in contrast to other data structures:

```javascript
//bad
class user {
  constructor(firstName, lastName) { ... }
}
var me = new user('John', 'Smith');

//good
class User {
  constructor(firstName, lastName) { ... }
}
var me = new User('John', 'Smith');
```

# Class Members
Follow the same rules as for regular functions and variables - use self-descriptive names in camelCase
```
class User {
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }
 
  getFullName() {
    return `${this.firstName} ${this.lastName}`;
  }
}
```

# Class Members: Private 
JS doesn't enforce access levels restrictions but you can mark "internal use only" properties and methods via undescore prefix.
Even though TS have level restriction support it is still good to have visual distinguish between public and private members
```
class User {
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.fullName = this._getFullName();
  }
 
  _getFullName() {
    return `${this.firstName} ${this.lastName}`;
  }
}

var user = new User('John', 'Smith');

// bad
console.log(user._getFullName());

// good
console.log(user.fullName);
```

# Component
Every time when component name appears in code it should be with capital first letter, no matter is it class-based or function-based component

```javascript
//bad
class user {
  constructor({firstName, lastName}) { ... }
}
<user firstName="John" lastName="Smith"/>;

function user({firstName, lastName}) { ... }
<user firstName="John" lastName="Smith"/>;

//good
class User {
  constructor({firstName, lastName}) { ... }
}
<User firstName="John" lastName="Smith"/>;

function User({firstName, lastName}) { ... }
<User firstName="John" lastName="Smith"/>;
```

#Global variables and constants
A global variables/constants are declared at the top of a file.
Use let and camelCase if it is mutable.
Use const and UPPERCASE with underscore if it is immutable.
Declare all const first.
```
// bad
const apiKey = '7dd791a7-cc5f-4534-8fa8-77e8b5b613bf';
let USER_PROFILE = await loadUserProfile(); 

// good
const  API_KEY = '7dd791a7-cc5f-4534-8fa8-77e8b5b613bf';
let userProfile = await loadUserProfile(); 
```

# Acronims 
Do not capitalize them, use rules for regular variables and constant.
Add short descriptive comment when you first introduce the abbreviation.

```javascript
// bad
const SPSLayout = (props) => {} //wtf is SPS?

// good
/**
* SPS - is short for `self profile setup`
*/
const SpsLayout = (props) => {} //wtf is SPS?
```

# Files
// to be discussed - kebab case vs component names

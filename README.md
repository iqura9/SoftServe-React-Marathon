# SoftServe js tasks

## _SPRINT- 2. JS for React_

## Task 1

Implement the **getModifiedArray(array)** function, which takes an arbitrary array, and returns an array with the value of the first element of the array equal to “Start”, the last element of the array equal to “End” and the rest of elements should be the same as in an initial array. The initial array should stay unchanged.

Function example:

getModifiedArray([12, 6, 22, 0, -8])); // [‘Start’, 6, 22, 0, ‘End’]

Code:

```js function getModifiedArray(array) {
   const resArray = array.map((el,index)=> {
       if(index==0) return 'Start';
       if(index==array.length-1) return 'End';
       return el;
   })
   return resArray;
}
```

Result:

<img src="./SPRINT- 2. JS for React/images/img1.jpg">

# Task 2

The function **filterByN** receives an array of integers, a number and a parameter (greater, less). Print a new array, where all elements will be greater/less than this number

By default, the number is 0, the parameter is greater.

Example:

filterNums([-1, 2, 4, 0, 55, -12, 3], 11, 'greater'); //[ 55]

filterNums([-2, 2, 3, 0, 43, -13, 6], 6, 'less'); // [-2, 2, 3, 0, -13]

filterNums([-2, 2, 3, 0, 43, -13, 6], -33, 'less'); // []

filterNums([-2, 2, 3, 0, 43, -13, 6]); // [2, 3, 43, 6]

filterNums([-2, 2, 3, 0, 43, -13, 6], 23); // [43]

Code:

```js
const filterNums = (array, number = 0, parameter = "greater") => {
  if (parameter === "greater") return array.filter((f) => f > number);
  return array.filter((f) => f < number);
};
```

Result:

<img src="./SPRINT- 2. JS for React/images/img2.jpg">

# Task 3

Find the **maximum** interval between two consecutive arguments.

Example:

maxInterv(3, 5, 2, 7); //5

maxInterv(3, 5, 2, 7, 11, 0, -2); //11

maxInterv(3, 5); //2

maxInterv(3); //0

Code:

```js
const maxInterv = (...arg) => {
  if (arg.length <= 1) return 0;
  let res = -100;
  [...arg].reduce((a, b) => {
    res = Math.max(res, Math.abs(a - b));
    return b;
  });
  return res;
};
```

Result:

<img src="./SPRINT- 2. JS for React/images/img3.jpg">

# Task 4

The function takes any number of strings and returns the sum of their lengths.

Example:

console.log(sumOfLen('hello', 'hi')); //7

console.log(sumOfLen('hi')); //2

console.log(sumOfLen()); //0

console.log(sumOfLen('hello', 'hi', 'my name', 'is')); //16

Code:

```js
const sumOfLen = (...arg) => {
  if (arg.length <= 0) return 0;
  return arg.reduce((sum, el) => {
    if (typeof sum == "string") sum = 0;
    return sum + el.length;
  }, arg[0]);
};
```

Result:

<img src="./SPRINT- 2. JS for React/images/img4.jpg">

# Task 5

Write a function **combineArray(arr1, arr2)**, which takes 2 arrays, and returns a new array consisting only of numeric elements of arrays arr1 and arr2.

Function example:

combineArray([12, "User01", 22, true, -8], ["Index", 6, null, 15])); // [12, 22, -8, 6, 15]

Code:

```js
function combineArray(arr1, arr2) {
  return [
    ...arr1.filter((f) => typeof f == "number"),
    ...arr2.filter((f) => typeof f == "number"),
  ];
}
```

Result:

<img src="./SPRINT- 2. JS for React/images/img5.jpg">

# Task 6

Implement the **longestLogin(loginList)** function, which takes an array of user logins loginList and returns the longest login. If the logins of the same length are the longest in the array, the login element with the largest index is returned. Tip: You can use the reduce() method to solve the task.

Function examples:

longestLogin(["serg22", "tester_2", "Prokopenko", "guest"]); // Prokopenko

longestLogin(["user1", "user2", "333", "user4", "aa"]); // user4

Code:

```js
function longestLogin(loginList) {
  return loginList.reduce((res, val) => {
    if (res.length > val.length) return res;
    else return val;
  });
}
```

Result:

<img src="./SPRINT- 2. JS for React/images/img6.jpg">

# Task 7

Implement the **processArray(arr, factorial)** function, which takes the first parameter of the array arr, and the second parameter the function factorial and processes each element of the array arr with the function factorial, returning a new array (the source array arr does not change)

The function factorial(n) calculates and returns the factorial of the number n. For example factorial(4) returns 24.

Example

// determines the factorial of the number n

function factorial(n) { // your code};

processArray([1, 2, 3, 4, 5], factorial); // [1, 2, 6, 24, 120]

Code:

```js
function factorial(n) {
  if (n <= 1) return 1;
  return n * factorial(n - 1);
}

function processArray(arr, factorial) {
  return arr.map((el) => factorial(el));
}
```

Result:

<img src="./SPRINT- 2. JS for React/images/img7.jpg">

# Task 8

Using the default parameter technique, overload the **overloadedFunc()** function, which takes 3 arguments. For the 1st argument of the function set the default value [1, 2, 3], for the 2nd - the value 2, for the 3rd - the function that returns the product of the first two arguments, and the function can multiply both arrays and numbers.

The overloadedFunc() function returns the result of the default function.

Usage example:

<img src="./SPRINT- 2. JS for React/images/example.png">

Code:

```js
const func = require("./Checker.js");

const multiply = (a, b) => {
  if (typeof a === "number" && typeof b === "number") return a * b;
  if (Array.isArray(a) && typeof b === "number") return a.map((el) => el * b);
};

function overloadedFunc(arg1 = [1, 2, 3], arg2 = 2, arg3 = multiply) {
  return arg3(arg1, arg2);
}
```

Result:

<img src="./SPRINT- 2. JS for React/images/img8.jpg">

# Task 9

Please, implement a function combineFunctions that takes any number of functions as an argument and returns a function that is a composition of the arguments.

For example:

negate = function(x){ return -x; };

halve = function(x){ return x / 2; };

square = function(x){ return x \* x; };

double = function(x){ return 2 \* x; };

combineFunctions(negate, halve, square) should return a function

square(halve(negate(x)))

combineFunctions(negate, double) should return a function

double(negate(x)))

Code:

```js
const combineFunctions = (...func) => {
  return function (x) {
    let temp = x;
    let len = func.length;
    for (let i = 0; i < len; i++) temp = func[i](temp);
    return temp;
  };
};
```

Result:

<img src="./SPRINT- 2. JS for React/images/img9.jpg">

# Task 10

Suppose, you have an array of students:

```js
let students = [
  {
    name: "Anna",
    languages: ["English", "Ukrainian"],
    age: 21,
  },
  {
    name: "Bob",
    languages: ["Polish", "Spanish"],
    age: 26,
  },
  {
    name: "Alice",
    languages: ["Italian", "Russian"],
    age: 18,
  },
];
```

Please, implement a function getLanguages.

The function takes an array of students as a first parameter

and a condition on a student (function)

getLanguages should return an array of languages from students that satisfy a condition.

**For example:**

```js
getLanguages(students, student => student.age < 26) should return

['English', 'Ukrainian',  'Italian', 'Russian']
```

```js
getLanguages(students, student => student.name === 'Alice') should return

['Italian', 'Russian']
```

```js
getLanguages(students) should return

['English', 'Ukrainian','Polish', 'Spanish', 'Italian', 'Russian']
```

Try to use reduce and not use loops to solve this task.

Code:

```js
const getLanguages = (students, func = (f) => true) => {
  return [...students]
    .filter(func)
    .map((el) => el.languages)
    .reduce((left, right) => left.concat(right));
};
```

Result:

<img src="./SPRINT- 2. JS for React/images/img10.jpg">

# Task 11

Implement 5 functions that take strings of data and process them in a certain way.

1. The upperCase() function takes string data as an argument and returns it to uppercase.

2. The tripleExclaim() function takes string data as an argument and returns it by adding three exclamation marks to it.

3. The split() function takes a separator as an argument, returns a function that accepts string data split by the separator character into an ordered set of substrings, and returns an array of those substrings.

4. The join() function takes separator as an argument, returns a function that takes an array of string data that are concatenated into a string by separator, and returns that string.

5. The copy() function takes string data as an argument and returns it repeating 2 times.

Implement the **createComposition()** function, which can take any number of functions as arguments, and create a composition from them. The **createComposition()** function takes our 5 functions as arguments. The **createComposition()** function returns a function that takes its initial value as an argument. This nested function successively passes through an array of functions with each iteration returning the result of calling the accumulated value of the current function argument. The reduce() method can be used here.

The final function result is assigned the function **createComposition()**, which takes our 5 functions as arguments in the appropriate order. (split with '\_' argument, join with ' ' argument)

Tips.

Consider that the result of one function can be passed as an argument to another function.

Pay attention to the order of the function arguments.

If you have difficulty implementing the createComposition() function, check out the "Useful links" for the material on function composition.

Usage example:

// implementation of 5 atomic functions

// implementation of createComposition function

```js
const result = createComposition( // 5 function-arguments )

console.log(result("by_ticket_now"));  //  BY TICKET NOW!!! BY TICKET NOW!!!
console.log(result("total sale")); //  TOTAL SALE!!! TOTAL SALE!!!
```

Code:

```js
const upperCase = (str) => str.toUpperCase();

const tripleExclaim = (str) => str + "!!!";

const split = (separator) =>
  function (str) {
    return str.split(separator);
  };
const join = (separator) =>
  function (arr) {
    return arr.join(separator);
  };

const copy = (str) => str + " " + str;

const createComposition = (...args) => {
  let len = args.length;
  return function (str) {
    let temp = str;
    for (let i = 0; i < len; i++) {
      temp = args[i](temp);
    }
    return temp;
  };
};

const result = createComposition(
  upperCase,
  tripleExclaim,
  split("_"),
  join(" "),
  copy
);
```

Result:

<img src="./SPRINT- 2. JS for React/images/img11.jpg">

## _SPRINT 4. Object-oriented design (OOD) Object-oriented programming (OOP)_

# Task 1

Create a Movie class, the constructor of which accepts 3 parameters: movie name name, movie genre category and start year of startShow.

The class has a watchMovie() method that returns a phrase and adds a movie name name parameter to it at the end. For example, "I watch the movie Titanic!"

Create an instance of the movie1 class with the title of the movie "Titanic", the genre "drama" and 1997 release.

Create an instance of the movie2 class with the title of the movie "Troya", the genre "historical" and the 2004 release.

Code:

```js
const Checker = require("./Checker.js");

class Movie {
  constructor(name, category, startShow) {
    this.name = name;
    this.category = category;
    this.startShow = startShow;
  }
  watchMovie() {
    return `I watch the movie ${this.name}!`;
  }
}
movie1 = new Movie("Titanic", "drama", 1997);
movie2 = new Movie("Troya", "historical", 2004);
```

# Task 2

Implement the Student class, the constructor of which accepts 2 parameters fullName - the name and surname of the student, direction - the direction in which he studies.

Create a showFullName() method that returns the student's first and last name.

Create a nameIncludes(data) method that, using the showFullName() method, checks for the text data argument in the student’s name and returns true if a match is found or false if not found.

Create a static studentBuilder() method that returns a new instance of the class named ‘Ihor Kohut’ and the direction ‘qc’.

Create a getter and setter direction() to read and specify the direction field.

Create an instance of class stud1 named 'Ivan Petrenko' and direction 'web'.

Create an instance of class stud2 named 'Sergiy Koval' and direction 'python'.

Create an instance of the stud3 class named ‘Ihor Kohut’ and the direction ‘qc’ using the static studentBuilder() method.

Usage example:

```js
const stud1 = new Student("Ivan Petrenko", "web");

stud1.nameIncludes("Ivan"); // true

stud1.nameIncludes("Denysenko"); // false
```

Code:

```js
const Checker = require("./Checker.js");

class Student {
  constructor(fullName, direction) {
    this._fullName = fullName;
    this._direction = direction;
  }
  showFullName() {
    return this._fullName;
  }
  nameIncludes(data) {
    return this.showFullName().includes(data);
  }
  get direction() {
    return this._direction;
  }
  set direction(direction) {
    this._direction = direction;
  }
  static studentBuilder() {
    return new Student("Ihor Kohut", "qc");
  }
}

const stud1 = new Student("Ivan Petrenko", "web");
const stud2 = new Student("Sergiy Koval", "python");
const stud3 = Student.studentBuilder();
```

# Task 3

Product constructor should provide a generation of unique product id within the application no matter how many products are created.

Distributor can store information about products in its products property and has an ability to add and remove a product.

addProduct adds a new property to products with name of product id and value - product name.

removeProduct removes a property with specified id from products

Please, use Symbol data type.

Code:

```js
class Distributor {
  constructor() {
    this.products = {};
  }

  addProduct(id, name) {
    this.products[id] = name;
  }

  removeProduct(id) {
    delete this.products[id];
  }
}

const localDistributor = new Distributor();
const localDistributor2 = new Distributor();

class MyProduct {
  constructor(name) {
    this.id = Symbol(name);
    this.name = name;
  }

  distribute(distributor) {
    distributor.addProduct(this.id, this.name);
  }
}
```

# Task 4

Implement the getMin(arr) function, which takes an array of numbers arr and returns the smallest number of the array. To solve the problem, you must use one of the methods to specify the context of this. It is forbidden to use any cycles.

Code:

```js
function getMin(arr) {
  return Math.min.apply(this, arr);
}
```

# Task 5

We have the product() function, you can see it on the snapshot below. This product() function finds the product of its arguments and also uses this object for the initial value of the product.

Please, create a new function getProduct() that, no matter how it is called, will be always bound to a particular this value. getProduct() should be created from the original product() function and work with the same logic, but should pass two additional arguments – 2 and 3 – to the original function, every time getProduct() is called.

Object this for getProduct() function you should also define by yourself. Look at snapshot for clues what it should be.

<img src="./SPRINT 4. Object-oriented design (OOD)  Object-oriented programming (OOP)/images/example.png">

Code:

```js
const product = function () {
  return [].reduce.call(
    arguments,
    function (res, elem) {
      return res * elem;
    },
    this.product
  );
};

const contextObj = {
  product: 10,
};

const getProduct = product.bind(contextObj, 2, 3);
```

# Task 6

Implement the Plane class, the constructor of which accepts 3 parameters model - model of the plane, fuelSupply - capacity of a stock of fuel of the plane, fuelConsumption - average fuel consumption in liters on 100 km of flight.

Create a method of class calcFlightRange(), which determines the range of the plane by the formula fuelSupply / fuelConsumption \* 100 and returns it.

Create a static method of class sortFlightRange(planesArray), which takes an array of instances of class planesArray, sorts the flight range of plane in ascending order and outputs the result to the console in the format plane_model: range.

Create a TransportPlane class, which is inherited from the Plane class, the constructor of which takes 5 parameters model - plane model, fuelSupply - the amount of fuel, fuelConsumption - the average fuel consumption in liters per 100 km, cargo - maximum tonnage, addTank - about additional tanks of the plane In this class, you need to override the calcFlightRange() method to take into account that the fuelSupply has increased the amount of fuel added by the addTank.

Create a class PassengerPlane, which is inherited from the class Plane, whose constructor accepts 5 parameters model, fuelSupply, fuelConsumption, passengers - the maximum number of passengers, refueling - the amount of additional fuel received in the refueling. In this class, you need to override the calcFlightRange() method to take into account that the fuelSupply has increased refueling.

Create a WarPlane class, which is inherited from the Plane class, the constructor of which accepts 5 parameters model, fuelSupply, fuelConsumption, missiles - the number of missile weapons, aerodynamicsKoef - the coefficient of aerodynamics of the plane. In this class, you need to override the calcFlightRange() method in such a way as to take into account that the flight range of the plane increases in proportion to the value of the aerodynamics coefficient of aerodynamicsKoef.

Usage example:

```js
console.log("Unsorted range of planes:");

const plane1 = new TransportPlane("An-225 Mriya", 105000, 5000, 500, 300000);

console.log("An-225 Mriya: ", plane1.calcFlightRange());

const plane2 = new PassengerPlane("Boeing-747", 193000, 2500, 410, 90000);

console.log("Boeing-747:", plane2.calcFlightRange());

const plane3 = new WarPlane("F-22 Raptor", 8200, 320, 20, 1.2);

console.log("F-22 Raptor:", plane3.calcFlightRange());

console.log("Sorted range of planes:");

const planesArray = [plane1, plane2, plane3];

Plane.sortFlightRange(planesArray);
```

Output in console:

```
Unsorted range of planes:

An-225 Mriya:  8100

Boeing-747:  11320

F-22 Raptor:  3075

Sorted range of planes:

F-22 Raptor: 3075

An-225 Mriya: 8100

Boeing-747: 11320
```

Code:

```js
class Plane {
  constructor(model, fuelSupply, fuelConsumption) {
    this.model = model;
    this.fuelSupply = fuelSupply;
    this.fuelConsumption = fuelConsumption;
  }
  calcFlightRange() {
    return (this.fuelSupply / this.fuelConsumption) * 100;
  }
  static sortFlightRange(planesArray) {
    planesArray.sort((a, b) => a.calcFlightRange() - b.calcFlightRange());
    planesArray.forEach((el) => {
      console.log(`${el.model}: ${el.calcFlightRange()}`);
    });
  }
}

class TransportPlane extends Plane {
  constructor(model, fuelSupply, fuelConsumption, cargo, addTank) {
    super(model, fuelSupply, fuelConsumption);
    this.cargo = cargo;
    this.addTank = addTank;

    this.fuelSupply += this.addTank;
  }
  calcFlightRange() {
    return super.calcFlightRange();
  }
}

class PassengerPlane extends Plane {
  constructor(model, fuelSupply, fuelConsumption, passengers, refueling) {
    super(model, fuelSupply, fuelConsumption);
    this.passengers = passengers;
    this.refueling = refueling;

    this.fuelSupply += this.refueling;
  }
  calcFlightRange() {
    return super.calcFlightRange();
  }
}

class WarPlane extends Plane {
  constructor(model, fuelSupply, fuelConsumption, missiles, aerodynamicsKoef) {
    super(model, fuelSupply, fuelConsumption);
    this.missiles = missiles;
    this.aerodynamicsKoef = aerodynamicsKoef;

    this.fuelSupply *= this.aerodynamicsKoef;
  }
  calcFlightRange() {
    return super.calcFlightRange();
  }
}
```

# Task 7

Implement the PizzaMaker class, which allows you to create pizza of different types, with different ingredients, calculate the price and calorie content of pizza.

The pizza comes in 3 sizes: S, M and L.

There are 4 types of pizza available: meat, fish, cheese and vegetarian.

When creating a new pizza, be sure to specify the size and appearance.

Additional ingredients are available that can be added to the pizza at the customer's request: tomatoes, peppers, bacon and olives.

Each element that makes up pizza has its own name, price and calorie content. All of this data is contained in the pizzaMenu object.

The PizzaMaker class has a number of methods for generating pizza:

- addIngredient(ingredient) method adds an additional ingredient to the pizza. A new ingredient is added if it is not included in the pizza, and the message "ingredient_name has been added" is displayed in the console. If such an ingredient has already been added, the message "Such an ingredient already exists!" Is generated.

- deleteIngredient(ingredient) method removes the specified ingredient from the list of existing ingredients, displays the message "ingredient_name has been deleted" to the console.

- getIngredients() method returns a list of the attached ingredients with their name, price, calorie content.

- getSize() method returns the size of the pizza.

- getKind() method returns the type of pizza.

- calculatePrice() method calculates and returns the total cost of a pizza, which consists of the sum of the values ​​of all its components.

- calculateCalories() method calculates and returns the total calorie content of a pizza, which consists of the sum of the calories of all its components.

Usage example:

```js
const pizzaMenu = {
  SIZE_S: { param: "SIZE_S", price: 60, calorie: 300 },
  SIZE_M: { param: "SIZE_M", price: 90, calorie: 450 },
  SIZE_L: { param: "SIZE_L", price: 110, calorie: 600 },
  KIND_MEAT: { param: "KIND_MEAT", price: 55, calorie: 230 },
  KIND_FISH: { param: "KIND_FISH", price: 70, calorie: 150 },
  KIND_CHEESE: { param: "KIND_CHEESE", price: 50, calorie: 200 },
  KIND_VEGETARIAN: { param: "KIND_VEGETARIAN", price: 35, calorie: 50 },
  INGREDIENT_TOMATOES: { param: "INGREDIENT_TOMATOES", price: 15, calorie: 5 },
  INGREDIENT_PEPPER: { param: "INGREDIENT_PEPPER", price: 18, calorie: 5 },
  INGREDIENT_BACON: { param: "INGREDIENT_BACON", price: 25, calorie: 40 },
  INGREDIENT_OLIVES: { param: "INGREDIENT_OLIVES", price: 20, calorie: 0 },
};

// your PizzaMaker class implementation

const pizza = new PizzaMaker(pizzaMenu.SIZE_M, pizzaMenu.KIND_MEAT);

console.log("Size:", pizza.getSize());

console.log("Kind:", pizza.getKind());

console.log("calculatePrice:", pizza.calculatePrice());

console.log("calculateCalories:", pizza.calculateCalories());

console.log("getIngredients:", pizza.getIngredients());

pizza.addIngredient(pizzaMenu.INGREDIENT_TOMATOES);

pizza.addIngredient(pizzaMenu.INGREDIENT_BACON);

console.log("getIngredients:", pizza.getIngredients());

pizza.deleteIngredient(pizzaMenu.INGREDIENT_TOMATOES);

console.log("getIngredients:", pizza.getIngredients());

console.log("calculatePrice:", pizza.calculatePrice());

console.log("calculateCalories:", pizza.calculateCalories());
```

Output in console:

```
Size: SIZE_M

Kind: KIND_MEAT

calculatePrice: 145

calculateCalories: 680

getIngredients: []

INGREDIENT_TOMATOES has been added

INGREDIENT_BACON has been added

getIngredients: [

  { param: 'INGREDIENT_TOMATOES', price: 15, calorie: 5 },

  { param: 'INGREDIENT_BACON', price: 25, calorie: 40 }

]

INGREDIENT_TOMATOES has been deleted

getIngredients: [ { param: 'INGREDIENT_BACON', price: 25, calorie: 40 } ]

calculatePrice: 170

calculateCalories: 720
```

Code:

```js
const pizzaMenu = {
  SIZE_S: { param: "SIZE_S", price: 60, calorie: 300 },
  SIZE_M: { param: "SIZE_M", price: 90, calorie: 450 },
  SIZE_L: { param: "SIZE_L", price: 110, calorie: 600 },
  KIND_MEAT: { param: "KIND_MEAT", price: 55, calorie: 230 },
  KIND_FISH: { param: "KIND_FISH", price: 70, calorie: 150 },
  KIND_CHEESE: { param: "KIND_CHEESE", price: 50, calorie: 200 },
  KIND_VEGETARIAN: { param: "KIND_VEGETARIAN", price: 35, calorie: 50 },
  INGREDIENT_TOMATOES: { param: "INGREDIENT_TOMATOES", price: 15, calorie: 5 },
  INGREDIENT_PEPPER: { param: "INGREDIENT_PEPPER", price: 18, calorie: 5 },
  INGREDIENT_BACON: { param: "INGREDIENT_BACON", price: 25, calorie: 40 },
  INGREDIENT_OLIVES: { param: "INGREDIENT_OLIVES", price: 20, calorie: 0 },
};
class PizzaMaker {
  constructor(size, appearance) {
    this.size = size;
    this.appearance = appearance;
    this.ingredients = [];
  }
  addIngredient(ingredient) {
    if (this.ingredients.includes(ingredient))
      console.log("Such an ingredient already exists!");
    else {
      this.ingredients.push(ingredient);
      console.log(`${ingredient.param} has been added`);
    }
  }
  deleteIngredient(ingredient) {
    if (this.ingredients.includes(ingredient)) {
      this.ingredients = this.ingredients.filter((f) => f != ingredient);
      console.log(`${ingredient.param} has been deleted`);
    }
  }
  getIngredients() {
    return this.ingredients;
  }
  getSize() {
    return this.size.param;
  }
  getKind() {
    return this.appearance.param;
  }
  calculatePrice() {
    return (
      this.size.price +
      this.appearance.price +
      this.ingredients.reduce((acc, item) => acc + item.price, 0)
    );
  }
  calculateCalories() {
    return (
      this.size.calorie +
      this.appearance.calorie +
      this.ingredients.reduce((acc, item) => acc + item.calorie, 0)
    );
  }
}
```

## _SPRINT 6. Asynchronous JS, Closures, Exceptions_

# Task 1

Implement the getPromise(delay, message) function, which takes an integer number delay (between 0 and 2000) and string message and returns a Promise that waits for specified amount of time (using delay argument) and resolves with the message.

Code:

```js
function getPromise(delay, message) {
  return new Promise((resolve) => {
    return setTimeout(() => resolve(message), delay);
  });
}
```

# Task 2

Write an add(x, y) function that takes two arguments x and y. The function should return a Promise that resolves with the sum of the two arguments if they are Numbers, or rejects with the message "Error!" otherwise.

Code:

```js
function add(x, y) {
  return new Promise((resolve, reject) => {
    if (isNaN(+x) || isNaN(+y)) return reject("Error!");
    return resolve(x + y);
  });
}
```

# Task 3

Implement the getAge() function to get user age. To find his age you need to call a getUser() async function that returns a user object in format {role: "somerole", id: 1}.

To get the actual user info you need to call another async function getUserProfile(id), which uses id returned from the previous function and returns user info as an object

```js
{name: "Petro", age: 15}. //The getAge() must return the age of the user.
```

Code:

```js
const { getUser, getUserProfile } = require("./Helper.js");

async function getAge() {
  const { id } = await getUser();
  const { age } = await getUserProfile(id);
  return age;
}
```

# Task 4

Implement the take() function that converts a sequence of iterated values into a sequence of length n.

Example usage:

```js
const arr = ["a", "b", "c", "d"];
for (const x of take(2, arr)) {
  console.log(x);
}
// Output:
// a
// b
```

Code:

```js
function* take(n, iterable) {
  for (let i = 0; i < n; i++) yield iterable[i];
}
```

# Task 5

Please, implement a function accountPatients that takes a count of free beds in a hospital and returns two functions:

the first one for adding a patient

the second one for discharging a patient

accountPatients should keep track of free beds in a hospital and every time when a patient is admitted or discharged, print the count to the console like in examples:

A patient was discharged, 54 beds are available

A patient was admitted, 34 beds are available

When there are no beds available,

Can not admit a patient, no beds available should be printed

When there is an attempt to discharge a patient when there are no patients,

There are no patients to discharge should be printed

Code:

```js
const accountPatients = (countOfFreeBeds) => {
  let count = countOfFreeBeds;
  function admit() {
    if (count <= 0) {
      console.log(`Can not admit a patient, no beds available`);
      return;
    }
    count--;
    console.log(`A patient was admitted, ${count} beds are available`);
  }
  function discharge() {
    count++;
    if (count > countOfFreeBeds) {
      console.log(`There are no patients to discharge`);
      return;
    }
    console.log(`A patient was discharged, ${count} beds are available`);
  }
  return [admit, discharge];
};
```

# Task 6

Write a checkAdult(age) function whose input parameter is the age of the user age. The function checks whether the set age parameter is set correctly, if it is set incorrectly, the corresponding error should be generated and displayed in the console:

- if the age value has not been set, you need to create the following error: "Please, enter your age",

- If you set a negative age value, you need to create the following error: "Please, enter positive number",

- if a non-numeric value of age was specified, you need to create the following error: "Please, enter number",

- if the integer value of age was not specified, you need to create the following error: "Please, enter Integer number",

- If the user is under 18, you need to create the following error: "Access denied - you are too young!".

If there is no error, the message “Access allowed” is displayed in the console.

In the function, implement the handling of possible exceptions, providing the output to the console of the name and description of the error.

Regardless of whether the age parameter was set correctly or incorrectly, the message “Age verification complete” should be displayed at the end of the test.

Function usage example:

```js
checkAdult(15); // Error Access denied - you are too young!

// Age verification complete

checkAdult(25); // Access allowed

// Age verification complete
```

Code:

```js
function checkAdult(age) {
  if (!age) {
    console.log(`Error Please, enter your age`);
  } else if (age < 0) {
    console.log(`Error Please, enter positive number`);
  } else if (isNaN(+age)) {
    console.log(`Error Please, enter number`);
  } else if (age != Math.floor(age)) {
    console.log(`Error Please, enter Integer number`);
  } else if (age < 18) {
    console.log(`Error Access denied - you are too young!`);
  } else console.log(`Access allowed`);
  console.log(`Age verification complete`);
}
```

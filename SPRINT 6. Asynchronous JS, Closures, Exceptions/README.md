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

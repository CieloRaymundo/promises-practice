# Unit 6 Lesson 1 Practice: Promises

## Directions
Fork and clone this lab. Respond to questions in clear, concise sentences directly within this markdown file.

**1. What will the following code snippet log? Why?**
  ```javascript
  console.log('Line 1')
  setTimeout(() => console.log('Line 2'), 1000)
  console.log('Line 3')
  ```
This will log 'Line 1', then 'Line 3' and finally 'Line 2' because line 2 has a set timeout that will make it wait for 1 second until it actually logs 'Line 2' to the console

**2. What does the following code snippet log? Why?**
  ```javascript
  function createPromise(seconds) {
    return new Promise((resolve) => {
      setTimeout(function() {
        resolve(`After ${seconds} second(s), this promise is resolved.`)
      }, seconds * 1000)
    })
  }

  console.log(createPromise(1000))
  ```
This will log 'After 1000 second(s), this promise is resolved.', because it takes in the amount of seconds as an argument.

**3. How do we use our `createPromise` function to log `"After 1 second(s), this promise is resolved."`**
In order for us to log the string then when we create a new promise we use the ".then" method to get the value and log that value to the c onsole. 

Ex:
 const a = createPromise(3);
 a.then(value => console.log(value))

**4. What does the following code snippet return? What does it log?**
  ```javascript
  const ourPromise = new Promise((resolve) => {
    resolve(12);
  })

  ourPromise.then(value => value * 2);
  ```
This returns 24 and logs the resolved promise with value of 24

**5. What does the following code snippet return? What does it log?** <br> _**Note:** Instead of using the `Promise` constructor to create a Promise that immediately resolves to 12, we can just use the [`Promise.resolve`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/resolve) method._
  ```javascript
  const ourPromise = Promise.resolve(12);
  ourPromise.then(value => value * 2).then(value => value + 10);
  ```
This returns 34 and logs the resolved promise with its value of 34. 

**6. What does the following code snippet return? What does it log? How does this differ from the question above?**
  ```javascript
  Promise.resolve(12).then(value => value * 2).then(value => console.log(value + 10))
  ```
This returns the resolved promise with no value and logs 34. This differs from the question above because everything is being done on one line, and it has no value because nothing is being returned while in the previous question the value is being returned.

**7. What does the following code snippet return? What does it log? How does this differ from the question above?**
  ```javascript
  Promise.resolve(12).then(value => value * 2).then(value => {
    console.log(value + 10);
    return value + 10;
    });
  ```
This code snippet will return the promise as resolved and the value of 34, and will also log 34. This is different from the question above because this explicitly returns the value + 10 as the final step, and also logs it.

**8. What does the following code snippet return? What does it log? How does this differ from the question above?**
  ```javascript
  Promise.reject(12).then(value => value * 2).then(value => {
    console.log(value + 10);
    return value + 10;
    }).catch(reason => {
      const message = `${reason} is a bad number.`;
      console.error(message);
      return reason;
    });
  ```
This code snippet will return 12, and logs '12 is a bad number'. This differs from the question above because it will never be resolved since the promise is built to reject the number 12. So then it will default into goint to the catch method and executoing it's inner function. Once that rejected execution function is complete it will default the promise to say "resolved".

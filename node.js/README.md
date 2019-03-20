# Node.js

{% embed url="https://www.onlineinterviewquestions.com/node-js-interview-questions/" %}

* What is “callback hell” and how can it be avoided?
* How does Node.js handle child threads?
  * Node.js, in its essence, is a **single thread** process. It does not expose child threads and thread management methods to the developer. Technically, Node.js _does_ spawn child threads for certain tasks such as asynchronous I/O, but these run behind the scenes and do not execute any application JavaScript code, nor block the main event loop.

    If threading support is desired in a Node.js application, there are tools available to enable it, such as the [ChildProcess](http://nodejs.org/api/child_process.html) module.
* What is the preferred method of resolving unhandled exceptions in Node.js?
  * Unhandled exceptions in Node.js can be caught at the `Process` level by attaching a handler for `uncaughtException` event.

    ```javascript
    process.on('uncaughtException', function(err) {
      console.log('Caught exception: ' + err);
    });
    ```

    However, `uncaughtException` is a very crude mechanism for exception handling and may be removed from Node.js in the future. An exception that has bubbled all the way up to the `Process` level means that your application, and Node.js may be in an undefined state, and the only sensible approach would be to restart everything.

    The preferred way is to add another layer between your application and the Node.js process which is called the [domain](http://nodejs.org/api/domain.html).

    Domains provide a way to handle multiple different I/O operations as a single group. So, by having your application, or part of it, running in a separate domain, you can safely handle exceptions at the domain level, before they reach the `Process` level.
* What is typically the first argument passed to a Node.js callback handler?
* **Provide some example of config file separation for dev and prod environments**
* **process.nextTick** - used to schedule a callback function to be invoked in the next iteration of the Event Loop
* **What is the difference between process.nextTick\(\) and setImmediate\(\) ?**
  * The difference between `process.nextTick()` and `setImmediate()` is that `process.nextTick()` defers the execution of an action till the next pass around the event loop or it simply calls the callback function once the ongoing execution of the event loop is finished whereas `setImmediate()` executes a callback on the next cycle of the event loop and it gives back to the event loop for executing any I/O operations.
* **How can you avoid callback hells?**
* **Provide some example of config file separation for dev and prod environments**
* **Explain what is Reactor Pattern in Node.js?**
* **Why should you separate Express 'app' and 'server'?**

![](../.gitbook/assets/image%20%2831%29.png)


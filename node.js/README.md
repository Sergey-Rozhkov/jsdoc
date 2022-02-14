# Node.js

* List down the major benefits of using Node.js?
  * Fast Node.js is built on Google Chrome’s V8 JavaScript Engine which makes its library very fast in code execution
  * Asynchronous Node.js based server never waits for an API to return data thus making it asynchronous
  * Scalable It is highly scalable because of its event mechanism which helps the server to respond in a non-blocking way
  * Open Source Node.js has an extensive open source community which has contributed in producing some excellent modules to add additional capabilities to Node.js applications
  * No Buffering Node.js applications simply output the data in chunks and never buffer any data
* How many types of API functions are there in Node.js?
  * Asynchronous, non-blocking functions
  * Synchronous, blocking functions
* Что такое `callback hell` и как его избежать?
* Differentiate between `process.nextTick()` and `setImmediate()` ?
  * In Node.js, process.nextTick() and setImmediate(), both are functions of the Timers module which help in executing the code after a predefined period of time. But these functions differ in their execution. The process.nextTick function waits for the execution of action till the next pass around in the event loop or once the event loop is completed only then it will invoke the callback function. On the other hand, setImmediate() is used to execute a callback method on the next cycle of the event loop which eventually returns it to the event loop in order to execute the I/O operations.
* Explain stream in Node.js along with its various types.
  *   Streams in Node.js are the collection of data similar to arrays and strings. They are objects using which you can read data from a source or write data to a destination in a continuous manner. It might not be available at once and need not to have fit in the memory. These streams are especially useful for reading and processing a large set of data. In Node.js, there are four fundamental types of streams:

      ```
      Readable: Used for reading large chunks of data from the source.
      Writeable: Use for writing large chunks of data to the destination.
      Duplex: Used for both the functions; read and write.
      Transform: It is a duplex stream that is used for modifying the data.
      ```
* Is Node a single threaded application?
  * > Yes. Node is a single-threaded application with event looping.
* How does Node.js handle child threads?&#x20;
  * > Node.js, in its essence, is a **single thread** process. It does not expose child threads and thread management methods to the developer. Technically, Node.js _does_ spawn child threads for certain tasks such as asynchronous I/O, but these run behind the scenes and do not execute any application JavaScript code, nor block the main event loop.\
    > If threading support is desired in a Node.js application, there are tools available to enable it, such as the [ChildProcess](http://nodejs.org/api/child\_process.html) module.
* What is the preferred method of resolving unhandled exceptions in Node.js?
  *   > Unhandled exceptions in Node.js can be caught at the `Process` level by attaching a handler for `uncaughtException` event.

      ```javascript
      process.on('uncaughtException', function(err) {
        console.log('Caught exception: ' + err);
      });
      ```

      > However, `uncaughtException` is a very crude mechanism for exception handling and may be removed from Node.js in the future. An exception that has bubbled all the way up to the `Process` level means that your application, and Node.js may be in an undefined state, and the only sensible approach would be to restart everything.

      > The preferred way is to add another layer between your application and the Node.js process which is called the [domain](http://nodejs.org/api/domain.html).

      > Domains provide a way to handle multiple different I/O operations as a single group. So, by having your application, or part of it, running in a separate domain, you can safely handle exceptions at the domain level, before they reach the `Process` level.
* What is typically the first argument passed to a Node.js callback handler?
* **Provide some example of config file separation for dev and prod environments**
* **process.nextTick** - used to schedule a callback function to be invoked in the next iteration of the Event Loop
* **What is the difference between process.nextTick() and setImmediate() ?**
  * The difference between `process.nextTick()` and `setImmediate()` is that `process.nextTick()` defers the execution of an action till the next pass around the event loop or it simply calls the callback function once the ongoing execution of the event loop is finished whereas `setImmediate()` executes a callback on the next cycle of the event loop and it gives back to the event loop for executing any I/O operations.
* **Provide some example of config file separation for dev and prod environments**
* **Explain what is Reactor Pattern in Node.js?**
* **Why should you separate Express 'app' and 'server'?**

![](<../.gitbook/assets/image (31).png>)

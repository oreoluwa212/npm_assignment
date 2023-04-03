================ QUESTION 1 =================
What is the Event loop ?
The event loop allows Node. js to perform non-blocking I/O operations despite the fact that JavaScript is single-threaded. It is done by assigning operations to the operating system whenever and wherever possible. The event loop is the secret behind JavaScript's asynchronous programming. The event loop is the secret behind JavaScript’s asynchronous programming. JS executes all operations on a single thread, but using a few smart data structures, it gives us the illusion of multi-threading. It constantly checks whether or not the call stack is empty. If it is empty, new functions are added from the event queue. If it is not, then the current function call is processed.

================ QUESTION 2 =================
Explain the 6 phases of the event loop
The Event Loop contains six main phases: timers, I/O callbacks, preparation / idle phase, I/O polling, setImmediate() callbacks execution, and close events callbacks.

_PHASE 1: TIMERS_
In Node.js timers, or functions that execute callbacks after a set period of time, are provided by the core timers module. This module provides two global functions: setTimeout(), and setInterval(). These allow you to define code to execute after a period of time.

Both functions take a callback function, and delay in milliseconds, as their arguments. Additional arguments can optionally be passed after the delay -- those arguments will be passed to the callback function.
The timers phase is executed directly by the Event Loop. At the beginning of this phase the Event Loop updates its own time. Then it checks a queue, or pool, of timers. This queue consists of all timers that are currently set. The Event Loop takes the timer with the shortest wait time and compares it with the Event Loop's current time. If the wait time has elapsed, then the timer's callback is queued to be called once the call stack is empty.

_Phase 2: I/O callbacks_
This is a phase of non-blocking input/output. Basically, when your application is waiting for a file to be read, it doesn't have to necessarily wait until the system gets back to it with the content of the file. It can continue code execution and receive the file's content asynchronously when it is ready.
This is what non-blocking I/O interfaces allow us to do. The asynchronous I/O request is recorded into the queue and then the main call stack can continue working as expected. In the second phase of the Event Loop the I/O callbacks of completed or errored out I/O operations are processed.

_Phase 3: idle / waiting / preparation_
This is a housekeeping phase. During this phase the Event Loop performs internal operations of any callbacks. Technically speaking, there is no possible direct influence on this phase, or its length. No mechanism is present that could guarantee code execution during this phase. It is primarily used for gathering information, and planning of what needs to be executed during the next tick of the Event Loop.

_Phase 4: I/O polling (poll phase)_
This is the phase in which all the JavaScript code that we write is executed, starting at the beginning of the file, and working down. Depending on the code it may execute immediately, or it may add something to the queue to be executed during a future tick of the Event Loop.
During this phase the Event Loop is managing the I/O workload, calling the functions in the queue until the queue is empty, and calculating how long it should wait until moving to the next phase. All callbacks in this phase are called synchronously in the order that they were added to the queue, from oldest to newest. This is the phase that can potentially block our application if any of these callbacks are slow and not executed asynchronously.
If there are any setImmediate() timers scheduled, Node.js will skip this phase during the current tick and move to the setImmediate() phase. If there are no functions in the queue, and no timers, the application will wait for callbacks to be added to the queue and execute them immediately, until the internal setTimeout() that is set at the beginning of this phase is up. At that point, it moves on to the next phase. The value of the delay in this timeout also depends on the state of the application.

_Phase 5: setImmediate() callbacks_
Node.js has a special timer, setImmediate(), and its callbacks are executed during this phase. This phase runs as soon as the poll phase becomes idle. If setImmediate() is scheduled within the I/O cycle it will always be executed before other timers regardless of how many timers are present.

_Phase 6: close events_
This phase executes the callbacks of all close events. For example, a close event of web socket callback, or when process.exit() is called. This is when the Event Loop is wrapping up one cycle and is ready to move to the next one. It is primarily used to clean the state of the application.

================ QUESTION 3 =================
List some best practices in server-side code development
Keeping Code small and easy to read.
Avoid Null or Undefined variables
Handling Errors.
Using Async/Await syntax to make the code more readable and maintainable.
Correctly use asynchronous methods on the server when a transaction is waiting for a response
Focusing on the quality of the code.
Manage Large arrays or objects.
Avoid Spawning too much work, too quickly


================ QUESTION 4 =================
What is NPM5: How do you initialize a package in npm?
Npm is the world's largest Software Registry. The registry contains over 800,000 code packages. Open-source developers use npm to share software. Many organizations also use npm to share and borrow packages. Npm allows you to install various packages and manage their dependencies. To initialize a package in NPM use the " npm init" command.


================ QUESTION 5 =================
How do you run a script in the package.json ?
   To run a script in package.json file, use the "npm run argument" command with the name of the script as the argument .e.g npm run prettier.

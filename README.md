1. what is event loop
In computer science, the event loop is a programming construct or design pattern that waits for and dispatches events or messages in a program. The event loop works by making a request to some internal or external "event provider", then calls the relevant event handler. Wikipedia
the node js through event listeners receives events, stacks them up, takes these one at a time events to appropriate processing component where it wiil be worked on and returned as processed to the frontend/client. the circle from the point of receiving the events, processing it and returning it after being processed is what is called event loop.

2. the 6 stages of event loop:
-Timers 
-I/O Callbacks 
-Waiting / Preparation 
-I/O Polling 
-setImmediate() callbacks 
-Close events
-Timers
The core timers module in Node.js provides timers, or functions that perform callbacks after a given amount of time. setTimeout() and setInterval() are two global functions provided by this module (). These let you to define code that will run once a certain amount of time has passed. 

The Event Loop executes the timers phase directly. The Event Loop changes its own time at the start of this phase. The timers are then checked in a queue or pool. All timers that are currently set are in this queue. The Event Loop compares the timer with the least wait time to the current time of the Event Loop. The timer's callback is scheduled to be triggered once the call stack is empty if the wait time has expired. 

There are two types of timers in Node.js: setTimeout() and setInterval() (). The main difference is that setInterval() has a repeat flag, which returns the timer to the queue once it has completed its execution. 

I/O Callbacks
I/O refers to reading/writing files or network operations in Node.js. Network operations allow you to bring in external data or send data from your program to another location. We'll use the file system as an example, although you could instead use network activities to examine these instances. 

When your program is waiting for a file to be read, it is not required to wait until the system returns with the file's content. It can keep running code and asynchronously receive the file's content when it's ready. 

Non-blocking, I/O interfaces enable us to do this. The asynchronous I/O request is queued, and the main call stack can then continue to function normally. The I/O callbacks of completed or errored out I/O operations are processed in the second phase of the Event Loop. 

Idle, Prepare
The Event Loop executes internal activities on any callbacks during this phase. Technically, there is no way to change the length or nature of this phase. During this phase, there is no mechanism in place to guarantee code execution. It is mostly used for gathering data and preparing what actions should be taken on the next tick of the Event Loop. 

Poll
This is the stage wherein the launch all of the JavaScript code we've created from top to bottom. Relying on the code, it could run immediately or add anything to the list to be handled on a subsequent iteration of the Event Loop. 

The Event Loop manages the I/O workload during this phase, calling the functions in the queue until the queue is empty, and calculates how long it should wait before going on to the next phase. In this phase, all callbacks are synchronously called in the order in which they were added to the queue, from oldest to newest. 

If any setImmediate() timers are scheduled during the current tick, Node.js will skip this phase and proceed to the setImmediate() phase.

If there are no timers or functions in the queue, the program will wait for callbacks to be added to the queue and then execute them until the internal setTimeout() that was set at the start of this phase expires. It continues on to the next step after that. The duration of this timeout is likewise determined by the status of the application. 

Check
The callbacks scheduled by setImmediate() are handled in this phase, and they will be executed once the Poll phase is idle. 

SetImmediate() in Node.js is a specific timer that executes callbacks during this period. When the poll phase is idle, this phase starts. SetImmediate() will always be executed before other timers if it is scheduled within the I/O cycle, regardless of how many timers are present. 

Close Callback
If a socket or handle is abruptly closed, the 'close' event is emitted, this phase handles callbacks. 

All closing event callbacks are executed in this phase. A closing event of a web socket callback, for example, or process.exit() is called. This is the point at which the Event Loop has completed one cycle and is ready to go on to the next. It is primarily used to clear the application's state. 


3. best practices in server-side code development
    a. Code quality
    b. Prefer ES6+ 
    c. keep code small
    d. handle errors
    e. Use code linters, formatters & style guides for Clean Code Practices & Easy Readability
    f. Always use naming conventions for variables, constants, functions, and classes
    g. Use Configuration files and Environment Variables
    h. Write Asynchronous Code, Use promises and async/await
    i. Follow Folder structure – Properly organize your code files
    j. Use efficient tools to restart your app
    k. Get acquainted with JavaScript Best Practices
    l. Create all your projects with npm init
    m. Test your Code
    n. Third-Party Solutions
    o. Keep your application stateless
 
4. I initialize NPM5 by typing npm init in the terminal. This will pop up some series of question which will be answered, and in the end i will run yes. However, there is a short form of doing it. you just run npm init -y

5. we run a script in the package.jason by typing-npm run <script-name>


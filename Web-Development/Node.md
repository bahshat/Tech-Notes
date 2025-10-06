@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@


Node is written in C++
Node is a C++ program
V8 is JS engine
V8 is written in C++
V8 converts JS to Machine Code
V8 can be embedded in  another C++ program
using which we can extend normal JS as well
C++ is closer to machine
That is why Node which works on top of V8
Node JS is a C++ program, with V8 Embedded, that adds wealth of great features that make a suitable server technology


We extend V8 so that we can make C++ things available to JS (C++ functions invoked through JS)
Node Js is not JS but allows JS to have the feature more than it actually have

+++++++++++++++++++++++++
Why React other PWA need Node then?

React applications leverage Node.js for essential development and build processes, including:
Package Management:
Node.js provides npm (Node Package Manager), which is crucial for installing and managing React libraries, dependencies, and development tools.
Build Tools:
Tools like Webpack and Babel, used for compiling, bundling, and transpiling React code for browser compatibility, run on Node.js.
Development Server:
Node.js powers the local development server that serves the React application during development, enabling features like hot reloading.
++++++++++++++++++++++++++++++++++++++


Server: A computer performing services 

Web Server: Serves web request

HTTP req-res 
++++++++++++++++++++++++++++++++++++++
 When we run node in interactive mode and open it command line
we actually pass js 

>1+1
2

this JS is passed to Node 
Node passed it to V8 engine as well as to the extension added around V8 engine and we get our code back we have executed

Similar;y we can make node work on a whole file with JS

> node app.js 

also you can provide multiple files but you need to provide single entry point to node.

+++++++++++++++++++++++++++
A Module: A reusable block of code whose existence does not accidently imapact othr code
module.export = greet


Expression : A bock of code resul that result in value

++++++++++++++++++++

Object is key/valus
primitive values
another objects
functions
+++++++++++++++++
Cutome Event
JS Core
Event Emitter
+++++

npm -i -g nodemon (monitor) for hot reloading

+++++++++++++++++

URL param using req.params
? mark param using req.query

Post:  req.body.name_of_param
+++++++++++++++++

JOI package

+++++++++++

if nodemon app.js does work
npx nodemon app.js


+++++++++++++
Node project created from scratch
> yarn init
> yarn add express

Express is lightweight fw

====================================================================

file:///C:/Users/rais.shaikh/Desktop/R&D%20Backend/src/app.js:1
require('dotenv').config();
^

ReferenceError: require is not defined in ES module scope, you can use import instead
This file is being treated as an ES module because it has a '.js' file extension and 'C:\Users\rais.shaikh\Desktop\R&D Backend\package.json' contains "type": "module". To treat it as a CommonJS script, rename it to use the '.cjs' file extension.
    at file:///C:/Users/rais.shaikh/Desktop/R&D%20Backend/src/app.js:1:1
    at ModuleJob.run (node:internal/modules/esm/module_job:329:25)
    at async onImport.tracePromise.__proto__ (node:internal/modules/esm/loader:644:26)
    at async asyncRunEntryPointWithESMLoader (node:internal/modules/run_main:117:5)

Node.js v22.17.0



====================================================================

Module: Just a fancy word for a single code file (.js file) that encapsulates related code.

CommonJS (CJS) Module System:
 * What it was: Node.js's original way to organize code.
 * How it worked:
   * Export: module.exports = ... or exports.myVar = ...
   * Import: const myModule = require('./myModule');
 * Loading: Synchronous (code waits for the module to load).
 * .cjs?: A file extension (.cjs) explicitly tells Node.js to treat the file as a CommonJS module, overriding other configurations.

ES Modules (ESM) / ES:
 * What it is: The official, standardized JavaScript module system (from ECMAScript 2015/ES6).
 * How it works:
   * Export: export const myVar = ...; or export default ...;
   * Import: import { myVar } from './myModule'; or import myDefault from './myModule';
 * Loading: Asynchronous (non-blocking).
 * Node.js support: Modern Node.js supports it. 

CommonJS to ES => either use .mjs extension or add "type": "module" to your package.json.

=====================================================================

The code require('dotenv').config() is used in Node.js applications to load environment variables from a .env file. dotenv is a module that reads the contents of a .env file and assigns those variables to process.env, making them accessible throughout the application. The require('dotenv') part imports the dotenv module, and .config() loads the environment variables. 
Here's a more detailed explanation:
1. require('dotenv'):
This line imports the dotenv module, which is a package that provides a way to manage environment variables in your Node.js application. 
2. .config():
This is a method provided by the dotenv module. It reads the contents of a .env file (usually located in the root of your project) and loads the key-value pairs defined in that file into process.env. 
3. .env file:
This file contains environment-specific variables, such as API keys, database URLs, or port numbers, that you don't want to hardcode directly into your application's source code. 
4. process.env:
This is a global object in Node.js that stores environment variables. By using dotenv.config(), you populate this object with the variables defined in your .env file. 
Example:
Install dotenv: npm install dotenv.
Create a .env file: 


Code
   PORT=3000
   API_KEY=your_secret_api_key
In your Node.js file:


JavaScript
   require('dotenv').config();
   const port = process.env.PORT;
   const apiKey = process.env.API_KEY
   console.log(`Port: ${port}`);
   console.log(`API Key: ${apiKey}`);
In this example, the PORT and API_KEY variables from the .env file will be accessible in your application through process.env.PORT and process.env.API_KEY. 



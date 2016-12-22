:warning: This is the client-side app for a two part NodeJS application
> [Voting-client-screencast][votingClientLink]

# TUTORIAL NOTES

> View the [screencast][screencastLink] for this tutorial.
> Visit my web development blog [web development blog][bloglink].

# 18/Nov/2016

- Actions:
  Actions are payloads of information that send data from your application to your store. They are the only source of information for the store. You send them to the store using store.dispatch().

  Actions are plain JavaScript objects. Actions must have a type property that indicates the type of action being performed. Types should typically be defined as string constants. Once your app is large enough, you may want to move them into a separate module.

  > ref: http://devdocs.io/redux/basics/actions

- Reducers:
  Actions describe the fact that something happened, but don't specify how the application's state changes in response. This is the job of a reducer.

  > ref: http://devdocs.io/redux/basics/reducers

- Export default:
    If we want to export a single value or to have a fallback value for our module, we could use a default export:

    > ref: http://devdocs.io/javascript/statements/export

- Switch and case

  switch:
    The switch statement evaluates an expression, matching the expression's value to a case clause, and executes statements associated with that case.

    > ref: http://devdocs.io/javascript/statements/switch

- Undefined

  undefined:
    The global undefined property represents the primitive value undefined. It is one of JavaScript's primitive types.

    undefined is a property of the global object, i.e. it is a variable in global scope. The initial value of undefined is the primitive value undefined.

    In modern browsers (JavaScript 1.8.5 / Firefox 4+), undefined is a non-configurable, non-writable property per the ECMAScript 5 specification. Even when this is not the case, avoid overriding it.

    A variable that has not been assigned a value is of type undefined. A method or statement also returns undefined if the variable that is being evaluated does not have an assigned value. A function returns undefined if a value was not returned.

    > ref: http://devdocs.io/javascript/global_objects/undefined

- const

  const:
    Constants are block-scoped, much like variables defined using the let statement. The value of a constant cannot change through re-assignment, and it can't be redeclared.

    This declaration creates a constant that can be either global or local to the function in which it is declared. An initializer for a constant is required; that is, you must specify its value in the same statement in which it's declared (which makes sense, given that it can't be changed later).

    The const declaration creates a read-only reference to a value. It does not mean the value it holds is immutable, just that the variable identifier cannot be reassigned. For instance, in case the content is an object, this means the object itself can still be altered.

    > ref: http://devdocs.io/javascript/statements/const


# 19/Nov/2016

- Redux store

  Store:
    A store holds the whole state tree of your application.

    The only way to change the state inside it is to dispatch an action on it.

    A store is not a class. It's just an object with a few methods on it.

    To create it, pass your root reducing function to createStore.

    > ref: http://devdocs.io/redux/api/store


- dispatch(action)

  dispatch(action):
    Dispatches an action. This is the only way to trigger a state change.

    The store's reducing function will be called with the current getState() result and the given action synchronously. Its return value will be considered the next state. It will be returned from getState() from now on, and the change listeners will immediately be notified.

    > ref: http://devdocs.io/redux/api/store#dispatch


- fromJS (immutable-js):
    Deeply converts plain JS objects and arrays to Immutable Maps and Lists.

    > ref: https://facebook.github.io/immutable-js/docs/#/fromJS


- Git push.default

  git push origin:
    Without additional configuration, pushes the current branch to the configured upstream (remote.origin.merge configuration variable) if it has the same name as the current branch, and errors out without pushing otherwise.

    The default behavior of this command when no <refspec> is given can be configured by setting the push option of the remote, or the push.default configuration variable.

    For example, to default to pushing only the current branch to origin use git config remote.origin.push HEAD. Any valid <refspec> (like the ones in the examples below) can be configured as the default for git push origin.

    > ref: http://devdocs.io/git/git-push


- socket.io
  - 'Server' from socket.io
      
    Server():
      Creates a new Server. Works with and without new.

      > ref: http://devdocs.io/socketio/server-api#server


    Server#attach:
      Server#attach(port:Number, opts:Object):Server

      Attaches the Server to an engine.io instance that is bound to port with the given opts (optionally).

      > ref: http://devdocs.io/socketio/server-api#server-attach-srv-http-server-opts-object-server


  - babel-node (from babel-cli package)

    babel-node:
      Not meant for production use
      
      You should not be using babel-node in production. It is unnecessarily heavy, with high memory usage due to the cache being stored in memory. You will also always experience a startup performance penalty as the entire app needs to be compiled on the fly.

      Check out the example Node.js server with Babel for an idea of how to use Babel in a production deployment.

      > ref: https://babeljs.io/docs/usage/cli/

  - WebSockets

    Websocket:
      This is an experimental technology
      
      Because this technology's specification has not stabilized, check the compatibility table for usage in various browsers. Also note that the syntax and behavior of an experimental technology is subject to change in future versions of browsers as the specification changes.

      The WebSocket object provides the API for creating and managing a WebSocket connection to a server, as well as for sending and receiving data on the connection.

      > ref: http://devdocs.io/dom/websocket


  - fallback mechanisms

    'Fallback mechanism':
      Socket.io has fallback mechanisms for clients that don't support WebSockets.

      > ref: http://blog.caplin.com/2010/03/02/why-we-dont-need-html5-websocket/


# 21/Nov/2016

  - Emitting a Socket.io event (io.emit, io.on)
    > ref: http://socket.io/docs/server-api/#server#emit

    Server#emit:
    Emits an event to all connected clients.

  - Subscribe to Redux store

    subscribe(listener)

    Adds a change listener. It will be called any time an action is dispatched, and some part of the state tree may potentially have changed. You may then call getState() to read the current state tree inside the callback.

    Arguments

    listener (Function): The callback to be invoked any time an action has been dispatched, and the state tree might have changed. You may call getState() inside this callback to read the current state tree. It is reasonable to expect that the store's reducer is a pure function, so you may compare references to some deep path in the state tree to learn whether its value has changed.

    > ref: http://devdocs.io/redux/api/store#subscribe


  - .toJS()

    Converts back to raw Javascript objects.

    All immutable Iterables can be converted to plain JavaScript Arrays and Objects shallowly with toArray() and toObject() or deeply with toJS(). All Immutable Iterables also implement toJSON() allowing them to be passed to JSON.stringify directly.

    var deep = Immutable.Map({ a: 1, b: 2, c: Immutable.List.of(3, 4, 5) });
    deep.toObject() // { a: 1, b: 2, c: List [ 3, 4, 5 ] }
    deep.toArray() // [ 1, 2, List [ 3, 4, 5 ] ]
    deep.toJS() // { a: 1, b: 2, c: [ 3, 4, 5 ] }
    JSON.stringify(deep) // '{"a":1,"b":2,"c":[3,4,5]}'

    > ref: https://facebook.github.io/immutable-js/


    Immutable-to-js 

    Convert immutable-js value to regular js value
    Function to convert an immutable-js value to a regular JavaScript value. If the given value is not an immutable-js value, it is simply returned.

    Example
    var toJS = require("immutable-to-js");
    var Immutable = require("immutable");
     
    toJS(Immutable.Map({ foo: 1 })); // -> { foo: 1 } 
    toJS(Immutable.fromJS([1, 2, 3])); // -> [1, 2, 3] 
    toJS("hello"); // -> "hello" 
    toJS(5); // -> 5 

    > ref: https://www.npmjs.com/package/immutable-to-js


  - Event Bus Bridge

    For most applications you probably don’t want client side JavaScript being able to send just any message to any handlers on the server side or to all other browsers.

    For example, you may have a service on the event bus which allows data to be accessed or deleted. We don’t want badly behaved or malicious clients being able to delete all the data in your database!

    Also, we don’t necessarily want any client to be able to listen in on any event bus address.

    To deal with this, a SockJS bridge will by default refuse to let through any messages. It’s up to you to tell the bridge what messages are ok for it to pass through. (There is an exception for reply messages which are always allowed through).

    In other words the bridge acts like a kind of firewall which has a default deny-all policy.

    Configuring the bridge to tell it what messages it should pass through is easy.

    > ref: http://vertx.io/docs/vertx-web/java/#_securing_the_bridge

[screencastLink]: <https://www.youtube.com/watch?v=SZ4-rHL0cl0&list=PLX-RIZuCBJBJLDb3ilr7GVTUWEY-7qDw7>
[bloglink]: <https://medium.com/@pereirawebdev>
[votingClientLink]: <https://github.com/pereiradaniel/voting-client-screencast>
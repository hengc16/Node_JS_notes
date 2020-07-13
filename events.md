# events

### Node.JS core

* Event driven architecture
* emitters- emit named events
* listeners -act on these events

### Emitters:

* Instances of EventEmitter class
* on\(\) method- to register listener
* emit\(\) method -to trigger the event
  * Listeners invoked synchronously, by default

### single call example

```javascript
const EventEmitter = require('events');
const emitter = new EventEmitter();

//on to register listener
emitter.on('event1', (data) => {
    console.log('event1 has raised, args:' , data);
});

//emit to trigger
emitter.emit('event1', {a: 'foo', b: 'bar'});
```

### multiple call example

```javascript
const EventEmitter = require('events');
const emitter = new EventEmitter();

//on to register listener
emitter.on('event1', (data) => {
    console.log('first subscriber: ' , data);
});
//on to register listener
emitter.on('event1', (data) => {
    console.log('second subscriber: ' , data);
});

//emit to trigger
emitter.emit('event1', {a: 'foo', b: 'bar'});

console.log("...after event handlers...");
```

listener invoked synchronously by default. 

the order of the above, is first , second, then console log.

### Asynchronous handlers

```javascript
const EventEmitter = require('events');
const emitter = new EventEmitter();

//on to register listener
emitter.on('event1', (data) => {
    setImmediate(()=> {
        console.log('first event has raised, args:' , data);
    })
});

emitter.on('event1', (data) => {
    setImmediate(()=> {
        console.log('second event has raised, args:' , data);
    })
});

//emit to trigger
emitter.emit('event1', {a: 'foo', b: 'bar'});
console.log("...after event handlers...?");
```

set Immediate will schedule your code into the next clock-cycle, to perform asynchronous.

### conditional handler

```javascript
const EventEmitter = require('events');
const emitter = new EventEmitter();

//on to register listener
emitter.on('event1', (data) => {
    console.log('first subscriber: ' , data);
    data.handled = false;
});
//on to register listener
emitter.on('event1', (data) => {
    if(data.handled){
        console.log("backup-plan triggered", data);
    }
});

//emit to trigger
emitter.emit('event1', {a: 'foo', b: 'bar'});

console.log("...after event handlers...");
```

we can add property called handled to data object. and trigger the second event only if the first event didn't not trigger properly.


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


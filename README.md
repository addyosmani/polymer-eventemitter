polymer-eventemitter
===================

> A Polymer event emitter element with support for wildcards, many and once.

## Features

* Basic events
* Wildcards
* Many
* Once

## API

The following are valid attributes supported by the element:

* **on-event-[name]="{{callback}}"**: subscribes to `event` notifications for an event with the name `[name]`. For example, if you setup `on-event-foo` and then somewhere in your application run `this.asyncFire('event', {name: "foo", data: "Foo!"});` this will trigger `callback`, passing the data specified.
* **on-event-wildcard**: similar to the above, but will trigger for any event fired.
* **many="N"**: subscribes to an event N many times. E.g for `many="3"`, we will no longer execute the callback after the third occurrence.

## Examples

### Basic events

An element listening for an event 'foo' will fire a callback 'fooEvent' when we detect it has been broadcast.

```
<polymer-element name="my-app-a">
  <template>
    <polymer-eventemitter on-event-foo="{{fooEvent}}"></polymer-eventemitter>
    <content></content>
  </template>
  <script>
    Polymer('my-app-a', {
      fooEvent: function(e, detail, sender) {
        this.innerHTML += '<br>[my-app-a] got a [' + detail + '] event<br>';
      }
    });
  </script>
</polymer-element>
```

### Wildcards

An element with a wildcard listener. Catches all events broadcast, firing 'fooWildcard' every time we detect a notification.

```
<polymer-element name="my-app-b">
  <template>
    <polymer-eventemitter on-event-wildcard="{{fooWildcard}}"></polymer-eventemitter>
    <content></content>
  </template>
  <script>
    Polymer('my-app-b', {
      fooWildcard: function(e, detail, sender) {
        this.innerHTML += '<br>[my-app-b] got a [' + detail + '] wildcard event<br>';
      }
    });
  </script>
</polymer-element>
```

### Many

Listen for an event 'baz', N many times. Once 'baz' has been fired N times it will no longer do anything. Note: this differs from EventEmitter2 as its many fires an event N times then removes it.

```
<polymer-element name="my-app-c">
  <template>
    <polymer-eventemitter on-event-baz="{{bazMany}}" many="3"></polymer-eventemitter>
    <content></content>
  </template>
  <script>
    Polymer('my-app-c', {
      bazMany: function(e, detail, sender) {
        this.innerHTML += '<br>[my-app-c] got a [' + detail + '] event many<br>';
      }
    });
  </script>
</polymer-element>
```

### Once

Listen for an event 'faz', 1 many times.

```
<polymer-element name="my-app-d">
  <template>
    <polymer-eventemitter on-event-faz="{{fazOnce}}" many="1"></polymer-eventemitter>
    <content></content>
  </template>
  <script>
    Polymer('my-app-d', {
      fazOnce: function(e, detail, sender) {
        this.innerHTML += '<br>[my-app-d] got a [' + detail + '] event once<br>';
      }
    });
  </script>
</polymer-element>
```

## Inspired by

* https://github.com/hij1nx/EventEmitter2
* https://github.com/Wolfy87/EventEmitter
* https://github.com/Polymer/polymer-elements/tree/master/polymer-signals

## License

Released under a BSD license.
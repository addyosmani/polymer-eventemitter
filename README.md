polymer-eventemitter
===================

> A Polymer element for triggering advanced events anyone can listen to.

Event emitters trigger an event to which anyone can listen. Different libraries offer different implementations and for different purposes, but the basic idea is to provide a framework for issuing events and subscribing to them.


**Examples of what are supported:**

An element listening for an event 'foo' will fire a callback 'fooSignal' when we detect it has been broadcast.

### Basic events (a la Polymer's `fire`)

```
<polymer-element name="my-app-a">
  <template>
    <polymer-eventemitter on-polymer-eventemitter-foo="{{fooSignal}}"></polymer-eventemitter>
    <content></content>
  </template>
  <script>
    Polymer('my-app-a', {
      fooSignal: function(e, detail, sender) {
        this.innerHTML += '<br>[my-app-a] got a [' + detail + '] signal<br>';
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
    <polymer-eventemitter on-polymer-eventemitter-wildcard="{{fooWildcard}}"></polymer-eventemitter>
    <content></content>
  </template>
  <script>
    Polymer('my-app-b', {
      fooWildcard: function(e, detail, sender) {
        this.innerHTML += '<br>[my-app-b] got a [' + detail + '] wildcard signal<br>';
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
    <polymer-eventemitter on-polymer-eventemitter-baz="{{bazMany}}" many="3"></polymer-eventemitter>
    <content></content>
  </template>
  <script>
    Polymer('my-app-c', {
      bazMany: function(e, detail, sender) {
        this.innerHTML += '<br>[my-app-c] got a [' + detail + '] signal many<br>';
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
    <polymer-eventemitter on-polymer-eventemitter-faz="{{fazOnce}}" many="1"></polymer-eventemitter>
    <content></content>
  </template>
  <script>
    Polymer('my-app-d', {
      fazOnce: function(e, detail, sender) {
        this.innerHTML += '<br>[my-app-d] got a [' + detail + '] signal once<br>';
      }
    });
  </script>
</polymer-element>
```

**Reference**

* https://github.com/hij1nx/EventEmitter2
* https://github.com/Wolfy87/EventEmitter
* https://github.com/Polymer/polymer-elements/tree/master/polymer-signals

Released under an MIT License.
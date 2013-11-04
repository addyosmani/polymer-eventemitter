my-polymer-elements
===================

**Event emitter element**

Event emitters trigger an event to which anyone can listen. Different libraries offer different implementations and for different purposes, but the basic idea is to provide a framework for issuing events and subscribing to them.

`polymer-signals` offers an implementation for event emitting but currently lacks the following features:

* Wildcards
* Namespaces
* Time to listen
* Deliminators
* Once/many
* Max listeners

I'll be trying to add some of these features.

Ideally this might look like:

```html
<!--wildcards-->
<polymer-element name="my-app">
  <template>
    <polymer-signals on-polymer-signal-wildcard="{{fooSignal}}"></polymer-signals>
    <content></cotnent>
  </template>
  <script>
    Polymer('my-app', {
      fooSignal: function(e, detail, sender) {
        this.innerHTML += '<br>[my-app] got a [' + detail + '] signal<br>';
      }
    });
  </script>
</polymer-element>

<!--deliminators-->
<polymer-element name="my-app">
  <template>
    <polymer-signals on-polymer-signal-addy::foo="{{fooSignal}}" deliminator="::"></polymer-signals>
    <content></cotnent>
  </template>
  <script>
    Polymer('my-app', {
      fooSignal: function(e, detail, sender) {
        this.innerHTML += '<br>[my-app] got a [' + detail + '] signal<br>';
      }
    });
  </script>
</polymer-element>

<!--max listeners-->
<polymer-element name="my-app">
  <template>
    <polymer-signals on-polymer-signal-foo="{{fooSignal}}" maxListeners="10"></polymer-signals>
    <content></cotnent>
  </template>
  <script>
    Polymer('my-app', {
      fooSignal: function(e, detail, sender) {
        this.innerHTML += '<br>[my-app] got a [' + detail + '] signal<br>';
      }
    });
  </script>
</polymer-element>

<!--many-->
<polymer-element name="my-app">
  <template>
    <polymer-signals on-polymer-signal-foo="{{fooSignal}}" many="4"></polymer-signals>
    <content></cotnent>
  </template>
  <script>
    Polymer('my-app', {
      fooSignal: function(e, detail, sender) {
        this.innerHTML += '<br>[my-app] got a [' + detail + '] signal<br>';
      }
    });
  </script>
</polymer-element>
```

**Reference**

* https://github.com/hij1nx/EventEmitter2
* https://github.com/Wolfy87/EventEmitter
* https://github.com/Polymer/polymer-elements/tree/master/polymer-signals

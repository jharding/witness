# Witness

Inconsistencies across browsers make handling keyboard input a pain in the ass. The goal of Witness is to provide a simple abstraction that makes handling keyboard input easier.

Witness divides keyboard input into 2 groups: [printable characters](http://en.wikipedia.org/wiki/ASCII#ASCII_printable_characters) and [control keys](http://en.wikipedia.org/wiki/ASCII#ASCII_control_characters).

## API

### Witness(config)

* `config`: An object containing the default properties to be overridden. Refer to to the [Configuration](#configuration) section to learn what's configurable.

Constructor function. Calling `new Witness();` will return a Witness instance.

### _witness_.start()

Start listening for keyboard input.

### _witness_.stop()

Stop listening for keyboard input.

###_witness_.addCallback(func)

* `func`: A function to be called when input from the keyboard is received.

Add a callback to be called when keyboard input is received. The callback will be invoked with 1 argument, an object representing the keyboard input. Refer to the [Key Object](#key-object) section for more details.

This method can be called multiple times in order to add multiple callbacks. The callbacks will be invoked in the order they were added.

###_witness_.clearCallbacks()

Clear the collection of callbacks that have been added with the `addCallback` method.

## Configuration

This section details the various options that Witness allows you to configure. The default value of these options can be overridden by passing an object to the Witness constructor.

* `captureControlKeys`: If `true`, input from the keyboard that results in control keys will be captured. Defaults to `true`. 

* `capturePrintableChars`: If `true`, input from the keyboard that results in printable chars will be captured. Defaults to `true`. 

## Key Object

When a witness instance captures keyboard input, it calls all of the callbacks that have been added to it with 1 argument, an object representing the keyboard input. The various properties of that object are detailed below:

* `isPrintableChar`: A boolean that is `true` when the keyboard input is a printable character, `false` otherwise.

* `isControlKey`: A boolean that is `true` when the keyboard input is a control key, `false` otherwise.

* `modifiers`: An object with 4 properties: `altKey`, `shiftKey`, `ctrlKey`, and `metaKey`. Each property is a boolean. If the modifier key they represent was active when the keyboard input was generated, then their value will be `true`, otherwise their value will be `false`.

* `char`: If the keyboard input results in a printable character, this property will be a string representing that printable character. If the keyboard input results in a control key, this property will be `undefined`.

`type`: If the keyboard input results in a control key, this property will be a string representing that control key. If the keyboard input results in a printable character, this property will be `undefined`. Note that each Witness instance contains a property named `CONTROL_KEYS` that is a map of all of the supported control keys.

## Browser Support

Testing hasn't been very extensive, but Witness should work in IE 7+, FF 3+, and Chrome. Witness is broken in Opera and no testing has been done in Safari. As Witness matures, it'll hopefully support all of these browsers and should have a test suite available.

## Limitations

Witness is only meant to support the standard US keyboard. There are no plans to support any other keyboards at this time.

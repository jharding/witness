# Witness

Due to inconsistencies across browsers, handling keyboard input can be a pain. Witness attempts to allievate some of this pain by abstracting away these inconsistencies and by providing a clean API to handle keyboard input.

Witness breaks up the keys on the keyboard into 2 groups: [printable keys](http://en.wikipedia.org/wiki/ASCII#ASCII_printable_characters) and [control keys](http://en.wikipedia.org/wiki/ASCII#ASCII_control_characters). 

## API

### Witness(config)

Constructor function. Calling `new Witness()` will return a Witness instace.

* `config`: An object used to override the default configuration. More info about the configurations Witness provides can be found below.

### _witness_.start()

Invoking this method will cause the Witness instance to begin listening for keyboard input.

### _witness_.stop()

Invoking this method will cause the Witness instance to stop listening for keyboard input.

###_witness_.addCallback(func)

Provide a callback to be invoked when the Witness instace recieves input from the keyboard. The callback will invoked with 1 argument, the key object representing the key that was pressed. More info about the key object can be found below.

This method can be called multiple times in order to add multiple callbacks. The callbacks will be invoked in the order they were added.

###_witness_.clearCallbacks()

Invoking this function will empty out the current collection of callbacks the Witness instance has stored.

## Configuration

When creating a Witness instance, you can pass a configuration object to the constructor. The configurations you pass will override the defaults. 

* `captureControlKeys`: If true, the Witness instance will capture control keys. Defaults to true. 

* `capturePrintableKeys`: If true, the Witness instance will capture printable keys. Defaults to true. 

## Key Object

TODO

## Bugs

Witness should work in IE 7+, FF 3+ and Chrome (latest). At this point, testing hasn't been very extensive though, so bugs could exist.

Witness doesn't work in Opera hasn't been tested in Safari. Support for these browsers is in the pipeline.

Witness also only focuses on standard US keyboards.

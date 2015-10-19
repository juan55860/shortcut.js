
shortcut.js [![Code Climate](https://codeclimate.com/github/blainekasten/shortcut.js/badges/gpa.svg)](https://codeclimate.com/github/blainekasten/shortcut.js) [![Circle CI](https://circleci.com/gh/blainekasten/shortcut.js.svg?style=svg&circle-token=b2b27495568119b977fcf8088c679c721c49792b)](https://circleci.com/gh/blainekasten/shortcut.js)
============


Ever wanted to add keyboard shortcuts to your website, but couldnt justify the time to develop it?

Shortcut.js gives you easy access to add shortcuts to your already existing functions.

Features!
============

- Chainable
- Global and Individual pause/resume functions
- Cross OS Key Bindings ('mod' key)
- CrossBrowser (IE8+, Chrome, FF, Safari Tested)
- UMD compatibility

Installation
===========

`bower install shortcut`
`npm install shortcut.js`

How to use
===========

##### General

    function uppercaseInput(e){...}
    function validateInput(e){...}

    shortcut('mod =', 'input#uppercase').bindsTo(uppercaseInput).bindsTo(validateInput);

Here, when a user presses the the modifier key with the equals key, we run an uppercaseInput function, and then a validateInput function.

API
============

#### shortcut(shortcutKeys, /* optional selector */)

- `String shortcutKeys:` A space delimited set of keys to press. For special keys, use the following mappings:
`shift, meta, optn, ctrl, space, down, right, up, left, tab, rtn`

- `String selector:` a css selector used to specify if the shortcut should be bound to an element. For example, if you wanted a user to be able to press shift+g together in an input box to run a function to uppercase the entire input value, simply do something like: `shortcut('shift =', 'input#uppercase').bindsTo(uppercaseInput)`. When the selector argument is not supplied, the shortcut will get called on the window, meaning at any time the shortcut is pressed the functions will run.

#### +pause()

This function globally pauses all shortcut function dispatching. Keyboard shortcuts pressed after this function will not fire their associated functions.

Useage:

    shortcut.pause();
 
#### +resume()

This function globally resumes all shortcut function dispatching. Keyboard shortcuts pressed after this function WILL fire their associated functions.

Useage:

    shortcut.resume();


#### -bindsTo(fn)

- `function fn:` A function which gets ran when the shortcutKeys are pressed in the appropriate selector.

#### -preventDefault()

A function that prevents default on the current shortcut.
Usage:

    shortcut('meta a', 'input').bindsTo(uppercaseInput).preventDefault()

This usage would cause cmd + a to not hightlight the input, but rather call the uppercaseInput functions.

#### -trigger()

A function to trigger the functions associated to a shortcut.
Usage:

    shortcut('meta a', 'input').bindsTo(function(e){console.log('triggerMe!');}).trigger();
    // Triggers the bindsTo function and outputs:
    // "triggerMe!"

#### -unbind()

A function used to remove bindings to keyboard shortcuts.

Usage:

    shortcut('meta a', 'input').unbind();

Now when a user presses meta a in an input, it will not touch `shortcut` and run its normal native events.

#### -pause()

Pauses event dispatching for the associated shortcut.

Usage:

    shortcut('meta a', 'input').pause();

When a user presss meta a in an input, it will not fire associated functions. Once `-resume()` is called they will fire.

#### -resume()

Resumes event dispatching for the associated shortcut.

Usage:

    shortcut('meta a', 'input').pause();
    // pressing meta a in an input does nothing
    shortcut('meta a', 'input').resume();
    // pressing meta a dispatches the functions again

When a user presss meta a in an input, it will not fire associated functions. Once `-resume()` is called they will fire.


License
===========
Licensed under the MIT license. Copyright 2014 Blaine Kasten


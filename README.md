# FeedbackLed
C++ library for PlatformIO, model of LED with a set of animations to provide visual feedback.

## LICENSE

GPL v3

## What's new

### v0.0.1

Initial publishing, extracted from working code.


## Typical application

_See also [the showcase/maintenance project](https://github.com/sporniket/demo-task-gpio-button-led)_

```cpp
#include "FeedbackLed.hpp"
// etc...

#define MAIN_LED_PIN whatever
FeedbackLed mainLed ; // initialized to OFF

// interrupt to update led status 10 times per second
void onTimerLed() {
    digitalWrite(MY_LED_PIN, mainled.next() ? HIGH : LOW)
}

// ==== some callbacks to manage behavior ====
void onBootstrap() {
    // do stuff...
    mainLed.setFeedbackSequenceAndLoop(FeedbackSequence::BLINK_ONCE) ;
    // do stuff...
}

void onReady() {
    // do stuff...
    mainLed.setFeedbackSequenceOnce(FeedbackSequence::ON) ;
    // do stuff...
}

void onSentData() {
    // do stuff...
    mainLed.setFeedbackSequenceOnce(FeedbackSequence::FALTER_THRICE) ;
    // do stuff...
}


```
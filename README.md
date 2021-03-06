# Clock

A very simple observable clock service for EmberJS.

I display time in many of my projects and need to keep the displayed
time up-to-date so I generalized the solution to this Ember CLI Add-on.

[Live Demo](http://clock.jerel.co/)

[![Build Status](https://travis-ci.org/jerel/ember-cli-clock.svg?branch=master)](https://travis-ci.org/jerel/ember-cli-clock)

## Installation

`npm install --save-dev ember-cli-clock`

## Usage

Inject the `clock` service: `clock: Ember.inject.service()`. Now
you can observe changes like so for use with MomentJS:

    App.TweetComponent = Ember.Component.extend({
      posted: Ember.computed('clock.minute', function() {
        return moment(this.get('timestamp')).fromNow();
      })
    });

    {{posted}} outputs "2 minutes ago" and updates every minute

Or a clock that uses the local system time and updates every second.

    App.ClockComponent = Ember.Component.extend({
      time: Ember.computed('clock.second', function() {
        return moment().format('h:m:s');
      })
    });

## API

You can observe or display the following properties:

* `second`
* `minute`
* `five`
* `quarter`
* `hour`

Each one is an incrementing integer.

During testing you may also set a custom interval time to speed up your tests.
For example use `this.clock.set('intervalTime', 100);` to run the clock 10 times faster.

You may also reset the clock to 0 using `this.clock.reset();`


## Authors

* [Jerel Unruh](http://twitter.com/jerelunruh/)

## Legal

Copyright (c) 2014 Jerel Unruh and contributors

[Licensed under the MIT license](http://www.opensource.org/licenses/mit-license.php)

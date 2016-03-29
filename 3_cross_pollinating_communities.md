talk by [@cball_](https://twitter.com/cball_)

# Cross-Pollinating Communities: We All Win

## Communities that Ember has stolen from

#### SproutCore
'The original JS MVC library.'
* Flagship app: MobileME
* 2.0 would become [Amber.js](http://yehudakatz.com/2011/12/08/announcing-amber-js/), and because of a name conflict, would be renamed Ember.
* Most of the base object model and style of Ember came from SproutCore

#### Ruby on Rails
* Convention over Configuration
* Powerful Tooling
* The router
* "Happy Developer" functions. Singularize/Pluralize, visit/fillIn

#### React
* One-way bindings ("Actions Up, data down.")
* Virtual DOM, DOM Diffing (Glimmer 1)

#### Backbone.js
* modelForRoute/modelDidLoad/componentDidRender/blahblahblah, turned into smaller APIs: model/afterModel/didRender


## Communities that have stolen from Ember

#### React
* Took our fantastic Router

#### Angular
* Also took `route-recognizer` from us, turns URLs into defined routes
* Angular-CLI is just a fork of ember-cli


## How Ember is shaping our community

#### Promises
* Ember made a big bet on Promises, and now Promises are standard across everything.

#### WebComponents
* Same. Safari and Edge have a ways to go here, but the major browsers fully haveit.

#### ES2015++
* ESNext -> ES6 -> ES2015 -> ES2016
* Babel makes forwardporting easy.

#### JSONAPI
* A new standard that already is pushing forward, recently integrated into Rails5 via ActiveModelSerializers.

#### TC39
* Big thing, big idea, with tons of features. Think of it as a large RFC.
* https://tc39.github.io/ecma262/


## "Successful Communities Toggle Between Two Modes"

* Mode 1: Experimentation('Open Mode')
* Mode 2: Shared Solutions('Closed Mode')

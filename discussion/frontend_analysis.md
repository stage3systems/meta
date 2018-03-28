# State of the frontend

### Choices

- ReasonML
- Elm
- Typescript
- Vanilla JS
- Flutter (Fuchsia)
- React Native (probably with Typescript)
- Purescript
- ClojureScript

## Elm

#### Key Facts

- Created by Evan Czaplicki
- First released in 2012
- Astronomy: 4.4k stars in the compiler universe, 1.7k for core
- Clipboard Convenience: 1,241 questions tagged [elm] on StackOverflow

#### Where is it used?

- Stage 3 Systems!
- NoRedInk (educational software)

#### What's it used for?

- Currently only browser apps though some made poorly received efforts to make it work on the backend
- Was not originally intended to be a language for web applications exactly - more a graphics toolkit and it
seems likely that that will eventually be in more environments and avoid the need to transpile to JS entirely by targetting WASM

#### Advantages

- Promises and delivers (with the odd hiccup) no run-time exceptions
- Superb error messages when compared to the soup of a JS traceback
- Single architecture can reduce the amount of Bikeshedding but see below.
- Functional from the ground up in a way that many JS libraries (see the Redux/React universe) have to emulate through
various techniques
- Testing can be easier as side-effects are handled by the run-time (though see below).
- Fearless refactoring
- Relatively portable to possible destinations like
  - Purescript
- Works fine even without moving to 0.19 etc
- Consistent style via elm-format in the style of gofmt etc
- Static type system
- Elm Package if you can stay within the requirements of the repository
- Designed to be learned
  - Introduces functional concepts without nomenclature

#### Disadvantages

- No big backer
- Very dependent on the direction and pace set by its creator Evan
- Single sponsor is relatively small
- Language is pre-1.0 and has changed a lot in the past with the removal of Signals and introduction of Subscriptions
- No JS interop outside of ports but...
- ...ports are not synchronous - so some kinds of JS interop are made harder
- Undocumented native bindings which are meant to go away with 0.19
- Long period between releases with relatively little communication
- Small ecosystem; many common tasks have to be implemented again in Elm
- Very boilerplate heavy esp...
- State management
- JSON decoders/encoders and **
- UI functions that require config to be created for them that makes a simple dropdown take way longer than it should (off to get therapy)

## Typescript

#### Key Facts

- Created by Microsoft (to some surprise at the time)
- Author - many but Anders Hejlsberg (lead architect of C#) seems to have played a big role
- Astronomy: 32,448 stars in its universe
- Clipboard Convenience: 50,228 questions tagged with typescript

#### Where is it used?

- SEDNA
- Lots of places http://www.typescriptlang.org/community/friends.html
- Became primary language of Angular - displacing JS, their own proposed "AtScript", and Dart
- Microsoft

#### What's it used for?

- Anywhere where someone wanted types in place of vanilla JS - serverside node and client side apps plus React Native
- Particularly web apps but also Node and React Native

#### Advantages

- Backed by large company (MS) with many other users now **
- Superset of JS - javascript is valid JS??? - same approach taken by many languages in order to be able to use a pre-existing ecosystem (notably the approach rejected by Elm, see above)
- Typed language with many features now supporting generics, optional types, enums etc **
- Wide adoption

#### Disadvantages

- Requires type definitions to exist for the library being imported and used to be of full value though these exist widely now across the ecosystem (and especially with React etc)
- Not intrinsically functional though React etc can certainly be used without classes etc etc **
  - Maybe a trend towards classes etc in React?
- Error messages are not as nice as Elm
- Complicated type system? Scala of the frontend world...
- Maybe best at giving structure to existing large projects than enable new ones

## VanillaJS

#### Key Facts

- Created by Cthulu
- Really Brendan Eich (possibly Cthulu)
- Developed very hastily by Netscape Communications - featured in the first browser war (the remnants of which became Mozilla and thereby Firefox)
- Various efforts to circumvent especially when it was slow and regarded as a joke of particularly poor taste such as
  - Java in the browser - go make a cup of tea whilst this loads (incidentally also the same amount of time it took to exfiltrate your passwords)
  - Flash - much loved by some until Steve Jobs killed it
- After the Cambrian explosion in JS that followed the second browser war it became incredibly popular and saw use where no one thought it would (except Eich who said he saw it all coming)
- Astronomy: beyond our historic light cone
- Clipboard Convenience: 1,587,152 questions tagged with javascript

#### Where is it used?

- Ubiquitous - I think the dishwasher might be running it right now

#### What's it used for?

- Even aerospace

#### Advantages

- Very large ecosystem - in part due to an almost completely absent standard library
- Vast pool of support
- Surprisingly fast thanks to browser vendors
- Spawned a vast amount of creativity in languages designed to replace it
- Extremely flexible


#### Disadvantages

- Dynamic and weakly typed
- Doesn't 'scale' to larger apps due to the above (imho)
- Inscrutable errors that are likely not related to the place where the actual error is due to the above and the dynamic way code is run - i.e. some property is set very late on and it isn't apparent from the code that you thought would be the problem
- Refactoring: probably better to burn it all down and start again


## ReasonML

#### Key Facts

- Created by Facebook
- First commit in 2016/02/19
- Author Jordan Walke (creator of React)
- Astronomy: 5,335 stars in its universe
- For JS it uses Bucklescript which transpiles it
- Different syntax for OCAML
- Very thin layer over OCAML

#### Where is it used?

- Facebook.com
- Messenger.com (approx 50% of code in ReasonML now)
- Bunch of others - see https://reasonml.github.io/en/users-of-reason.html

####  What's it used for?

- Designed to be a general purpose syntax for OCAML which is a 22 year old programming language.
- It can compile down to assembly
- Has JS interop and a JS transpiler via BuckleScript
- React integration via ReasonReact which includes a redux style notion of state and a reducer function.

#### Advantages

- Appears to have heavyweight backing **
- Functional
- Strict types
- React
- In use on very, very large sites
- OCAML background allows for native compilation also which could lead to FB using it in more places than the browser.
- Has functioning React Native support (mature?) **
- JS interop/escape hatch
- JSX

#### Disadvantages

- Ecosystem is still young
- Unfamiliar syntax for many though similar to Elm
- See 25 questions tagged Reason/reason-react on stackoverflow (approx 79k questions in general for ReactJS, 1,241 for Elm)
- FB moving at speed - updating too often and/or making changes for FB benefit


## Flutter

#### Key Facts

- Created by Google
- Releaed May 2017
- Astronomy: 20,167 stars in its universe
- Clipboard Convenience: 1,495 questions tagged

#### Where is it used?

- Google (TODO: check where)
- Hamilton App
- Assorted other apps

#### What's it used for?

- Strictly mobile app development at this time - they say they are focussing here first

#### Advantages

- Big backer in the form of Google
- But Google is a fickle creature
- But this time they might really mean it because:
  - Java causes some problems (legal and others)
  - They seem to be working on a new OS that might see the light of day (Fuchsia) that's meant to be cross platform and Flutter could be the underpinning of that
- The people behind it are 15 year veterans of Chrome and the Web - they seem to be taking it seriously
- No JS bridge where JS plays puppetmaster to a bunch of native code
- Compiles to native ARM64
- Promises 120fps
- It's written in Dart (but see disadvantages) which is easy to pick up and understand plus strongly typed with v2.0
- Complete code re-use

#### Disadvantages

- It's written in Dart which:
  - Is easy to understand
  - but classic OO (though that's not so bad for interfaces imho)
  - Not much experience with it in the world
  - Java-like
- Very new and Google shut down Reader which has nothing to do with this but still annoys me
- Small ecosystem though large number of provided building blocks and components
- Is google really using this?
- Not for the web


## Purescript

..

## React Native

...

## Meta

- Code reuse on mobile with native frameworks?
  - ios/android reusable?
- Is the web really similar to mobile?
- Maybe not one answer really

## Connect Requirements

- Realistically only React Native or Flutter
- Simpler than web version...

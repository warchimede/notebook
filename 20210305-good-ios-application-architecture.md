# Good iOS App Architecture

## Traits of good architecture
- Each object has a clear role
- Ability to follow data flow with ease
- Doesn't depend on any particular framework
- Flexible, because it's simple, not because it's over abstracted
- Separation of concerns
- Testability

### Separation of Concerns

Define clear boundaries, an object usually should be responsible for a single thing.

### Testability

TDD helps create a better architecture.
- Writing tests first gives you a clearer perspective on the ideal API design
- If tests are hard to write it's usually a sign something could be improved with the architecture, with RGR (Red-Green-Refactor) you can catch that early on.

### Limited dependencies

## Signs of wrong architecture

### Too many lines

```
find . -type f exec wc -l {} + | sort -n
```

### Use of global states everywhere (app delegate)

```
grep -rnw . -e "UIApplication.sharedApplication().delegate"
```

## Design Patterns

- These are part of your toolkit, you should not be religious about it.
- You can have all the best design patterns in your code and make total shit with it.

### Singletons

- Singleton is not intrinsicly wrong, but the usual way it is used makes it bad.
- It's not supposed to be a pattern to wrap globals.
- An example of a decent use of Singleton in most apps is a Logger
- Even if you have some singletons, you don't need to expose them. Often you can leverage protocol oriented programming and default implementations.

### Composition (the one to master)

This is a pattern that naturally leads to other great patterns.

- Composition done right will actually make you follow SRP and DRY principles.
- It makes the code easier to test
- Flexible and easy to re-arrange

### Dependency Injection (goes well with composition)

- It allows you to swap underlying components when testing or for different platforms

## MVVM+ with Flow Coordinators (Router)

### Flow Coordinator

- Creates `ViewController` or `ViewModel`
- Configures based on Context
- Presents based on Context
- Listens to `ViewModel` events and reacts by coordinating the Flow
- Injects all objects needed to fulfill their role

### ViewModel

- No knowledge about Presentation
- No UIKit
- Black-box interface for all triggers

## [Source](20210305-good-ios-application-architecture.md)
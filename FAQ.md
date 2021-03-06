# FAQs

<!-- !!! READ THIS !!! -->
<!-- The table of contents is auto-generated using doctoc. Don't edit manually! -->
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


  - [Common Feature Requests](#common-feature-requests)
  - [Type System Behavior](#type-system-behavior)
    - [What is structural typing?](#what-is-structural-typing)
    - [What is type erasure?](#what-is-type-erasure)
    - [Why are getters without setters not considered read-only?](#why-are-getters-without-setters-not-considered-read-only)
    - [Why are function parameters bivariant?](#why-are-function-parameters-bivariant)
    - [Why are functions with fewer parameters assignable to functions that take more parameters?](#why-are-functions-with-fewer-parameters-assignable-to-functions-that-take-more-parameters)
    - [Why are functions returning non-`void` assignable to function returning `void`?](#why-are-functions-returning-non-void-assignable-to-function-returning-void)
    - [Why are all types assignable to empty interfaces?](#why-are-all-types-assignable-to-empty-interfaces)
    - [Can I make a type alias nominal?](#can-i-make-a-type-alias-nominal)
    - [How do I prevent two types from being structurally compatible?](#how-do-i-prevent-two-types-from-being-structurally-compatible)
    - [How do I check at runtime if an object implements some interface?](#how-do-i-check-at-runtime-if-an-object-implements-some-interface)
    - [Why doesn't this incorrect cast throw a runtime error?](#why-doesnt-this-incorrect-cast-throw-a-runtime-error)
    - [Why don't I get type checking for `(number) => string` or `(T) => T`?](#why-dont-i-get-type-checking-for-number--string-or-t--t)
    - [Why am I getting an error about a missing index signature?](#why-am-i-getting-an-error-about-a-missing-index-signature)
  - [Functions](#functions)
    - [Why can't I use `x` in the destructuring `function f({ x: number }) { /* ... */ }`?](#why-cant-i-use-x-in-the-destructuring-function-f-x-number------)
  - [Classes](#classes)
    - [Why do these empty classes behave strangely?](#why-do-these-empty-classes-behave-strangely)
    - [When and why are classes nominal?](#when-and-why-are-classes-nominal)
    - [Why does `this` get orphaned in my instance methods?](#why-does-this-get-orphaned-in-my-instance-methods)
    - [What's the difference between `Bar` and `typeof Bar` when `Bar` is a `class` ?](#whats-the-difference-between-bar-and-typeof-bar-when-bar-is-a-class-)
    - [Why do my derived class property initializers overwrite values set in the base class constructor?](#why-do-my-derived-class-property-initializers-overwrite-values-set-in-the-base-class-constructor)
    - [What's the difference between `declare class` and `inteface`?](#whats-the-difference-between-declare-class-and-inteface)
    - [What does it mean for an interface to extend a class?](#what-does-it-mean-for-an-interface-to-extend-a-class)
    - [Why am I getting "TypeError: [base class name] is not defined in `__extends` ?](#why-am-i-getting-typeerror-base-class-name-is-not-defined-in-__extends-)
    - [Why am I getting "TypeError: Cannot read property 'prototype' of undefined" in `__extends` ?](#why-am-i-getting-typeerror-cannot-read-property-prototype-of-undefined-in-__extends-)
  - [Generics](#generics)
    - [Why is `A<string>` assignable to `A<number>` for `interface A<T> { }`?](#why-is-astring-assignable-to-anumber-for-interface-at--)
    - [Why can't I write `typeof T` or `instanceof T` in my generic function?](#why-cant-i-write-typeof-t-or-instanceof-t-in-my-generic-function)
  - [Modules](#modules)
    - [Why are imports being elided in my emit?](#why-are-imports-being-elided-in-my-emit)
    - [Why don't namespaces merge across different module files?](#why-dont-namespaces-merge-across-different-module-files)
  - [Enums](#enums)
    - [What's the difference between `enum` and `const enum`s?](#whats-the-difference-between-enum-and-const-enums)
  - [Type Guards](#type-guards)
    - [Why doesn't `x instanceof Foo` narrow `x` to `Foo`?](#why-doesnt-x-instanceof-foo-narrow-x-to-foo)
    - [Why doesn't `isFoo(x)` narrow `x` to `Foo` when `isFoo` is a type guard?](#why-doesnt-isfoox-narrow-x-to-foo-when-isfoo-is-a-type-guard)
  - [Decorators](#decorators)
    - [Decorators on function declarations](#decorators-on-function-declarations)
    - [What's the difference between `@dec` and `@dec()` ? Shouldn't they be equivalent?](#whats-the-difference-between-@dec-and-@dec--shouldnt-they-be-equivalent)
  - [JSX and React](#jsx-and-react)
    - [I wrote `declare var MyComponent: React.Component;`, why can't I write `<MyComponent />` ?](#i-wrote-declare-var-mycomponent-reactcomponent-why-cant-i-write-mycomponent--)
  - [Things That Don't Work](#things-that-dont-work)
    - [You should emit classes like this so they have real private members](#you-should-emit-classes-like-this-so-they-have-real-private-members)
    - [You should emit classes like this so they don't lose `this` in callbacks](#you-should-emit-classes-like-this-so-they-dont-lose-this-in-callbacks)
    - [You should have some class initialization which is impossible to emit code for](#you-should-have-some-class-initialization-which-is-impossible-to-emit-code-for)
  - [External Tools](#external-tools)
    - [How do I write unit tests with TypeScript?](#how-do-i-write-unit-tests-with-typescript)
  - [Commandline Behavior](#commandline-behavior)
    - [Why did adding an `import` or `export` modifier break my program?](#why-did-adding-an-import-or-export-modifier-break-my-program)
    - [How do I control file ordering in combined output (`--out`) ?](#how-do-i-control-file-ordering-in-combined-output---out-)
    - [What does the error "Exported variable [name] has or is using private name [name]" mean?](#what-does-the-error-exported-variable-name-has-or-is-using-private-name-name-mean)
- [Glossary and Terms in this FAQ](#glossary-and-terms-in-this-faq)
    - [Dogs, Cats, and Animals, Oh My](#dogs-cats-and-animals-oh-my)
    - ["Substitutability"](#substitutability)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Common Feature Requests
> I want to request one of the following features...

Here's a list of common feature requests and their corresponding issue.
Please leave comments in these rather than logging new issues.
* Non-nullable values [#185](https://github.com/Microsoft/TypeScript/issues/185)
* Minification [#8](https://github.com/Microsoft/TypeScript/issues/8)
* Read-only properties [#12](https://github.com/Microsoft/TypeScript/issues/12)
* Extension methods [#9](https://github.com/Microsoft/TypeScript/issues/9)
* Partial classes [#563](https://github.com/Microsoft/TypeScript/issues/563)
* Non-numeric or string-based `enum`s [#1206](https://github.com/Microsoft/TypeScript/issues/1206)
* Wildcards or globbing in tsconfig.json: [#1927](https://github.com/Microsoft/TypeScript/issues/1927)
* Safe navigation operator, AKA CoffeeScript's null conditional/propagating/propagation operator, AKA C#'s' ?. operator [#16](https://github.com/Microsoft/TypeScript/issues/16)
* Something to do with `this` [#513](https://github.com/Microsoft/TypeScript/issues/513)
* Generic type parameter defaults [#2175](https://github.com/Microsoft/TypeScript/issues/2175)
* Strong typing of `Function` members `call`/`bind`/`apply` [#212](https://github.com/Microsoft/TypeScript/issues/212)
* Function overloading [#3442](https://github.com/Microsoft/TypeScript/issues/3442)
* Referencing generic components in JSX [#6395](https://github.com/Microsoft/TypeScript/issues/6395) 

## Type System Behavior

### What is structural typing?
TypeScript uses *structural typing*.
This system is different than the type system employed by some other popular languages you may have used (e.g. Java, C#, etc.)

The idea behind structural typing is that two types are compatible if their *members* are compatible.
For example, in C# or Java, two classes named `MyPoint` and `YourPoint`, both with public `int` properties `x` and `y`, are not interchangeable, even though they are identical.
But in a structural type system, the fact that these types have different names is immaterial.
Because they have the same members with the same types, they are identical.

This applies to subtype relationships as well.
In C++, for example, you could only use a `Dog` in place of an `Animal` if `Animal` was explicitly in `Dog`'s class heritage.
In TypeScript, this is not the case -- a `Dog` with at least as many members (with appropriate types) as `Animal` is a subtype of `Animal` regardless of explicit heritage.

This can have some surprising consequences for programmers accustomed to working in a nominally-typed language.
Many questions in this FAQ trace their roots to structural typing and its implications.
Once you grasp the basics of it, however, it's very easy to reason about.

### What is type erasure?

TypeScript *removes* type annotations, interfaces, type aliases, and other type system constructs during compilation.

Input:

```ts
var x: SomeInterface;
```

Output:

```js
var x;
```

This means that at run-time, there is no information present that says that some variable `x` was declared as being of type `SomeInterface`.

The lack of run-time type information can be surprising for programmers who are used to extensively using reflection or other metadata systems.
Many questions in this FAQ boil down to "because types are erased".

### Why are getters without setters not considered read-only?

> I wrote some code like this and expected an error:
> ```ts
> class Foo {
>    get bar() {
>      return 42;
>    }
> }
> let x = new Foo();
> // Expected error here
> x.bar = 10;
> ```

A getter without a setter *does not* create a read-only property.
See  [#12](https://github.com/Microsoft/TypeScript/issues/12) for the suggestion tracking this issue.

### Why are function parameters bivariant?

 > I wrote some code like this and expected an error:
 > ```ts
 > function trainDog(d: Dog) { ... }
 > function cloneAnimal(source: Animal, done: (result: Animal) => void): void { ... }
 > let c = new Cat();
 > // Runtime error here occurs because we end up invoking 'trainDog' with a 'Cat'
 > cloneAnimal(c, trainDog);
 > ```

This is a unsoundness resulting from the lack of explicit covariant / contravariant annotations in the type system.

To see why this happens, consider two questions: Is `Dog[]` a subtype of `Animal[]` ? *Should* `Dog[]` be a subtype of `Animal[]`?

The second question (*should* `Dog[]` be a subtype of `Animal[]`?) is an easier one.
What if the answer was "no" ?
```ts
function checkAnimalsAreAwake(arr: Animal[]) { ... }

let myPets: Dog[] = [spot, fido];
// Error? Can't substitute Dog[] for Animal[] ?
checkAnimalsAreAwake(myPets);
```
This would be *incredibly annoying*.
The code here is 100% correct.
There's not a good reason to reject this program on the basis that `Dog[]` can't be used in place of `Animal[]` -- clearly a group of `Dog`s is a group of `Animal`s.

Back to the first question.
When the type system is *deciding* whether or not `Dog[]` is a subtype of `Animal[]`, it does the following computation (written here as if the compiler took no optimizations), among many others:

 * Is `Dog[]` assignable to Animal[]` ?
  * Is each member of `Dog[]` assignable to `Animal[]` ?
    * Is `Dog[].push` assignable to `Animal[].push` ?
      * Is the type `(x: Dog) => number` assignable to `(x: Animal) => number` ?
        * Is the first parameter type in `(x: Dog) => number` assignable to or from first parameter type in `(x: Animal) => number`?
          * Is `Dog` assignable to or from `Animal`?
            * Yes

As you can see here, the relevant question *Is the type `(x: Dog) => number` assignable to `(x: Animal) => number` ?* is the same question
being asked when we were passing a possibly-too-specific callback to a function.

In summary, in the TypeScript type system, the question of *whether a more-specific-type-accepting function should be assignable to a
function accpting a less-specific type* provides a prerequisite answer to whether an *array* of that more specific type should be assignable
to an array of a less specific type. Having the latter *not* be the case would not be an acceptable type system in the vast majority of cases,
so we have to take a correctness trade-off for the specific case of function argument types.

### Why are functions with fewer parameters assignable to functions that take more parameters?

> I wrote some code like this and expected an error:
> ```ts
> function handler(arg: string) {
>     // ....
> }
> 
> function doSomething(callback: (arg1: string, arg2: number) => void) {
>     callback('hello', 42);
> }
> 
> // Expected error because 'doSomething' wants a callback of
> // 2 parameters, but 'handler' only accepts 1
> doSomething(handler);
> ```

This is the expected and desired behavior.
First, refer to the "substitutability" primer at the top of the FAQ -- `handler` is a valid argument for `callback` because it can safely ignored extra parameters.

Second, let's consider another case:
```ts
let items = [1, 2, 3];
items.forEach(arg => console.log(arg));
```

This is isomorphic to the example that "wanted" an error.
At runtime, `forEach` invokes the given callback with three arguments (value, index, array), but most of the time the callback only uses one or two of the arguments.
This is a very common JavaScript pattern and it would be burdensome to have to explicitly declare unused parameters.

### Why are functions returning non-`void` assignable to function returning `void`?

> I wrote some code like this and expected an error:
> ```ts
> function doSomething(): number {
>     return 42;
> }
> 
> function callMeMaybe(callback: () => void) {
>     callback();
> }
> 
> // Expected an error because 'doSomething' returns number, but 'callMeMaybe' expects void-returning function
> callMeMaybe(doSomething);
> ```

This is the expected and desired behavior.
First, refer to the "substitutability" primer -- the fact that `doSomething` returns "more" information than `callMeMaybe` is a valid substitution.

Second, let's consider another case:
```ts
let items = [1, 2];
callMeMaybe(() => items.push(3));
```
This is isomorphic to the example that "wanted" an error.
`Array#push` returns a number (the new length of the array), but it's a safe substitute to use for a `void`-returning function.

Another way to think of this is that a `void`-returning callback type says "I'm not going to look at your return value, if one exists".

### Why are all types assignable to empty interfaces?

> I wrote some code like this an expected an error:
> ```ts
> interface Thing { /* nothing here */ }
> function doSomething(a: Thing) {
>   // mysterious implementation here
> }
> // Expected some or all of these to be errors
> doSomething(window);
> doSomething(42);
> doSomething('huh?');
> ```

Types with no members can be substituted by *any* type.
In this example, `window`, `42`, and `'huh?'` all have the required members of a `Thing` (there are none).

In general, you should *never* find yourself declaring an `interface` with no properties.

### Can I make a type alias nominal?

> I wrote the following code and expected an error:
> ```ts
> type SomeUrl = string;
> type FirstName = string;
> let x: SomeUrl = "http://www.typescriptlang.org/";
> let y: FirstName = "Bob';
> x = y; // Expected error
> ```

Type aliases are simply *aliases* -- they are indistinguishable from the types they refer to.

A workaround involving intersection types to make "branded primitives" is possible:
```ts
// Strings here are arbitrary, but must be distinct
type SomeUrl = string & {'this is a url': {}};
type FirstName = string & {'person name': {}};

// Add type assertions
let x = <SomeUrl>'';
let y = <FirstName>'bob';
x = y; // Error

// OK
let xs: string = x;
let ys: string = y;
xs = ys;
```
You'll need to add a type assertion wherever a value of this type is created.
These can still be aliased by `string` and lose type safety.

### How do I prevent two types from being structurally compatible?
> I would like the following code to produce an error:
> ```ts
> interface ScreenCoordinate {
>   x: number;
>   y: number;
> }
> interface PrintCoordinate {
>   x: number;
>   y: number;
> }
> function sendToPrinter(pt: PrintCoordinate) {
>   // ...
> }
> function getCursorPos(): ScreenCoordinate {
>   // Not a real implementation
>   return { x: 0, y: 0 };
> }
> // This should be an error
> sendToPrinter(getCursorPos());
> ```

A possible fix if you really want two types to be incompatible is to add a 'brand' member:
```ts
interface ScreenCoordinate {
  _screenCoordBrand: any;
  x: number;
  y: number;
}
interface PrintCoordinate {
  _printCoordBrand: any;
  x: number;
  y: number;
}

// Error
sendToPrinter(getCursorPos());
```

Note that this will require a type assertion wherever 'branded' objects are created:
```ts
function getCursorPos(): ScreenCoordinate {
  // Not a real implementation
  return <ScreenCoordinate>{ x: 0, y: 0 };
}
```

See also [#202](https://github.com/Microsoft/TypeScript/issues/202) for a suggestion tracking making this more intuitive.

### How do I check at runtime if an object implements some interface?

> I want to write some code like this:
> ```ts
> interface SomeInterface {
>   name: string;
>   length: number;
> }
> interface SomeOtherInterface {
>   questions: string[];
> }
> 
> function f(x: SomeInterface|SomeOtherInterface) {
>   // Can't use instanceof on interface, help?
>   if (x instanceof SomeInterface) {
>     // ...
>   }
> }
> ```

TypeScript types are erased (https://en.wikipedia.org/wiki/Type_erasure) during compilation.
This means there is no built-in mechanism for performing runtime type checks.
It's up to you to decide how you want to distinguish objects.
A popular method is to check for properties an on object.
You can use user-defined type guards to accomplish this:

```ts
function isSomeInterface(x: any): x is SomeInterface {
  return typeof x.name === 'string' && typeof x.length === 'number';

function f(x: SomeInterface|SomeOtherInterface) {
  if (isSomeInterface(x)) {
    console.log(x.name); // Cool!
  }
}
```

### Why doesn't this incorrect cast throw a runtime error?
> I wrote some code like this:
> ```ts
> let x: any = true;
> let y = <string>x; // Expected: runtime error (can't convert boolean to string)
> ```
or this
> ```ts
> let a: any = 'hmm';
> let b = a as HTMLElement; // expected b === null
> ```

TypeScript has *type assertions*, not *type casts*.
The intent of `<T>x` is to say "TypeScript, please treat `x` as a `T`", not to perform a typesafe runtime conversion.
Because types are erased, there is no direct equivalent of C#'s `expr as` type or `(type)expr` syntax.


### Why don't I get type checking for `(number) => string` or `(T) => T`?
> I wrote some code like this and expected an error:
> ```ts
> let myFunc: (number) => string = (n) => 'The number in hex is ' + n.toString(16);
> // Expected error because boolean is not number
> console.log(myFunc(true));
> ```

Parameter names in function types are required.
The code as written describes a function taking one parameter named `number` of type `any`.
In other words, this declaration
```ts
let myFunc: (number) => string
```
is equivalent to this one
```ts
let myFunc: (number: any) => string
```

To avoid this problem, turn on the `noImplicitAny` flag, which will issue a warning about the implicit `any` parameter type.

### Why am I getting an error about a missing index signature?

TODO: Port content from here

http://stackoverflow.com/questions/22077023/why-cant-i-indirectly-return-an-object-literal-to-satisfy-an-index-signature-re

-------------------------------------------------------------------------------------

## Functions

### Why can't I use `x` in the destructuring `function f({ x: number }) { /* ... */ }`?
> I wrote some code like this and got an unexpected error:
> ```ts
> function f({x: number}) {
>   // Error, x is not defined?
>   console.log(x);
> }
> ```

Destructuring syntax is counterintuitive for those accustomed to looking at TypeScript type literals.
The syntax `f({x: number})` declares a destructuring *from the property* `x` *to the local* `number`.

Looking at the emitted code for this is instructive:
```ts
function f(_a) {
    // Not really what we were going for
    var number = _a.x;
}
```

To write this code correctly, you should write:
```ts
function f({x}: {x: number}) {
  // OK
  console.log(x);
}
```

If you can provide a default for all properties, it's preferable to write:
```ts
function f({x = 0}) {
  // x: number
  console.log(x);
}
```

-------------------------------------------------------------------------------------

## Classes

### Why do these empty classes behave strangely?

> I wrote some code like this and expected an error:
> ```ts
> class Empty { /* empty */ }
> 
> var e2: Empty = window;
> ```

See the question "Why are all types assignable to empty interfaces?" in this FAQ.


### When and why are classes nominal?

What explains the difference between these two lines of code?
```ts
class Alpha { x: number }
class Bravo { x: number }
class Charlie { private x: number }
class Delta { private x: number }

let a = new Alpha(), b = new Beta(), c = new Charlie(), d = new Delta();

a = b; // OK
c = d; // Error
```

In TypeScript, classes are compared structurally.
The one exception to this is `private` and `protected` members.
When a member is private or protected, it must *originate in the same declaration* to be considered the same as another private or protected member.


### Why does `this` get orphaned in my instance methods?

> I wrote some code like this:
> ```ts
> class MyClass {
>   x = 10;
>   someCallback() {
>     console.log(this.x); // Prints 'undefined', not 10
>     this.someMethod(); // Throws error "this.method is not a function"
>   }
>   someMethod() {
>     
>   } 
> }
> 
> let obj = new MyClass();
> window.setTimeout(obj.someCallback, 10);
> ```

Synonyms and alternate symptoms:
> * Why are my class properties `undefined` in my callback?
> * Why does `this` point to `window` in my callback?
> * Why does `this` point to `undefined` in my callback?
> * Why am I getting an error `this.someMethod is not a function`?
> * Why am I getting an error `Cannot read property 'someMethod' of undefined` ?

In JavaScript, the value of `this` inside a function is determined as follows:
 1. Was the function the result of calling `.bind`? If so, `this` is the first argument passed to `bind`
 2. Was the function *directly* invoked via a property access expression `expr.method()` ? If so, `this` is `expr`
 3. Otherwise, `this` is `undefined` (in "strict" mode), or `window` in non-strict mode

The offending problem is this line of code:
```ts
window.setTimeout(obj.someCallback, 10);
```
Here, we provided a function reference to `obj.someCallback` to `setTimeout`.
The function was then invoked on something that wasn't the result of `bind` and wasn't *directly* invoked as a method.
Thus, `this` in the body of `someCallback` referred to `window` (or `undefined` in strict mode).

Solutions to this are outlined here: http://stackoverflow.com/a/20627988/1704166

### What's the difference between `Bar` and `typeof Bar` when `Bar` is a `class` ?
> I wrote some code like this and don't understand the error I'm getting:
> ```ts
> class MyClass {
>   someMethod() { }
> }
> var x: MyClass;
> // Cannot assign 'typeof MyClass' to MyClass? Huh?
> x = MyClass;
> ```

It's important to remember that in JavaScript, classes are just functions.
We refer to the class object itself -- the *value* `MyClass` -- as a *constructor function*.
When a constructor function is invoked with `new`, we get back an object that is an *instance* of the class.

So when we define a class, we actually define two different *types*.

The first is the one referred to by the class's name; in this case, `MyClass`.
This is the *instance* type of the class.
It defines the properties and methods that an *instance* of the class has.
It's the type returned by invoking the class's constructor.

The second type is anonymous.
It is the type that the constructor function has.
It contains a *construct signature* (the ability to be invoked with `new`) that returns an *instance* of the class.
It also contains any `static` properties and methods the class might have.
This type is typically referred to as the "static side" of the class because it contains those static members (as well as being the *constructor* for the class).
We can refer to this type with the type query operator `typeof`.

The `typeof` operator (when used in a *type* position) expresses the *type* of an *expression*.
Thus, `typeof MyClass` refers to the type of the expression `MyClass` - the *constructor function* that produces instances of `MyClass`.


### Why do my derived class property initializers overwrite values set in the base class constructor?
See [#1617](https://github.com/Microsoft/TypeScript/issues/1617) for this and other initialization order questions


### What's the difference between `declare class` and `inteface`?

TODO: Write up common symptoms of `declare class` / `interface` confusion.

See http://stackoverflow.com/a/14348084/1704166


### What does it mean for an interface to extend a class?

> What does this code mean?
> 
> ```ts
> class Foo {
>   /* ... */
> }
> interface Bar extends Foo {
>   
> }
> ```

This makes a type called `Bar` that has the same members as the instance shape of `Foo`.
However, if `Foo` has private members, their corresponding properties in `Bar` must be implemented
  by a class which has `Foo` in its heritage.
In general, this pattern is best avoided, especially if `Foo` has private members.

### Why am I getting "TypeError: [base class name] is not defined in `__extends` ?
> I wrote some code like this:
> ```ts
> /** file1.ts **/
> class Alpha { /* ... */ }
> 
> /** file2.ts **/
> class Bravo extends Alpha { /* ... */ }
> ```
> I'm seeing a runtime error in `__extends`:
> ```
> Uncaught TypeError: Alpha is not defined
> ```

The most common cause of this is that your HTML page includes a `<script>` tag for file2.ts, but not file1.ts.
Add a script tag for the base class's output *before* the script tag for the derived class.

### Why am I getting "TypeError: Cannot read property 'prototype' of undefined" in `__extends` ?
> I wrote some code:
> ```ts
> /** file1.ts **/
> class Alpha { /* ... */ }
> 
> /** file2.ts **/
> class Bravo extends Alpha { /* ... */ }
> ```
> I'm seeing a runtime error in `__extends`:
> ```
> Uncaught TypeError: Cannot read property 'prototype' of undefined
> ```

This can happen for a few reasons.

The first is that, within a single file, you defined the derived class *before* the base class.
Re-order the file so that base classes are declared before the derived classes.

If you're using `--out`, the compiler may be confused about what order you intended the files to be in.
See the section "How do I control file ordering..." in the FAQ.

If you're not using `--out`, your script tags in the HTML file may be the wrong order.
Re-order your script tags so that files defining base classes are included before the files defining the derived classes.

Finally, if you're using a third-party bundler of some sort, that bundler may be ordering files incorrectly.
Refer to that tool's documentation to understand how to properly order the input files in the resulting output.

-------------------------------------------------------------------------------------

## Generics

### Why is `A<string>` assignable to `A<number>` for `interface A<T> { }`?

> I wrote some code and expected an error:
> ```ts
> interface Something<T> {
>   name: string;
> }
> let x: Something<number>;
> let y: Something<string>;
> // Expected error: Can't convert Something<number> to Something<string>!
> x = y;
> ```

TypeScript uses a structural type system.
When determining compatibility between `Something<number>` and `Something<string>`, we examine each *member* of each type.
If each member of the types are compatible, then the type are compatible as well.
Because `Something<T>` doesn't *use* `T` in any member, it doesn't matter what type `T` is.

In general, you should *never* have a type parameter which is unused.
The type will have unexpected compatibility (as shown here) and will also fail to have proper generic type inference in function calls.

### Why can't I write `typeof T` or `instanceof T` in my generic function?

> I want to write some code like this:
> ```ts
> function doSomething<T>(x: T) {
>   // Can't find name T?
>   let xType = typeof T;
>   let y = new xType();
> 
>   // Same here?
>   if(someVar instanceof typeof T) {
> 
>   }
> }
> ```

Generics are erased during compilation.
This means that there is no *value* `T` at runtime inside `doSomething`.
The normal pattern that people try to express here is to use the constructor function for a class either as a factory or as a runtime type check.
In both cases, using a *construct signature* and providing it as a parameter will do the right thing:

```ts
function create<T>(ctor: { new(): T }) {
    return new ctor();
}
var c = create(MyClass); // c: MyClass

function isReallyInstanceOf<T>(ctor: { new(...args: any) => T }, obj: T) {
  return obj instanceof ctor;
}
```

-------------------------------------------------------------------------------------
## Modules

### Why are imports being elided in my emit?
 
> I wrote some code like this
> ```ts
> import someModule = require('./myMod');
> 
> let x: someModule.SomeType = /* something */;
> ```
> 
> and the emit looked like this:
> ```js
> // Expected to see "var someModule = require('./myMod');" here!
> 
> var x = /* something */;
> ```

TypeScript assumes that module imports do not have side effects, so it removes module imports that aren't used in any *expression*.
Depending on your exact scenario, there are a few workarounds.

You can simply reference the module. This is the most universal workaround. A single use will do:

```ts
import someModule = require('./myMod');
someModule; // Used for side effects
```

If you're using CommonJS (typically with Node), you can use `require` directly while still using the import for type information:
```ts
import _someModule = require('./myMod');
const someModule: typeof _someModule = require('./myMod');
```

If you're using CommonJS and *don't* need type information, you can just invoke `require`:
```ts
require('./myMod');
```

If you're using AMD, you can use the `amd-depedency` tag:
```ts
/// <amd-depedency path="./myMod" />
import someModule = require('./myMod');
```

### Why don't namespaces merge across different module files?

TODO: Port content from
http://stackoverflow.com/questions/30357634/how-do-i-use-namespaces-with-typescript-external-modules

-------------------------------------------------------------------------------------

## Enums

### What's the difference between `enum` and `const enum`s?

TODO: Write up common symptoms of `enum` / `const enum` confusion.

See http://stackoverflow.com/questions/28818849/how-do-the-different-enum-variants-work-in-typescript

-------------------------------------------------------------------------------------

## Type Guards

### Why doesn't `x instanceof Foo` narrow `x` to `Foo`?

It depends what `x` is.
If the type of `x` was originally not even compatible with `Foo`, then it wouldn't make much sense to narrow the type, so we don't.

More likely, you'll find yourself in this situation when `x` had the type `any`.
The motivating example for this is something like the following:

```ts
function doIt(x) {
    if (x instanceof Object) {
        // Assume 'x' is a well-known object which
        // we know how to handle specifically
    }

    // Treat 'x' as a primitive
}
```

You'll see this type of code in TypeScript code that predates union types, or TypeScript code that's been ported over from JavaScript.
If we narrowed from `any` to `Object` then there's not much you could really do with `x`.
Using any properties that aren't in `Object` will lead to an error.
This is not just true of `Object`, it's true of any other type with a defined set of properties.

### Why doesn't `isFoo(x)` narrow `x` to `Foo` when `isFoo` is a type guard?

TODO, but it is strongly related to the above section.

-------------------------------------------------------------------------------------
## Decorators

### Decorators on function declarations
TODO: Answer. Also, what did we mean here?

### What's the difference between `@dec` and `@dec()` ? Shouldn't they be equivalent?
TODO: Answer

-------------------------------------------------------------------------------------

## JSX and React

### I wrote `declare var MyComponent: React.Component;`, why can't I write `<MyComponent />` ?

> I wrote some code like this. Why is there an error?
> ```ts
> class Display extends React.Component<any, any> {
>     render() { ... }
> }
> 
> let SomeThing: Display = /* ... */;
> // Error here, isn't this OK?
> let jsx = <SomeThing />;
> ```

This is a confusion between the *instance* and *static* side of a class.
When React instantiates a component, it's invoking a *constructor function*.
So when TypeScript sees a JSX `<TagName />`, it is validating that the result of *constructing* `TagName` produces a valid component.

But by declaring `let SomeThing: Display`, the code is indicating that `SomeThing` is the class *instance*, not the class *constructor*.
Indeed, it would be a runtime error to write:
```ts
let SomeThing = new Display();
let jsx = <SomeThing />; // Not gonna work
```

The easiest fix is to use the `typeof` type operator.
> let SomeThing: typeof Display = /* ... */;

-------------------------------------------------------------------------------------

## Things That Don't Work

### You should emit classes like this so they have real private members

> If I write code like this:
> ```ts
> class Foo {
> 	private x = 0;
> 	increment(): number {
> 		this.x++;
>       return x;
> 	}
> }
> ```
> You should emit code like this so that 'x' is truly private:
> ```js
> var Foo = (function () {
> 	  var x = 0;
> 	
>     function Foo() {
>     }
>     Foo.prototype.increment = function () {
>         x++;
>         return x;
>     };
>     return Foo;
> })();
> ```

This code doesn't work.
It creates a *single* private field that all classes share:
```js
var a = new Foo();
a.increment(); // Prints 1
a.increment(); // Prints 2
var b = new Foo(); // Should not affect a
a.increment(); // Prints 1
```

### You should emit classes like this so they don't lose `this` in callbacks
> If I write code like this:
> ```ts
> class MyClass {
> 	method() {
> 	}
> }
> ```
> You should emit code like this so that I can't mess up `this` in in callbacks:
> ```js
> var MyClass = (function () {
>     function MyClass() {
> 		this.method = function() {
> 			
> 		}
>     }
>     return MyClass;
> })();
> ```

Two problems here.

First, the proposed behavior change is not in line with the ECMAScript specification.
There isn't really anything else to be said on that front -- TypeScript must have the same runtime behavior as JavaScript.

Second, the runtime characteristics of this class are very surprising.
Instead of allocating one closure per method, this allocates one closure per method *per instance*.
This expensive in terms of class initialization cost, memory pressure, and GC performance.
 
### You should have some class initialization which is impossible to emit code for
TODO: Port content from [#1617](https://github.com/Microsoft/TypeScript/issues/1617)

-------------------------------------------------------------------------------------

## External Tools

### How do I write unit tests with TypeScript?
TODO: Answer


-------------------------------------------------------------------------------------

## Commandline Behavior


### Why did adding an `import` or `export` modifier break my program?

> I wrote a program:
> ```ts
> /* myApp.ts */
> function doSomething() {
>     console.log('Hello, world!');
> }
> doSomething();
> ```
> 
> I compiled it with `tsc --module commonjs myApp.ts --out app.js` and ran `node app.js` and got the expected output.
> 
> Then I added an `import` to it:
> ```ts
> import fs = require('fs');
> function doSomething() {
>     console.log('Hello, world!');
> }
> doSomething();
> ```
> 
> Or added an `export` to it:
> ```ts
> export function doSomething() {
>     console.log('Hello, world!');
> }
> doSomething();
> ```
> 
> And now nothing happens when I run `app.js`!

Modules -- those files containing top-level `export` or `import` statements -- are always compiled 1:1 with their corresponding js files.
The `--out` option only controls where *script* (non-module) code is emitted.
In this case, you should be running `node myApp.js`, because the *module* `myApp.ts` is always emitted to the file `myApp.js`.  

This behavior has been fixed as of TypeScript 1.8; combining `--out` and `--module` is now an error for CommonJS module output.

### How do I control file ordering in combined output (`--out`) ?
TODO: Answer

### What does the error "Exported variable [name] has or is using private name [name]" mean?
TODO: Port in content from [#6307](https://github.com/Microsoft/TypeScript/issues/6307)


-------------------------------------------------------------------------------------

# Glossary and Terms in this FAQ

### Dogs, Cats, and Animals, Oh My
For some code examples, we'll use a hypothetical type hierarchy:
```ts
       Animal
      /      \
    Dog      Cat
```
That is, all `Dog`s are `Animal`s, all `Cat`s are `Animal`s, but e.g. a function expecting a `Dog` cannot accept an argument of type `Cat`.
If you want to try these examples in the TypeScript Playground, start with this template:
```ts
interface Animal {
  move(): void;
}
interface Dog extends Animal {
  woof: string;
}
interface Cat extends Animal {
  meow: string;
}
```

Other examples will use DOM types like `HTMLElement` and `HTMLDivElement` to highlight concrete real-world implications of certain behaviors.

### "Substitutability"
Many answers relating to the type system make reference to [Substitutability](https://en.wikipedia.org/wiki/Liskov_substitution_principle).
This is a principle that says if an object `X` can be used in place of some object `Y`, then `X` is a *subtype* of `Y`.
We also commonly say that `X` is *assignable to* `Y` (these terms have slightly different meanings in TypeScript, but the difference is not important here).

In other words, if I ask for a `fork`, a `spork` is an acceptable *substitute* because it has the same functions and properties of a `fork` (three prongs and a handle).

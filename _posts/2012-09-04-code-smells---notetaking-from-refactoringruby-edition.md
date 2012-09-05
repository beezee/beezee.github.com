---
layout: post
title: "Code smells   notetaking from Refactoring:Ruby Edition"
category: Development
tags: ['code smells', 'best practices', 'refactoring']
---
{% include JB/setup %}

I'm reading through the Ruby Edition of Kent Beck, Martin Fowler, Shane Harvie and Jay Fields' Refactoring book and loving it.
Took a cue from [Therapeutic Refactoring](https://github.com/kytrinyx/therapeutic-refactoring) and picked up a copy after following
the process this weekend and breezing through a refactor of some code I normally wouldn't even try to read through. It was also the
first time I was able to write a good test suite for code that hadn't been test driven, or at least written to be testable.

The book is phenomenal, and I'm only on Chapter 3, breaking down code smells. Since I'm going to be walking my team through
the therapeutic refactoring process tomorrow, I figure it would be useful for me to extract a quick reference list of the code
smells here (not to mention a good exercise in retaining the info.)

So here's the list of code smells with one liner summary of the fix for each:

<hr />

*   Duplicated Code

Should be self explanatory, extract a class/module, or refer to the duplicated code in one place from the others

*   Long Method

Another self explanatory one, pretty much just extract (a) new method(s). Replace temp with query or create a parameter object
if you're passing a ton of arguments

*   Large Class

Again obvious- personally I like to be able to see 2 to 3 classes expanded in the source viewer on the side of my IDE. Extract a class,
 subclass, or module to fix.
 
*   Long Parameter List

We have a few of these that need attention, you can never call the function without reading the signature first. Create a parameter
object, query other objects for the data from within the method, or pass in a whole object if it contains all or much of the parameter
data.

*   Divergent Change

This means one class has to be frequently changed for a number of different reasons. Extract more classes so each reason for edit
points to a separate class.

*   Shotgun Surgery

This means one change turns into lots of small changes in several classes. Move methods and instance variables to one class so
the initial change only requires editing one class.

*   Feature Envy

This happens when a method is more focused on properties of a different class than its own. Move the method in question to the
class whose data it is focused on.

*   Data Clumps

This means a subset of either instance variables or method parameters repeatedly occur together in groups. For instance variables,
extract a class to house the clumps, for method arguments, create a parameter object or pass in an entire object that contains the
data passed in as arguments.

*   Primitive Obsession

Included for thoroughness - seems to mostly sum up cases where objects provide a more graceful solution than primitives, but
largely appears to be a broader view of several other smells in the list, like long parameter list, data clumps, case statements.
The only unique takeaway I found here is to replace data values with objects on individual data values where appropriate (eg are
currency strings, phone numbers and zip codes.)

*   Case Statements

I'll go the extra step and include any type of conditional statements beyond an early return in here. Extract a method for the
conditional logic, and move it to the class where the property lives that is being checked in the conditional. Then use polymorphism,
module extension, state or strategy in place of the conditional logic.

*   Parallel Inheritance Hierarchies

We haven't run into this yet, but if you have to create multiple subclasses of multiple parent classes to keep things in sync when
making one new subclass, you're having this problem. The solution is to move methods and properties to one hierarchy so the
other disappears.

*   Lazy Class

A class that isn't doing much of anything. Move methods and properties so you can get it out of there.

*   Speculative Generality

Mostly this means overengineering. Collapse unused subclasses, inline unused delegations, remove unused parameters, rename
poorly named methods, and wipe out any code that is only called by tests.

*   Temporary Fields

This happens when there are instance variables that are only used in a minority of methods. In this case extract the properties
and methods that use them to their own class.

*   Message Chains

This happens when you call a method that returns an object on which you call a method which returns an object etc etc to call a
method. Fix this by hiding the delegation within a method on the initially called class. If necessary, extract and move methods
to move it to a logical place on the chain based on the client code.

*   Middle Man

This is a class that delegates most of its work. Either inline the delegated methods to the calling class, or extend the caller with
the target class to remove the middle man.

*   Alternative Classes with Different Interfaces

Rename any methods that do the same thing but have different signatures, and move any methods necessary to balance out the
classes so that they implement the same interface.

*   Incomplete Library Class

Building out functionality that belongs in an exisiting library class. Extend the existing library class when possible.

*   Data Class

This is a class with nothing but properties. Introduce some getters/setters and add visibility declarations to the properties,
encapsulate any collection properties, then extract and move methods from client code to the data class.

*   Refused Bequest

This is a class that only implements a small amount of its inherited functionality. This can typically be ignored, unless a subclass
needs to refuse a public method that is inherited. In these cases, remove the inheritance of the class and delegate to the former
parent instead.

*   Comments

The "deodorant" of code smells, this is usually hiding bad code. If you need to comment a block of code, extract it to another
method with a descriptive name instead, rename the current method, or introduce an assertion to clarify state requirements.

*   Metaprogramming Madness

Abuse of dynamic metaprogramming, like Ruby's method_missing hook, or PHPs \_\_get and \_\_set overloaders. When possible,
extract a method to remove the meta methods.

*   Disjointed API

This is a symptom of using a subset of a library meant to accomodate a variety of needs. Implement a gateway or expression
builder to simplify the API based on what subset is being used.

*   Repetitive Boilerplate

These are methods that are defined in a majority of classes. Define a method which generates the boilerplate methods (class
annotation) and allow classes where it is needed to inherit this method.

<hr />

That gets through the main points of Chapter 3. I'll be using this to review code with my team, and will add a new post when I
get to the refactoring defintions to help me digest and share that as well.



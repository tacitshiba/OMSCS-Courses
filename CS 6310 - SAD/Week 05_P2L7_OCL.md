# Lesson 10

## OCL （Object Constraint Language)

- Official part of UML
- OCL is a strongly typed, declarative specification of system properties, allows you to specify the functional details of system properties
- consists of a means of express constraints + collection classes + UML diagram navigation
- supported by: Rational Rose, ArgoUML, Eclipse, Poseidon/Octopus, Enterprise Architect

## Why Do We Need OCL

We need OCL because UML diagrams are limited in what they can express (structural relationships and behavioral descriptions). OCL extends UML with:

- Class invariants
- Operation pre and post conditions
- Guards on state-machine transitions

## OCL Overview

OCL has the following characteristics:

- Declarative not procedural
- Pure expression language
- No assignment statements or other side effects
- Strongly typed
- Built-in types and includes types introduced in UML diagrams

OCL also includes a high level mechanism known as a **constraint** which is a formal assertion of system properties.

## Uses Of OCL

There are multiple uses of OCL:

- Specify invariants on classes in the class model
- Describe pre and post conditions on operations and methods
- Specify derivation rules for derived attributes
- Describe guards on transitions in state chart diagrams
- Specify targets for messages and actions
- Specify type invariants for stereotypes
- Query language

## Syntax

Here is an example of syntax in OCL: `context <identifier> <constraintType>: <Boolean expression>`

## Invariants

- **Invariants** are statements of a property that is always true:

```
context LargeCompany
inv: numberOfEmployees > 50
```

- express key system requirements
- inv keyword

## Role Of Invariants

- Role of invariants include concept of integrity constraints e.g., properties of the data in the database that describe whether the database is sound.
- OCL invariant constraints play this role for system specifications

## Pre And Post Conditions

Both `pre` and `post` conditions are used to express the meaning of UML operations. A `pre` condition specifies what must be true for the operation to meaningfully take place. A `post` condition specifies what is guaranteed to be true after the operation completes.

## Changes to Attribute Values

Post-conditions can also be used to describe the results of changes in the values of an attribute

```cpp
context Account::deposit(Real : amount)
pre: amount > 0
post: balance = balance@pre + amount
```

## OCL Built In Primitive Types

[OCL also includes built in types](https://www.youtube.com/watch?v=o5Rih1sBEuQ) as well as literals and operations.

Boolean, Integer, Real, String

## OCL Keywords

[There are also keywords we can use in OCL](https://www.youtube.com/watch?v=6_YE18LdtC4). We already have seen `inv`, `pre`, and `post`.

if-then-else-endif

not, or, and, xor, implies

package, enpackage,

context,

def

let, in

derive

init

result

self

## let Clause

- way of introducing an abbreviation into a constraint
- has two parts: both expressions

```python
let income : Integer = self.job.salary -> sum() in
	if isUnemployed then income < 100
									else income >= 100
	endif
```

## Navigation

Recall that OCL constraints are associated with class model diagrams. 

Each constraint specifies a context. 

To refer to features of a non-context class in an OCL invariant, you must use a qualified name

**Navigation** is done by walking through a diagram from the context class to the other class using intermediary relationship lines and class rectangles.

## Navigation: Multiplicity

Associations can be multiplicity (e.g., 1-1, 1-m, n-m). When an association has multiplicity greater than one, the result is a collection rather than an individual object. If an operation is performed, then the `->` symbol is used to separate the collection name from the operation name.

## Collections

OCL features four kinds of collections that support associations with m-m and 1-m multiplicities:

- `Collection` provides features that hold true for all collections
- Collections can also provide specialized operations e.g., `Set`, `Bag`, and `Sequence`

## Summary

OCL gives us the ability to properly specify the properties of our system.

Other OCL Features:

Tuple expression, Enumerations, Message expression, Access to the UML metamodel, Automatic flattening.tuple

## Section Quizzes

### Invariant Constraint Quiz

*See if you can come up with another invariant constraint for the LargeCompany class. Express an invariant that satisfies this requirement for large companies... "A company is considered large if it has a market capitalization of over one million dollars."*

```
context LargeCompany inv:
marketCapitalization > 1000000
```

### Post Condition Quiz

*Say you had a class with two attributes, a and b, both Reals, and you wanted to have an Operations called swap that interchanges their values. See if you can probide a post-condition that expresses this Operation*.

`post a = b@pre and b = a@pre`

### Bank ID Quiz

*For the same diagram with context class Customer, how would you refer to the size of the set of BankIDs that a Customer instance has written checks on for all Orders that the Customer has made*?

`self.Order.Check.bankID --> size()`

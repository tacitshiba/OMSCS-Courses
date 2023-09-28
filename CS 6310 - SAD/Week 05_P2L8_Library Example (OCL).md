# Lesson 11

## Library Exercise

- Analyzed a set of requirements for a library information system
- Expressed the result as a UML class diagram
- Improved the requirements
- Some aspects of the problem that the UML diagram could not addresss
- OCL fill in the gaps

## Limitations

For UML diagrams, either the specification as given by the diagram must be supplemented or an entirely new specification must be introduced.

## Side Effects

**Side effects** specify an even more complex situation - one where an operation actually results in a change of state.

## Observations

We should be open during the process of analysis to the possibility of new requirements arising. This could include further consultation with the customer. A simple set of requirements can have so many issues - this should illustrate the value of constructing an OCL specification.

## Section Quizzes

### Requirements Quiz

*Determine which of the requirements the diagram is able to adequately address with a `+` or cannot address with a `-`*.

- Req 1: -
- Req 2: +
- Req 3: -
- Req 4: -
- Req 5: -
- Req 6: -
- Req 7: -
- Req 8: -
- Req 9: +
- Req 10: -
- Req 11: -

## Requirement 6 Quiz

*Which of the classes in the diagram is most appropriate to associate with Requirement #6 (checking out books)*?

`Book` is the most appropriate class.

UML provides a way to express requirements like this and associate them with elements of diagrams

Object Constraint Language (OCL) is an official part of UML and provides sufficient expressive power

```jsx
**context** Book **inv**:
	**if** bestSeller then
			checkoutPeriod = 2 -- weeks
	**else**
			checkoutPeriod = 3
  **endif**
```

## Explanation

- Each OCL constraint is interpreted in the context of a particular class
- Text expresses a single constraint
- The constraint is an invariant
- OCL keywords are highlighted in bold, and a comment is expressed by appending two dashes and some text
- In the example the context is the Book class
- All unqualified names appearing in the constraint are attributes of the Book class
- Operations and associations may be similarly referenced
- This particular constraint is a conditional

## Operations

- Invariants are one constraint useful for describing properties of attributes that must always hold
- OCL provides a way to specify Operations using pre- and post-condition constraints
- Associated this text with an operation in class Patron called itemsCurrentlyCheckedout
- Specify that the value computed by this operation in fact corresponds to just those items that are checked out for that Patron

```jsx
**context**
	Patron::itemsCurrentlyCheckedOut() :
		Set(LoanableItem)
**post:**
	result = checkedOut.LoanableItem
```

## Limitations

- Either the specification as given by the diagram must be supplemented or an entirely new specification must be introduced

## Checked Out Quiz

*Does the constraint for the checkout period sound more like a class invariant or an operation*?

Sounds more like an invariant.

## Requirement 7 OCL Quiz

*Complete the OCL constraint for Requirement #7 (AV material checkout)*.

- Attribute name: checkOutPeriod
- Operator: =
- Value: 2

## Requirement 4 OCL Quiz

*Complete the OCL constraint for Requirement #4 (children checkout limit)*.

```
context Patron : : checkout (i : LoanableItem)
pre: if age <= 12 then
  itemsCurrentlyCheckedOut() -> size() < 5
```

Note that because this constraint is not a complete specification of checkOut, it contains no postcondition.

## Side Effects

- Specify an even more complex situation - one where an Operation actually results in a change of state
- Choose to model the actual process of checking out a LoanableItem as indicated in requirement #5.

## Requirement 5

- Precondition has 3 conjuncts.
- For the first and second condition, we have invented new Operations, to be defined in class LoanableItem.
- This is similar to what we do when writing a program and want to break up an algorithm into pieces.

```jsx
**context** Patron::checkOut (i: LoanableItem)
**pre:**
	i.isAvailable() **and**
	i.notRequestedBySomeoneElse **(self) and**
	(age <= 12 **implies**
			itemCurrentlyCheckedOut() -> **size**() < 5)
**post:**
	**exists** (c: CheckedOut |
		c.loanableItem = i **and**
		c.dueDate = operatingSystem.getDate() +
			c.loanableItem.checkedoutPeriod **and**
		checkedOut = checkedOut@**pre** -> **including(c)**)
```

- This postcondition has three clauses.
- The first clause (c.loanableItem = i) says that after execution of the CheckOut operation is complete there must exist an instance (c) whose corresponding LoanableItem is the argument of CheckOut (i).

another postcondition is to update the list

```jsx
**context** Patron::checkOut (i : LoanableItem)
**post:**
	**let** t : Title = i.title in
		**if** t.requests.patron -> includes(**self**)
		**then**
			requests = 
			  requests@pre -> reject(title = t **and** patron = **self**)
		**else**
			true
		**endif**
```

## Checkout Preconditions Quiz

*For adults, which of the following is not a precondition for the Patron::checkOut operation*?

The patron has not exceeded checkout limit.

## Derived Data Quiz

*Complete the OCL constraint for Patron's age. Hint: Use the OCL keyword derive*.

`context Patron::age:Date
derive:
  OperatingSystem.getDate() - birthDate`

## Missing Pieces

- Illustrated some uses of OCL to provide precise specification for a simple library information system.
- There are many more things we would need to do to complete this exercise.

## OCL Type

![Untitled](Lesson%2011%20ea5467ab1b634faeb4f411e7ef88de85/Untitled.png)

- Basic Type: Boolean, Integer, Real, String
- Collection Type: Set, Bag, OrderedSet, Sequence
- Collection Operations:
    - Equal (=) or NotEqual (<>)
    - Transform: asBag(), asSet(), asOrderedSet(), asSequence()
    - includding(object) & excluding(object)
    - flatten()
    - Some universal operations: union, intersection, minus, symmetricDifference
    - Sorting (OrderedSet, Sequence) Operations: first(), last(), indexOf()
    - Loop Operations: any, collect, exists, isUnique, one, select, reject, sortedBy

## Examples:

| Constraint | OCL Equivalent |
| --- | --- |
| The age of a person is not negative. | context Person inv: self.age >=0 |
| A person is younger than its parents. | context Person inv: self.parents->forAll(p|p.age>self.age) |
| After a birthday, a person becomes one year older. | context Person::hasBirthday() post: self.age=self.age@pre+1 |
| A Person has 2 parents at max. | context Person inv: self.parents->size()<=2 |
| After somebody has a child, his/her child-set is not empty, and it is larger than before. | context Person::getsChild() post: self.childs->notEmpty() and self.childs->size() > self.childs@pre->size() |
| Only an adult can be owner of a car. | context Person inv: self.age<18 implies self.cars->isEmpty() |
| The first registration of a car can not be before it is built. | context Auto inv: self.registration>=self.constructionYear |
| Every Person that has a car has at least one car which is younger than the Person. | context Person inv: self.cars->notEmpty() implies self.cars->exists( c | Calendar.YEAR - c.constructionYear < self.age) |
| Nobody can be his/her own parent. | context Person inv: self.parents->excludes(self) |
| There's at least one Person which owns a car. | context Person inv: Person.allInstances()->exists(p | p.cars->size() > 0) |
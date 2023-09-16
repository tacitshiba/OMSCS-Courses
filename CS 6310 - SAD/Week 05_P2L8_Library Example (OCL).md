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
- 

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
  itemsCurrentlyCheckedOut() --> size() < 5
```

## Checkout Preconditions Quiz

*For adults, which of the following is not a precondition for the Patron::checkOut operation*?

The patron has not exceeded checkout limit.

## Derived Data Quiz

*Complete the OCL constraint for Patron's age. Hint: Use the OCL keyword derive*.

`context Patron::age:Date
derive:
  OperatingSystem.getDate() - birthDate`
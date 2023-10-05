# Lesson 14

To familiarize ourselves more with software architecture, we will examine a paper by David Parnas and come up with four different architectures that address the same problem. The problem introduced is to design a program that produces a *key word in context* index.

## [Key Word In Context](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2014%20(P3L1)%20-%20KWIC%20Exercise.md#key-word-in-context) (Index System)

The KWIC (Key Word In Context) problem is described as follows:

- KWIC index system accepts as input a sequence of text lines
- A line may be circularly shifted by removing its first word and appending it at the end of the line
- KWIC index system outputs a listing of all circular shifts of all lines

## Shared Data Decomposition

- Break the system into components based on the functions they compute
- All components share access to the data
- Usually contains some form of master-controller routine responsible for invoking the others

## [Pipe And Filter](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2014%20(P3L1)%20-%20KWIC%20Exercise.md#pipe-and-filter)

For pipe and filter:

- Break the system into independently executing components (filters)
- Connect the components together via FIFO queues (pipes)
- Each filter takes a single input (`stdin`) and produces a single output (`stdout`)
- The filters share the assumption that the inputs and output consist of sequential files containing lines of ASCII characters
- Input Medium → Input → Circular Shift → Alphabetizer → Output → Output Medium

## [Abstract Data Types](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2014%20(P3L1)%20-%20KWIC%20Exercise.md#abstract-data-types)

For ADTs (abstract data types):

- Break the system into components based on important data structures
- Hide the representations of the data structures behind abstract interfaces
- The components holding the data structures also provide operations
- ADTs were a precursors to objects in object-oriented languages

## [Implicit Invocation](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2014%20(P3L1)%20-%20KWIC%20Exercise.md#implicit-invocation)

Implicit invocation implies that:

- Communication is coordinated between components using registration-broadcast
- Servers do not know the identities of clients
- The unit of notification is the event

## [Evaluation](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2014%20(P3L1)%20-%20KWIC%20Exercise.md#evaluation)

Below are some advantages and disadvantages of each:

- ADT:
    - Pros: maintainability, reuse
    - Cons: Performance
- Implicit invocation:
    - Pros: enhancements, data representation changes, reuse
    - Cons: difficult to control/think about, inefficient
- Pipe and filter:
    - Pros: intuitive, reuse
    - Cons: interactivity, space efficiency

## [Lessons](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2014%20(P3L1)%20-%20KWIC%20Exercise.md#lessons)

There are a variety of different architectural styles that can be used to solve a design problem. A given style will have advantages and disadvantages depending on the particular requirements changes it must deal with.

## [Section Quizzes](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2014%20(P3L1)%20-%20KWIC%20Exercise.md#section-quizzes)

### [Shared Data Approach Quiz](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2014%20(P3L1)%20-%20KWIC%20Exercise.md#shared-data-approach-quiz)

*Each approach to solving the KWIC problem has advantages and disadvantages . For the following statements choose whether they are advantages or disadvantages of the shared data approach*.

- Data Access Complexity: advantage
- Data Access Speed: advantage
- Resilience to Change: disadvantage

### [Enhancements Quiz](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2014%20(P3L1)%20-%20KWIC%20Exercise.md#enhancements-quiz)

*Assume that you have built the KWIC program, and it has been successfully released. Customers would like to see more enhancements. List at least three ways the tool could be improved*.

1. Return results based on cached/collected data
2. Add some way to get customer feedback because that is what matters most
3. Add some way to recommend - to development team - features that might be useful based on user metrics

### [Reusability Quiz](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2014%20(P3L1)%20-%20KWIC%20Exercise.md#reusability-quiz)

*Which of the four styles do you think would be best able to deal with change regarding reusability of components*?

Pipe and filter

### [Data Change Resilience Quiz](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2014%20(P3L1)%20-%20KWIC%20Exercise.md#data-change-resilience-quiz)

*Which of the four styles would be least able to cope with change having to do with different data representation*?

Shared data

### [Deletion Quiz](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2014%20(P3L1)%20-%20KWIC%20Exercise.md#deletion-quiz)

*Which of the four styles do you think would be best able to deal with change regarding interactive title deletion*?

Abstract data type
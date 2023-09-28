# Lesson 12

Structural models express properties that are always true but fail to convey interesting behavioral aspects of systems. UML provides alternatives for behavior modeling. In this lesson we will look into behavior modeling and state chart diagrams.

## [States](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#states)

**States** are abstract descriptions of system values at a given time. A state space is a set of all possible states and increases multiplicatively.

## [Events](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#events)

**Events** are single, instantaneous, noticeable occurrences.

## [UML Event Taxonomy](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#uml-event-taxonomy)

UML supports the following events:

- Signal (asynchronous notification)
- Method call (synchronous operation invocation)
- State change (continuously monitored)
- Time passage

## [Modeling Techniques](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#modeling-techniques)

Systems that respond to events are called **reactive systems**. Modeling techniques include:

- Combinatorial: states but no events
- Sequential: states, linearly ordered events
- Concurrent: states, unconstrained events

## [Combinatorial Modeling](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#combinatorial-modeling)

**Combinatorial modeling** expresses logic of simple combinatorial systems where only inputs determine subsequent states. Some tools for this type of modeling include:

- Decision trees
- Decision tables

## [Decision Tables](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#decision-tables)

**Decision tables** are useful for determining system outcomes for a given configuration. For decision tables, conditions are called inputs and responses are called outputs.

## [Decision Trees](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#decision-trees)

The graphical form of the decision table is the **decision tree**.

## [Sequential Systems](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#sequential-systems)

**Sequential systems** (also called **finite state systems** or FSM) have memory of previous system activities.

## [State Transition Table (STT)](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#state-transition-table-stt)

**STT (state transition tables)** have rows that correspond to states and contain four columns:

- Name
- Input event
- Output actions
- Next state

## [State Transition Diagrams](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#state-transition-diagrams)

**State transition diagrams** are graphical representation of finite state machines. However, the layout of these diagrams has no semantic import.

## [Problems With State Transition Diagrams](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#problems-with-state-transition-diagrams)

There are several problems with state transition diagrams:

- Too many arrows
- Too many states
- No concept of abstraction/nesting

## [State Charts](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#state-charts)

Improvements to state transition diagrams are included in state charts. State charts are able to address the issue of complexity and is part of UML.

## [State Chart Extensions To FSMs](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#state-chart-extensions-to-fsms)

State charts extents FSMs by offering the following:

- Depth
- Concurrency
- Broadcast events
- Conditional transitions
- Entry/exit action/activities
- Event parameters
- History
- Default states

## [Complete UML Transition Description](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#complete-uml-transition-description)

The complete UML transition description includes:

- Source state
- Target state
- Trigger event
- Guard
- Action
- Forks and joins

## [Relationship To Class Diagram](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#relationship-to-class-diagram)

How does the state chart relate to the class diagram? Each class has attributes and attributes form state space. Each class could have the  ir own state chart but most have simple states. For state charts:

- Attributes are attributes of class
- Actions are methods
- Events appear as signals

## [Summary](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#summary)

Behavioral modeling can be done with state charts. There are other methods we can use as well (shown in slides) but for the purposes of the course, state charts will be effective in representing behavior in our systems.

## [Section Quizzes](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#section-quizzes)

### [Tic Tac Toe Quiz](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#tic-tac-toe-quiz)

*The game of TicTacToe is played on a 3 x 3 grid. Each grid cell can contain an X, an O, or can be empty. In how many different states can a TicTacToe board be*?

3^9 = 19683

### [State Vs. Event Quiz](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#state-vs-event-quiz)

*Which of the following are states, events, or neither? Select the correct option from the drop down next to each of the below*.

- State
- Neither
- Event
- Event
- State
- Event
- Neither
- Event

### [Garage Door Quiz 1](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#garage-door-quiz-1)

*In how many states could the garage door be*?

There are six states total based on the given information:

1. Open
2. Closed
3. Partial open
4. Partial close
5. Opening
6. Closing

### [Garage Door Quiz 2](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#garage-door-quiz-2)

*To how many events does the garage door system respond*?

The system responds to three events based on the given information:

1. Remote trigger
2. Switch up
3. Switch down

### [Harel's Digital Watch Quiz](https://github.com/stevenxchung/OMSCS-Notes/blob/master/CS%206310%20-%20SA%26D/Lesson%2012%20(P2L9)%20-%20Behavior%20Modeling.md#harels-digital-watch-quiz)

*Refer to the given state diagrams in lecture*.

- *How many outermost states does the watch have*? 2
- *What button must be pressed to turn on the alarm-clock feature*? a
- *In the ALIVE state, how many concurrent machines are running*? 5
- *When the c button is pressed to set the time, which part (day, date, hour, minute, or second) is the first one a user can change*? Second
- *If you are changing the time on your watch, and you press the b button to indicate that you are done, what unexpected side effect occurs*? The watch light turns on
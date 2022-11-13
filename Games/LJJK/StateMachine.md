# StateMachine
The StateMachine is the most important component of the engine, while also being one of the simplest. The StateMachine separates seperate tasks into their own bespoke states, and allows for simple pausing, resuming, and swapping between them.

See [[State]].

## Methods

### cleanup
Cleans up all active states and shuts down the State Machine.

### pushStae(state)
First pauses the current active State, if one is active. Then pushes the provided State `state` onto the stack. The provided State will become active after the current `update` function has finished execution, not necessarily immediately after this function is called. In most cases, steps should be taken to ensure the active State's update function does not continue execution following this call, as data saved during the active State's pause function may be overriden, and data expected by the active State's update function may become undefined, causing memory exceptions.

### popState
Cleans up and removes the current active State from the stack. If there are States beneath the current active State, the most recent one will be resumed.

### changeState(state)
Cleans up and removes the current state, and then initialises and activates the provided State `state`.

Internally calls `popState` and then `pushState(state)`.

### update(deltaTime)
Updates the current active state, if there is one.

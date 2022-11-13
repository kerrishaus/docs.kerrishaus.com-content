# State
A State handled by the [[StateMachine]].

## Methods

### init(stateMachine)
Initialises the State and sets the internal `stateMachine` member to the provided `stateMachine`.

This method is usually overriden by extending States, but it is important to call `super.init(stateMachine)` to ensure the State is properly initialised.

### cleanup
This method cleans up the State. By default, this method does nothing because JavaScript handles memory deallocation and what not for us. This method can be used to clean up, transfer, or save data that is required to persist outside of a given state. 

For example, [[LoadingState]] will save all loaded assets to the window variable for use by other States within this method.

### pause
Runs necessary code when a State is paused by the StateMachine.

### resume
Runs necessary code when a State is resumed by the StateMachine.

### update(deltaTime)
Called every frame by the StateMachine.
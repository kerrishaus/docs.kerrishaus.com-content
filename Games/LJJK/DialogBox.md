# DialogBox

`DialogBox` is the component used to create on screen DialogBoxes, with which the user can interact. `DialogBox` uses a div pre-created that lives inside the `.interface-container` element. When a new `DialogBox` is created, shown, or hidden, the content contained in the `.dialog-box` element is reset and replaced with the new content.

## Methods

### `constructor(message, printSpeed = 50, printDelay = 400)`
`message` message  
`printSpeed` default is 50.  
`printDelay` default is 400.  

### `presentDialog`
Moves the dialog box on screen.

### `hideDialog`
Moves the dialog box off screen.
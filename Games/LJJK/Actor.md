# Actor
The Actor class represents characters, player or non-player.

## Configuration
`spriteUpdateTime` represents the time in seconds between sprite changes.

## Methods

### addSpriteSheet(name, frames)
`name` is the filename of the sprite, location in `textures/sprites/`.
`frames` is the number of frames in the sheet.

### removeSpriteSheet(name)
`name` is the name of the sprite as loaded previously.

### setSpriteSheet(name)
This will set the current spritesheet, provided it is already loaded.

`name` is the name of the sprite as loaded previously.
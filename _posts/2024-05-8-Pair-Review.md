---
toc: true
comments: false
layout: post
title: Pair Review
description:  
type: devops
courses: { csse: {week: 15} }
---
## Finite State Machines 
As we continue to create our level, Finite State Machines are prevelant in our Harry Potter sprite. Now that the player code has been restructured, we should be switching our player to use PlayerBase by changing it's class from Player to PlayerQuidditch. 
``` js
{ name: 'harry', id: 'player', class: PlayerQuidditch, data: this.assets.players.harry }
```
Even though this was a quick fix, I somehow broke our team level. After using inspect and looking at the console, it tells me that there's issues with animation. 
The problem with this is that the PlayerBase updates the aniation based off of the Mario sprite but obviously our Harry sprite isn't made to have the same frames as Mario. So, we just state the frames for each state of Harry, which ended up fixing our problem!
``` js
harry: {
        src: "/images/platformer/sprites/harryanimation3.png",
        width: 32,
        height: 32,
        scaleSize: 60,
        speedRatio: 0.7,
        idle: {
          left: { row: 1, frames: 1 },
          right: { row: 2, frames: 1 },
        },
        walk: {
          left: { row: 1, frames: 5 },
          right: { row: 2, frames: 5 },
        },
        run: {
          left: { row: 1, frames: 5 },
          right: { row: 2, frames: 5 },
        },
        jump: {
          left: { row: 1, frames: 1 },
          right: { row: 2, frames: 1 },
        },
        hitbox: { widthPercentage: 0.3, heightPercentage: 0.8 }
      },
```

##  Single Responsibility Principle
As we progress in making our team level, we have to change our dementor enemy since it originally follows the FlyingGoomba code but with a dementor image. This doesn't really work since we're not using a FlyingGoomba for our level so we shouldn't have that reflected in our code. When creating the Dementor.js based off of of FlyingGoomba, I see that it exemplifies the SRP. 

``` js
update() {
        super.update();

        if (this.x <= this.minPosition || (this.x + this.canvasWidth >= this.maxPosition) || this.x > (GameEnv.innerWidth - 100) ) {
            this.speed = -this.speed;
        }

        if (this.speed < 0) {
            this.canvas.style.transform = 'scaleX(1)';
        } else {
            this.canvas.style.transform = 'scaleX(-1)';
        }
```
I believe that it resembles the character update:
``` js
update() {
    // Update the y position of the character based on gravity
    this.updateY();
    // Update animation frameX of the object
    this.updateFrameX(); 
    // Check for collisions, defined in GameObject which calls the collisionAction method
    this.collisionChecks();
}
```
except in the FlyingGoomba example, it's updating the speed and scale of the x positioning in the game. It's single responsibility is that it updates the FlyingGoomba based on it's position so that once it reaches the end so that it transforms and turns around. 

## Objects in JavaScript
The following line is listed in GameSetup.js before every teams level, to list out the objects for that level. This makes it an object that holds multiple objects. 
``` js
// Quidditch Game Level definition...
    const quidditchGameObjects = [
      // GameObject(s), the order is important to z-index...
      { name: 'quidditch', id: 'background', class: Background, data: this.assets.backgrounds.quidditch },
```
``` js
{ name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.536, yPercentage: 0.72 },
```
For listing out multiple objects under the TeamObjects, it utilizes the dot property for example this.assets.platforms.cobblestones which accesses the cobblestone object from the platforms objects that is under the assets objects. So when I want to add a new object to the Quidditch level, I have to follow that same idea. To make a tower, I have to go GameSetup.js, then go to the platforms under assets to state the name of the object I want and what image I want it for. 

``` js
platforms: {
      yellowpattern: { src: "/images/platformer/platforms/yellowtowerpattern.jpg" },
```
now that the object is in assets, I can add it to the game level definition list for the Quidditch level
``` js
{ name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.yellowpattern, xPercentage: 0.456, yPercentage: 1.08 },
```
Here, I'm putting in a block that is jumpplatform that is made from the code BlockPlatform.js, which is a yellowpattern platform object from assets. 
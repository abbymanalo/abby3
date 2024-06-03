---
toc: true
comments: false
layout: post
title: College Articulation 
description:  
type: devops
courses: { csse: {week: 16} }
---
# Game Control
This is a snippet of the Java Script Objects for our Quidditch level. Each object has properties that organize each object. For example, the background object is **named** quidditch, is under the **class** background, and its **data** comes from the background asset quidditch. 
``` js
    // Quidditch Game Level definition...
    const quidditchGameObjects = [
      // GameObject(s), the order is important to z-index...
      { name: 'quidditch', id: 'background', class: Background, data: this.assets.backgrounds.quidditch },
      { name: 'turf', id: 'platform', class: Platform, data: this.assets.platforms.turf },
      { name: 'clouds', id: 'background', class: BackgroundClouds, data:this.assets.backgrounds.clouds }, 
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.1, yPercentage: 0.81 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.14, yPercentage: 0.81 },
      
```
At the end of this piece, it adds our objects to the Game Enviornment and creates a new level.
``` js
    // Quidditch Game Level added to the GameEnv ...
    new GameLevel({ tag: "quidditch", callback: this.playerOffScreenCallBack, objects: quidditchGameObjects });
```
Now in GameLevel.js, this takes the objects from each object listing and creates a level and adds it to the Game Enviornment
``` js
class GameLevel {
    /**
     * Creates a new GameLevel.
     * @param {Object} levelObject - An object containing the properties for the level.
     */
    constructor(levelObject) {
        // The levelObjects property stores the levelObject parameter.
        this.levelObjects = levelObject;        
        // The tag is a friendly name used to identify the level.
        this.tag = levelObject?.tag;
        // The passive property determines if the level is passive (i.e., not playable).
        this.passive = levelObject?.passive;
        // The isComplete property is a function that determines if the level is complete.
        // build conditions to make determination of complete (e.g., all enemies defeated, player reached the end of the screen, etc.)
        this.isComplete = levelObject?.callback;
        // The gameObjects property is an array of the game objects for this level.
        this.gameObjects = this.levelObjects?.objects || [];
        // Each GameLevel instance is stored in the GameEnv.levels array.
        GameEnv.levels.push(this);
    }
```
In GameControl.js, this transitions to the next level after the current level is complete. 
``` js

    /**
     * Transitions to a new level. Destroys the current level and loads the new level.
     * @param {Object} newLevel - The new level to transition to.
     */
    async transitionToLevel(newLevel) {
        this.inTransition = true;

        // Destroy existing game objects
        GameEnv.destroy();

        // Load GameLevel objects
        if (GameEnv.currentLevel !== newLevel) {
            GameEnv.claimedCoinIds = [];
        }
        await newLevel.load();
        GameEnv.currentLevel = newLevel;

        // Update invert property
        GameEnv.setInvert();
        
        // Trigger a resize to redraw canvas elements
        window.dispatchEvent(new Event('resize'));

        this.inTransition = false;
    },
```
This next piece loops the entire game 
``` js
  gameLoop() {
        // Turn game loop off during transitions
        if (!this.inTransition) {

            // Get current level
            GameEnv.update();
            const currentLevel = GameEnv.currentLevel;

            // currentLevel is defined
            if (currentLevel) {
                // run the isComplete callback function
                if (currentLevel.isComplete && currentLevel.isComplete()) {
                    const currentIndex = GameEnv.levels.indexOf(currentLevel);
                    // next index is in bounds
                    if (currentIndex !== -1 && currentIndex + 1 < GameEnv.levels.length) {
                        // transition to the next level
                        this.transitionToLevel(GameEnv.levels[currentIndex + 1]);
                    } 
                }
            // currentLevel is null, (ie start or restart game)
            } else {
                // transition to beginning of game
                this.transitionToLevel(GameEnv.levels[0]);
            }
        }

        // recycle gameLoop, aka recursion
        requestAnimationFrame(this.gameLoop.bind(this));  
    },
};
```
This gets the game level as long as its not transitioning between levels. It also moves to the next level once the current one is complete or starts the entire game from the beginning. 
# Class Design, Draw.io
I chose to create my diagram based on our mini level, Hogwarts since that is the level I created on behalf of my team and worked most on. 
![diagram]({{site.baseurl}}/images/diagram.png)

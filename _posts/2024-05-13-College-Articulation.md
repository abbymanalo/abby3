---
toc: true
comments: false
layout: post
title: College Articulation 
description:  
type: devops
courses: { csse: {week: 16} }
---
## Game Control Code
These are the Java Script Objects for our Quidditch level:
``` js
    // Quidditch Game Level definition...
    const quidditchGameObjects = [
      // GameObject(s), the order is important to z-index...
      { name: 'quidditch', id: 'background', class: Background, data: this.assets.backgrounds.quidditch },
      { name: 'turf', id: 'platform', class: Platform, data: this.assets.platforms.turf },
      { name: 'clouds', id: 'background', class: BackgroundClouds, data:this.assets.backgrounds.clouds }, 
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.1, yPercentage: 0.81 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.14, yPercentage: 0.81 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.18, yPercentage: 0.81 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.22, yPercentage: 0.81 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.22, yPercentage: 0.69 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.30, yPercentage: 0.81 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.30, yPercentage: 0.71 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.30, yPercentage: 0.61 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.30, yPercentage: 0.33 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.30, yPercentage: 0.23 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.30, yPercentage: 0.13 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.34, yPercentage: 0.81 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.38, yPercentage: 0.81 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.42, yPercentage: 0.81 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.38, yPercentage: 0.57 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.38, yPercentage: 0.47 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.38, yPercentage: 0.37 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.38, yPercentage: 0.27 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.38, yPercentage: 0.17 },

      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.536, yPercentage: 0.72 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.616, yPercentage: 0.81 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.cobblestone, xPercentage: 0.696, yPercentage: 0.90 },

      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.yellowpattern, xPercentage: 0.456, yPercentage: 1.08 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.yellowredpattern, xPercentage: 0.456, yPercentage: 0.985 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.yellowpattern, xPercentage: 0.456, yPercentage: 0.89 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.lionpattern, xPercentage: 0.456, yPercentage: 0.795 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.yellowpattern, xPercentage: 0.456, yPercentage: 0.7 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.yellowredpattern, xPercentage: 0.456, yPercentage: 0.605 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.yellowpattern, xPercentage: 0.456, yPercentage: 0.51 },
      { name: 'blocks', id: 'jumpPlatform', class: BlockPlatform, data: this.assets.platforms.lionpattern, xPercentage: 0.456, yPercentage: 0.415 },

      { name: 'draco', id: 'draco', class: Draco, data: this.assets.enemies.draco, xPercentage: 0.3, minPosition: 0.05, difficulties: ["normal", "hard", "impossible"] },
      { name: 'draco', id: 'draco', class: Draco, data: this.assets.enemies.draco, xPercentage: 0.5, minPosition: 0.3, difficulties: ["normal", "hard", "impossible"] },
      { name: 'draco', id: 'draco', class: Draco, data: this.assets.enemies.draco, xPercentage: 0.75, minPosition: 0.5, difficulties: ["normal", "hard", "impossible"] }, //this special name is used for random event 2 to make sure that only one of the Goombas ends the random event
      { name: 'dementor', id: 'dementor', class: Dementor, data: this.assets.enemies.dementor, xPercentage: 0.5, minPosition: 0.05 },
      { name: 'dementor', id: 'dementor', class: Dementor, data: this.assets.enemies.dementor, xPercentage: 0.9, minPosition: 0.5 },

      { name: 'coin', id: 'coin', class: Coin, data: this.assets.obstacles.snitch, xPercentage: 0.095, yPercentage: 0.7 },
      { name: 'coin', id: 'coin', class: Coin, data: this.assets.obstacles.snitch, xPercentage: 0.135, yPercentage: 0.7 },
      { name: 'coin', id: 'coin', class: Coin, data: this.assets.obstacles.snitch, xPercentage: 0.175, yPercentage: 0.7 },
      { name: 'coin', id: 'coin', class: Coin, data: this.assets.obstacles.snitch, xPercentage: 0.375, yPercentage: 0.7 },
      { name: 'coin', id: 'coin', class: Coin, data: this.assets.obstacles.snitch, xPercentage: 0.409, yPercentage: 0.7 },
      { name: 'coin', id: 'coin', class: Coin, data: this.assets.obstacles.snitch, xPercentage: 0.295, yPercentage: 0.46 },

      { name: 'coin', id: 'coin', class: Coin, data: this.assets.obstacles.snitch, xPercentage: 0.687, yPercentage: 0.79, },
      { name: 'coin', id: 'coin', class: Coin, data: this.assets.obstacles.snitch, xPercentage: 0.611, yPercentage: 0.7 },
      { name: 'coin', id: 'coin', class: Coin, data: this.assets.obstacles.snitch, xPercentage: 0.529, yPercentage: 0.61 },

      { name: 'harry', id: 'player', class: PlayerQuidditch, data: this.assets.players.harry },
      { name: 'tube', id: 'tube', class: Tube, data: this.assets.obstacles.tube },
      { name: 'waterEnd', id: 'background', class: BackgroundTransitions,  data: this.assets.transitions.waterEnd },
    ];
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
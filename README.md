# Hunted
#### Video Demo: 
#### Description:

Hunted is a survival auto-shooter game. You play as a Wizard/Witch marked by night creatures are the prey of the hunt. Waves of enemies will spawn with a variety of enemy types. Evade their attacks, while firing magic orbs at the nearest target. You must fight off the waves and be the first survivor among the hunted.


###### Controls
W A S D - Movement keys

Shooting is automatic as well as the aiming. You must focus on skillfully dodging enemies and their attacks.


##### Folders and Files

###### main.lua
Where it starts from. Initializes global variables, imports and preloads a tile texture, 1 song and 2 sound effects. Update function and draw function calls the respective functions of the state

###### conf.lua
Configures the game window title, icon and fullscreen (set to true)

###### classic.lua
A free software module used to add Object oriented aspects to Love2d. 

Link to source: https://github.com/rxi/classic.git

###### state.lua
Manages the current state of the game between the Main menu, game and the gameover screen (win or loss). When the update and draw functions are called, it calls the same function for the current state.


###### states (Folder)
A folder containing the 3 states + a utility lua for text display

###### ++++states++++

###### menuState.lua
The state for the games main menu. Feature a title and 2 buttons for starting or quitting the game.

###### gameState.lua
The state for the game itself. On update, it updates all entities including the players. On draw, it draws the entity auras, entity sprites and then the UI of the game, featuring health indicator in the top left and wave counter at the top middle.

When the game is reset, all game related data is reset to default values

###### overState.lua
The state for when the gameover screen is to be displayed. Will win/loss text and statistics of waves survived and enemies killed

###### text.lua
A utility lua for displaying text on the screen

###### ----states----


###### level.lua
Manages the spawn list for all 10 waves. function copyTable maintains a copy of the original level list, as the original is modified by removing rosters as the level progressed. On reseting of the gameState, the copy is applied to the original, reseting the spawn list.

###### entities (Folder)
Contains ai, entityTypes, the entity.lua utility, player lua and the npc and bullet blueprint luas

###### ++++entities++++

###### entity.lua
Contains functions that perform operations on entity variables when called, as well as making calculations and performing actions. It is modelled to as to allow both the player and npc luas to use the same functions.

###### npc.lua
The blueprint lua for all npcs in the game. Each npc will have its value initialised from the npcTypes. Unique npc behaviour is handled by ai luas. This one class allows the creation of any number of unique npcs types without having to repeat the code in this lua

###### bullet.lua
The same concept as npc.lua, however designed to cater to bullets.

###### player.lua
All variables are the same as npc.lua, however control is given to the player instead of an ai, and function Player:aim() chooses the nearest npc to target. These two differences are why I chose to keep a seperate lua for the player.

###### entityTypes (Folder)
Contains luas that store the data tables of the different npc and bullet types.

###### ++++entityTypes++++

###### npcTypes.lua
Table of all npc types. It stores the name, stats and ai of each npc. When a particular table is fed into the npc blueprint, its value are copied to the npc, turning the blueprint into that particular npc.

###### bulletTypes.lua
Table of all bullet types. Similarly to npcType.lua, it stores the data of each bullet type. When a particular table is fed into the bullet blueprint, its value are copied to the bullet, turning the blueprint into that particular bullet.

###### ----entityTypes----

###### ai (Folder)
Contains the ai.lua and different ais for each npcType

###### ++++ai++++

###### ai.lua
The ai class and contains utility functions that allow the different ais to perform actions like moving towards the player, without repeating the code for each ai

###### stalk.lua
AI for eyeball npc. Makes the npc move towards the player wherever they go.

###### shooter.lua
AI for ranger npc. Makes the npc move towards the player and when in range, shoots at them

###### joust.lua
AI for jouster npc. Makes the npc move towards the player and when in range, charges them

###### teleport.lua
AI for teleporter npc. Makes the npc move towards the player. If the player moves to far away from the npc, the npc teleports closer to the player.

###### bulletBoss.lua
AI for the bulletBoss final boss npc. Makes the npc move towards the player and when in range, fires a bullet hell attack in all directions.

###### ----ai----

###### ----entities----

###### libraries (Folder)
Contains luas which contain the imports of the different ai luas and entities luas. Makes the main.lua imports less lenghty

This includes:
AILibrary.lua - Import of all luas in the ai folder
entityLibrary.lua - Import of all luas in the entities folder, except the ai folder

###### res (Folder)
All resources used by the game

###### ++++res++++

###### images (Folder)
All image resources used. All images were made by me, using the software GIMP

###### music (Folder)
All audio resources used. All audio was made using Bosca Ceoil

###### ----res----

###### Runnable exe of Hunted:
This is a readymade executable of Hunted. Clicking on Hunted.exe will open the game. Other files in the same folder are needed to run the game. These are the dll files to run Love2d games. DO NOT DELETE!


#### Certain design choices
##### Language to use
I think the most basic and important of all, I was debating between Java, a language I am experienced enough to make a game with, or to use lua through Love2d, a completely new language I will have to learn up before then proceeding to make a game with. I ended up choosing lua, because I currently face problems trying to get Java to load resources such as images and sounds from directories within the same folder as the program execution. Even though I would have to completely learn up a new language, Love2d handled this in lua for me. I considered this worth the extra work and chose lua in the end.

The tutorial provided by Sheepolution was fantastic for this: https://sheepolution.com/learn/book/contents

##### An lua for each npc vs blueprint method
At the beginning of the project, I was intending to make an individual lua for each npc. However on making my second npc, I realised that this was not going to scale well and adding changes would become tedious and the risk of missing out was high. So I decided to follow the blueprint system. I made a copy of the whole project and kept it elsewhere, incase I decided to scrap the idea and tried to get the atleast one npc working on this.
Under this system, there is **technically** only *one* npc type. And each unique "npcType" is actually just the same npc given different stats, ai and a sprite image. But once I implemented it, I could make as many npcs I wanted with relatively few lines of code.
This is not my first time doing this, so I had some confidence in this decision. But ofcourse as mentioned, I kept a copy of the project incase I face problems unique to lua.

##### Auto-shoot and aim vs manual attacks
While manual attacks make the game more engaging, this was a slight disadvantage for laptop users who don't have a mouse to use (my bluetooth mouse needs frequent charging). So as both a personal and user-friendly choice, I made the aiming and firing of player attacks automated. So whether or not you have the privilege of a USB/fully charged mouse, it will not impact playability.

##### Free assets vs self-made assets
While Free assets provided online are certainly good in quality and quantity, I decided to make everything myself. This choice was motivated by me not being sure if using other peoples assets is allowed and also because this is my first game and I want it to be my own. It was enjoyable and added to the pride I felt for my end product.

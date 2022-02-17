# Ping-Pong
2D ping pong game in unity using C#.
UNITY:
For a ping-pong game we need very few things:-
1-You have a Background to play on
2-You have a set of Paddles that go up and down
3-You have a ball that bounces off walls and paddles
4-You have a set of side walls that you hit to score
5-You have a score at which you win
6-You have a reset button so you can play again
The very 0th step is that we will need to set the UNITY game engine.Create the project with unchecking the “UNITY analytics” off.Drag all the asset files which is in other zipped file attached outside this folder to the project pane which is at the bottom of the project window.Now we have all the assets ready to begin with.

Step 1:(Setting background and main camera)
	Now we will be making a background.Click and drag the background file from the project pane to the hierarchy pane just below  the main camera  button.Now we adjust the background image so for that we will go to inspector button on the right.This inspector tab will be our very best friend for this project.So adjusting the background image,we will put the transform position to (0.75,0.75,1)(by this the background will be nicely centered).
	Now below the transform section,in sprite renderer there we see a Sorting layer button.We will add a new sorting layer.Making a new sorting layer and naming it background(we want our background to be at the back,not with other objects which will be at the default).
	The main camera button on the hierarchy tab,it shows how the user will see the screen on the main output.We will set the camera well.So click on the camera button and move to the inspector tab.In the inspector tab we will change the camera SIZE to 3.Now in the background button we will put the color to black with RGBA values to 0.This background feature makes a border at the screen if our background image isnt big enough to fit the screen.

Step 2:(Setting the paddles)
	Now we will be dragging the paddle’s images from project pane to hierarchy pane and click on that to open inspector tab.We will rename the paddle as Paddle1 and change the tag to player(it gives a tag that it will be treated as player because player uses it which will be importantly considered in our further programs).Now putting the position to (-4,0,0) and scale to (0.5,1.5,1).
	now ,we will add more components and add 2 new  components and go to physics2d,Rigidbody2d to make our paddle move and Boxcollider2d to bounce back the ball when hit on the paddle.Unity has a great, realistic physics system built in that calculates the effects of gravity, friction, and other forces on any object that has a Rigidbody 2D component. That system is often very handy, but we don’t want to use it for our paddles. Our paddles aren’t exactly realistic – they’re just kind of floating in space and they only move when we tell them to. Thankfully Unity gives us a way to tell our Rigidbody 2D to only move when we tell it to. We just have to click the Body type dropdown menu and select Kinematics.
Now we want our paddle to move as we want.Starting with writing the script,go to add component of paddle1 inspector tab > new script and name it PlayerControls.Now click on the file and start coding.
	Coding part is attached in the folder beside.VS code worked while making this.After that we will check if everything is fine.We will click the play button and check wheter its running all fine or not.
	Now,click on the Paddle1 of hierarchy pane and right click.DUplicate it and change its name to Paddle2.Now click on the duplicated Paddle2 and make its position to (4,0,0) in the inspector tab.And edit the key bindings accordingly for the second paddle.

Step:3(Setting up the ball)
 Ball has more work to do as it wont just move around the screen but it will decide the score when it goes to a certain part of the screen.
Now click and drag the ball image from the asset pane to the hierarchy pane and click on it and move to inspector pane.Now go to tag and click the add tag button and name it Ball.Then click on tag and select the Ball tag we just added.THen change the scale to (0.5,0.5,1).We want our ball to be physical so we will go to add component and in Physics2d we will add circle collider 2d and rigidbody 2d .In circle collider we will put the radius to 0.23.
Select the BallBounce Material from the Project pane and look at the Inspector. You’ll see the friction value is 0, and the bounce factor is 1. That way our ball doesn’t experience friction from anything, including our paddles and wall. The bounciness factor means that it also doesn’t lose any speed. It bounces back with the exact same speed it hit the object with.
To apply the material, select Ball in the Inspector, then click and drag the BallBounce material to the Circle Collider 2D box. We also need to adjust several settings in Rigidbody 2D so we can get our desired ball behavior. It should look like this at the end:
Now to begin with coding,add component and add script.The coding part for ball is attached to previous files along with player control file.
	We will set the ball according to our will like I like the ball to be free of gravity so that as the paddles can fly,the ball shall also be free to fly.And i also increase the ball bounce factor so that the game feels fast and fun.
 
Step:4(Setting up the wall)
	You may have noticed by now that your ball can fly off the screen. We need to make some walls.
Let’s first make a game object to contain our walls. Make sure nothing is selected in the Hierarchy pane, then right click some empty space in the Hierarchy and choose Create Empty. It will create a plain ol’ empty game object, which we will name Walls. We don’t need to change anything except to make sure that it has a position of (0,0,0).
Now to make an actual wall. In the Hierarchy pane, right click on the Walls object we just made and choose Create Empty. This will make a new game object that is a “child” of the Walls object. For our purposes, having our walls as children of ‘Walls’ will help us keep the hierarchy nice and clear, since we can click the little arrow next to Walls whenever we don’t want to see each individual wall object. The idea of ‘child’ game objects is actually very powerful and does more than just organize things, but we won’t go into it much in this tutorial.
Anyway, call this new child object RightWall. Also make sure you go to Add Component and add a Box Collider 2D. That way the ball will bounce off of the wall object, just like we want!
Now duplicate our new wall object 3 times. Call those duplicates LeftWall, TopWall, and BottomWall. Now we need to move and size those walls so they are in the right spot in our game view - right now, they’re just points sitting in the middle of our board. We need to make them look like walls.
For the RightWall, set its Position to (5.8, 0, 0) and its Scale to (1, 6, 1). This will make it nice and tall. The LeftWall is the same, except its X Position is -5.8. (The numbers might be different on your computer – basically, just make sure your screen looks like the screenshot below, with the walls on the outside edges of each side of the camera view.)
TopWall should be positioned at (0, 3.5, 0) with a scale of (10.7, 1, 1), and BottomWall has the same scale but with a Y Position of -3.5. If you click on the parent ‘Walls’ object, you should now see this in the Scene view:
 
Step 5:Setting the Scoring Interface(Score board)
	We will need a scoreboard so for that on the hierarchy pane,right click and choose Create Empty and we name it HUD(Head Ups Display).So let its current position be (0,0,0) and we will go to inspector menu and Add component and then New script,we name it GameManager.
	The coding part is attached along with the previous files.
Ok cool. Looking at the HUD, we now see there’s one new variable under this script that needs filling. It’s asking for a ‘Skin.’ We need to make that in Unity. If you look in your Assets folder, you should see a file that we downloaded that is a special font called ‘6809 Chargen’.
In your Project pane, right-click and create a GUI Skin called ScoreSkin. Click on that Skin, and you should see a variable field called ‘Font’ at the top of the Inspector pane. Click + drag our font to that variable slot.(Basically setting the font style).
 
Step 6:Setting the walls so that the game knows when we score
Cool. Now let’s make sure that the game knows when we do score. To do that, we need to add a script to the LeftWall and RightWall objects under the HUD dropdown. It’s the same script so it should be pretty easy to do. First, we’ll go to Add Component > New Script on the LeftWall, and name this new script SideWalls.(attached with previous files).
You already added the script to LeftWall, and now, since it’s written, go to Add Component > Scripts on RightWall. Choose the Script we just wrote. Here’s the completed script: SideWalls.cs.
Now, in order for Unity to call our OnTriggerEnter2D method, we have to make sure both the LeftWall and RightWall have the Is Trigger checkbox selected on their Box Colliders in the Inspector pane. This means that Unity won’t treat these walls as physical walls, but rather they “trigger” something in the game (in this case, they give a player a point).
	
Step 6:Building the game
Go to Build Settings and then choose Mac, PC, Linux Standalone. This will make an executable (playable) file appear on our desktop. You may need to Add Open Scenes, to ensure that Main is included in the build.
Now, click on Player Settings. This is where you should put your name on the Project, choose an icon (I chose the Ball sprite), and uncheck Default Is Full Screen. It asks for a default screen width and height. I chose 960x540 but it really doesn’t matter too much. The important thing is in the Supported Aspect Ratios list. Click the little arrow and uncheck everything except 16:10 and 16:9. If we choose a different aspect ratio, it’s possible we might not see our paddles. Your settings in the end should look like this:
Now, hit Build and choose where you want to save the file (I chose the desktop), and name it something (I named it Pong v1.0). Look at your desktop.
Now go game on.

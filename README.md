
Created by: http://infiSTAR.de  Credits to infistar for the actual script
		Edited by FragZ
		Re-Edited By TheDuke™ for different effects


Ok so here is my version of Smoke Hemp for Epoch 1.0.6.1

- When you right click on a kilo of hemp, you can smoke it. It will fully heal you, and give you the munchies a bit.
You will get a 60 second blur effect, but the effect is medium. And you can still move around, partially see and shoot.
The idea was to be able to heal while doing a mission, but kinda have a bit of effects to make it somewhat like real life LOL

- You can also smoke at hookas on the map, or the ones used in the gem crafting.
While looking at the hooka you get the option to "smoke pipe".
This one does the normal effect of rolling on the ground with the massive screen blur. Meant to be done at base ;)

Download from the github

Place the smokeweed folder in your customs folder. If you dont have one create one.

Open your custom fn_selfactions.sqf

Place this at the bottom

//Smoke Bong
	_isbong = typeOf cursorTarget in ["Land_Water_pipe_EP1"];	
if((_isbong) && _canDo) then {
                if (s_player_pipe < 0) then {
                s_player_pipe = player addAction["Smoke Pipe", "custom\smokeweed\pipesmoke.sqf","", 1, true, true, "", ""];
    };
        } else {
    player removeAction s_player_pipe;
    s_player_pipe = -1;
        };
	
Still in the fn_selfactions look for

player removeAction s_player_manageDoor;
    s_player_manageDoor = -1;

add this bellow

player removeAction s_player_pipe;
    s_player_pipe = -1;
		
save and close

Open your extra_rc.sqf and add this

class ItemKiloHemp {
        class smokeweed {
            text = "Smoke the shit";
            script = "execVM 'custom\smokeweed\smokeweed.sqf'";
        };
    };
	
save and close

Open your description.extra_rc

Add this in your CfgSounds

	class cough
	{
	name="cough";
	sound[]={custom\smokeweed\cough.ogg,0.9,1};
	titles[] = {};
	};
	 
	class bong
	{
	name="bong";
	sound[]={custom\smokeweed\bong.ogg,0.9,1};
	titles[] = {};
	};	
	
Save and close

Repack your mission and you're good to go!

Enjoy...not too much ;)

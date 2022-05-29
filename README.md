# LinnLights
A Programme for setting Lights on a LinnStrument (An expressive midi controller designed and produced by Roger Linn)

Purpose
This HTML/javascript "page" is a tool to aid setting the lights on a LinnStrument.
It is primarily designed to set the lights for a 'scale', where a 'scale' is a collection of Large and Small steps

The page displays the pattern as it will appear on your LinnStrument
The page puts midi messages in a text box in a format that is designed for use with Geert Bevin's sendmidi <include link>
The page does *not* tune your LinnStrument. The idea is that you would use this in conjunction with a synth that is capable of using microtunings.

A LinnStrument has the capability to fully programme the lights, but this is focussed on scales, a repeating pattern of light colours to aid orientation when using microtunings, but it can work with any scale of more or less than 12 notes. Because this page does not tune your instrument, what the 'scale light pattern' means to the user is entirely dependent on what tuning you use. 
  
You can also use the page to programme a custom 12-note pattern (for example, set an octatonic scale to green lights with the others off, or a different colour for each note etc.)
  
A Quick note on scales and this tool
This tool was designed primarily with MOS Scales in mind (google Erv Wilson and MOS scales for more info). These scales have a patterned structure which resembles the diatonic and pentatonic scales in that only two step sizes are present, one of which is larger than the other. In this tool one is labelled L and the other S.

For the plain diatonic scale this pattern is LLsLLLs, where L is the step of a tone and s is the step of a semitone. For the pentatonic scale this pattern is sLssL, where the s step is 2 semitones and the L step is 3 semitones.
  
The tool accepts any scale form containing the scale steps s and L, so it's possible to make a scale which is not an MOS but contains only L and s steps, e.g. LsLLssLss.  

  
How to use.

1. Load the html into a browser
2. Select your linnstrument from the dropdown
3. choose which user memory you want the pattern stored in
4. Select which offset you want. This can be set anywhere in the full range of the LinnStrument Offsets from -16 to 16. The default setting is 5.
5. Enter the scale pattern you want. (The default is the initial 12-tone pattern on the LinnStrument with the 'white notes' set to green lights and the 'black notes' set to off.)
6. Select the size of the L (Large) Step - the box accepts integer values.
7. Select the size of s (small) step - the box accepts integer values.
8. The drop down 'Choose the colour of the first scale note' allows you to choose a different colour for the starting note of the scale.
9. Clicking on 'Setup L Colours' will create 'n' colour select dropdowns depending on what number you put in the 'Choose L setp size' input.
10. Clicking on 'Setup s Colours' will do the same as 8. for the number you typed in the 'Choose s step size' input.
11. Set the colour pattern you want.
12. Set the scale offset starting note. This sets where the lights start in the scale. The default is 6 - so you can adjust where the scale starts on the bottom left pad on the playing surface.
13. The two buttons underneath should be self explanatory, one creates a simulation of the light pattern based on the settings, and the other creates a string of midi commands in a text box.
14. Once the desired pattern is displayed, and the midi generated, merely copy the text from the text box into a text file and run sendmidi with your text file as an input.
  
Some implementation notes
========================
  
Page is html5, with javascript. It's a fairly simple page with only simple styling, and the javascript is written with some checking but not 'bomb proof'. 
Data is stored in SessionStorage, with prefixed names, hopefully to avoid trampling on other session data.

It is expected that this tool is used in conjunction with Geert Bevin's sendmidi. If you have another tool which sends midi CCs in a different format it should be easy to adapt the generateMidi() function. 
  
The current generateMidi() function inserts 'relative timestamps' in between CC commands to ensure that sendmidi sends the commands slow enough for the LinnStrument to respond. The current setting is 10ms, so a 200-pad light setting takes 2sec to load. Removing them leads to patterns not loading correctly.
 
TO DO
=====
  
Put in full form validation op input fields. Some are validated but not all.
Lots of code tidying.
  

Changes and upgrades
====================
  
I've put this tool as creative commons, please credit my work if you produce a new version / upgrade / incorporate into other software. Thanks!
mark _at_ equiton.net

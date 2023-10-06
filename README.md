# Extension-Blip
Add-on: animate the text of character messages with variable speed and play sound along the animation

# What it does:
- animate the text of character messages with variable speed and play sound along the animation
- Can use audio file or generate the sound

# How it does it:
- Intercept the message using events -> store it and replace by blank in chat history -> wait if an animation is playing -> message get rendered empty -> (optional translation) -> animation start
- Message received are queued to allow to run generate() while animation is played (usefull when user message is animated or in group chat).
- Animation can be force to finish by clicking on usual abort request button (bottom right)

# Features:
## Global settings
- TTS extension inspired options
  - enable/disable user message blip (require user voice assigned to play)
  - only blip for quote
  - disable asterisk blip
 - Enable/disable auto scrolling down to follow text animation.
 - Global audio mixer applied to any blip sound playing (mute/volume) 
 - Settings are saved per character like for RVC extension using a voicemap
  - The voicemap text is just for debug visualization, not editable directly
  
![image](https://github.com/SillyTavern/SillyTavern/assets/48798118/0a322de3-a0cb-462a-9381-a7852b5e5189)

- Default option is the profile that will be used for character with no settings. (if not set, no animation)
- User name appear in second in the list, can be assign a blip like any character (need checkbox enable for it to play)
- Only current chat character show in the list by defautl, clicking the checbox show all character
- Character group list updated automatically, refresh button is for special case like when user add/delete a character for global list update
![image](https://github.com/SillyTavern/SillyTavern/assets/48798118/2d5f59ec-e727-4692-a0a0-435b3a4d9d5a)


## Text settings
- Animation settings allow to set text speed and min/max random multiplier for more dynamism. Some special delay can be applied on comma and phrase end (?,!?.) characters.

![Capture d'écran 2023-09-29 205324](https://github.com/SillyTavern/SillyTavern/assets/48798118/55bce69a-3b14-4891-b500-fe2b46aa68d2)

## Audio settings
- Audio settings, audio speed is independant of text speed except when text pause the audio when comma/phrase delay is set > 0ms. Audio volume percent can be applied for the character, will be a percent of the global sound option when played.

![Capture d'écran 2023-09-29 205402](https://github.com/SillyTavern/SillyTavern/assets/48798118/67c94a92-dd94-4607-82f2-e61f18ffba93)


### Audio origin
- By default a generated sound. User can choose a min/max frequency a random frequency of this range will play for each blip.

![image](https://github.com/SillyTavern/SillyTavern/assets/48798118/49edea0d-3de3-4ea6-928c-4b472458fe0c)

- Audio origin, can also be a audio file from the asset folder. In this case pitch shift min/max can also be choosen for random variation (done without library for now). Also an option to force play the whole audio before starting it again, can be usefull for some effects.

![image](https://github.com/SillyTavern/SillyTavern/assets/48798118/d9105573-ce4e-4021-875d-398ec8bcc022)

# Remarks:
- Can skip animation using the abort request button
- Compatible with translate extension, only the translation is animated.
- Burger menu regenerate/continue click should have no effect *while animation is playing*.
- When using burger menu continue only the new part is animated.

SpeechRecognitionPlugin - Extra Functions
=======================

Adjusted to loop on the listener to always listen to voice. This causes a continous beep sound, which can be heard twice before the mute is enabled. 

Extra functions: options for a mute with delay and a hard mute.



Adapted from:

=======================

W3C Web Speech API - Speech Recognition plugin for PhoneGap

Update 2013/09/05
=================

Back to work on this but it's not ready yet so don't try to use.

Update 2013/08/05
=================

Hi, you are all probably wondering where the code is after seeing my PhoneGap Day US presentation or reading the slides. Well, I've been dealing with an illness in the family and have not has as much spare time as I would have hoped to update this project. However, things are working out better than I could have hoped for and I should have time to concentrate on this very soon.

Update 2015/04/04
=================

Basic example is working on iOS and android
```
<script type="text/javascript">
var recognition;
document.addEventListener('deviceready', onDeviceReady, false);

function onDeviceReady() {
    recognition = new SpeechRecognition();
    recognition.onresult = function(event) {
        if (event.results.length > 0) {
            q.value = event.results[0][0].transcript;
            q.form.submit();
        }
    }
}
</script>
<form action="http://www.example.com/search">
    <input type="search" id="q" name="q" size=60>
    <input type="button" value="Click to Speak" onclick="recognition.start()">
</form>
```

Example from section 6.1 Speech Recognition Examples of the W3C page
(https://dvcs.w3.org/hg/speech-api/raw-file/tip/speechapi.html#examples)

To install the plugin use 

```
cordova plugin add https://github.com/macdonst/SpeechRecognitionPlugin
```

Since iOS 10 it's mandatory to add a `NSMicrophoneUsageDescription` in the info.plist to access the microphone.


To add this entry you can pass the `MICROPHONE_USAGE_DESCRIPTION` variable on plugin install.


Example:

`cordova plugin add https://github.com/macdonst/SpeechRecognitionPlugin --variable MICROPHONE_USAGE_DESCRIPTION="your usage message"`

If the variable is not provided it will use an empty message.


The iOS version uses iSpeech SDK, an API key is required, get one on https://www.ispeech.org/, it's free.
To provide the key, add this preference inside the config.xml
```
 <preference name="apiKey" value="yourApiKeyHere" />
 ```
 If none is provided it will use the demo key "developerdemokeydeveloperdemokey"
 
 Added iOS multiple language support, the supported languages are:
 
English (Canada) (en-CA) 	
English (United States) (en-US) 	
Spanish (Spain) (es-ES) 	
French (France) (fr-FR) 	
Italian (Italy) (it-IT) 	
Polish (Poland) (pl-PL) 	
Portuguese (Portugal) (pt-PT)

Two-character codes can be used too, but for English, "en" will use "en-US" 
 
 

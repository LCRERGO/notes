# Pulseaudio: disable auto mic boost
------------------------------------
By default pulseaudio does an autoincrement in the microphone volume by
detecting the surrond audio and trying to normalize the microphone volume with
the current surrond audio. This might be something anoying when it's not easy
and trivial to control the audio from your microphone by simply altering it on
an audio mixer.

## Solution
To resolve this problem it's necessary to change input audio files present in
the directory:

> /usr/share/pulseaudio/alsa-mixer/paths/

The sections *Element Internal Mic Boost*, *Element Int Mic Boost* and *Element
Mic Boost* may have the atribute set to some value that isn't off or
zero (like merge), if that is the case change it to zero. The changes require
pulseaudio to be restarted.

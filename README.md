# AWS DeepComposer Keyboard AMGI-1 / AKM322

The sticker reads Model Number: AMGI-1

My serial number is: 00000791

Rack.app sees the MIDI device as AKM322

usb vendor/product combo is 1acc:1533

Mac system profiler shows this info:

    _name=AKM322
    bcd_device=0.0b
    bus_power=500
    bus_power_used=100
    device_speed=full_speed
    extra_current_used=0
    location_id=0x14100000 / 13<
    manufacturer=MIDIPLUS
    product_id=0x1533
    serial_num=MIDIPLUS-CC-1533-00AKM322
    vendor_id=0x1acc

## MIDI Codes


|Keyboard Label|MIDI Bytes|Command|Channel|               | Values 
|--------------|----------|-------|-------|---------------|-------
| Pitch        | 124      | 14    | 0     | 0,64          | 0-127
| Modulation   | 176      | 11    | 0     | 1             | 0-127
| Volume       | 176      | 11    | 0     | 7             | 0-127
| 0(encoder)   | 176      | 11    | 0     | 10            | 0-127
| 1(knob)      | 176      | 11    | 0     | 21            | 0-127
| 2(knob)      | 176      | 11    | 0     | 22            | 0-127
| 3(knob)      | 176      | 11    | 0     | 23            | 0-127
| Set+Reverb   | 176      | 11    | 0     | 91            | 0,64
| ▶ (play)     | 176      | 11    | 0     | 105           | 127
| ■ (stop)     | 176      | 11    | 0     | 106           | 0,127
| ● (rec)      | 176      | 11    | 0     | 107           | 127
| keys         | 144,128  | 8,9   | 0     | 41-72 (0-120) | 0-127

> NOTE: some systems refer to the codes in hexadecimal instead of decimal. Reverb is typically 0x5B or 91. I will prefer the decimal (91) in this document and code.

## MIDI Synth

This application is a analog synthesizer simulation built on the [Web Audio API](https://webaudio.github.io/web-audio-api/).  It is very loosely based on the architecture of a [Moog Prodigy](http://www.vintagesynth.com/moog/prodigy.php) synthesizer, although this is a polyphonic synthesizer, and it lacks the oscillator sync and glide effects of the Prodigy.  (AKA: this is not intended to be a replication of the Prodigy, so pleased don't tell me how crappy a reproduction it is! :)

This uses my [Web MIDI Polyfill](https://github.com/cwilso/WebMIDIAPIShim) to add MIDI support via the [Web MIDI API](http://webaudio.github.io/web-midi-api/) - in fact, I partly wrote this as a test case for the polyfill and the MIDI API itself, so if you have a MIDI keyboard attached, check it out.  The polyfill uses Java to access the MIDI device, so if you're wondering why Java is loading, that's why.  It may take a few seconds for MIDI to become active - the library takes a while to load - but when the ring turns gray (instead of blue), it's ready.  If you have a native implementation of the Web MIDI API in your browser, the polyfill shouldn't load - at the time of this writing, Chrome Stable (from version 43) has the only such implementation. Earlier versions of Chrome (from version 33) can enable Web MIDI via chrome://flags/#enable-web-midi

You can try it out live at https://danlangford.github.io/AMGI-1_AKM322

Check it out, feel free to fork, submit pull requests, etc.

-Chris

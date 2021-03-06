# flutter_midi

A FLutter Plugin to Play midi on iOS and Android. This uses SoundFont (.sf2) Files.

## Instalation

Download a sound font file, example: `sound_font.SF2` file [here.](https://drive.google.com/file/d/1Oaw_AYVp7BNb7_U9NqgAj9c8r4ALpXw3/view?usp=sharing)

Create an /assets folder and store the .sf2 files

Update pubspec.yaml

``` ruby
assets:
   - assets/sf2/Piano.SF2
   - assets/sf2/SmallTimGM6mb.sf2
```
 
Load the sound font to prepare to play;

```dart
 @override
  void initState() {
    load('assets/sf2/Piano.SF2');
    super.initState();
  }
  
 void load(String asset) async {
    FlutterMidi.unmute(); // Optionally Unmute
    ByteData _byte = await rootBundle.load(asset);
    FlutterMidi.prepare(sf2: _byte);
  }
```

Play and Stop the Midi Notes

```dart
 FlutterMidi.playMidiNote(midi: 60);

 FlutterMidi.stopMidiNote(midi: 60);
```
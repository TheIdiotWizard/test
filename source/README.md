# Source for this build

The firmware in `firmware/melodee-1.6.1.fwsc` is [keremimo/melodee](https://github.com/keremimo/melodee) at
`165d177` (1.6.1) with these patches, applied in order:

1. `0001-…` — Felucca's WHEEL organ restored (the melodee-wheel.patch you supplied).
2. `0002-…` — Felucca's PHASE (with FOLD), LOFI, VOICE, TRIO and PHYS restored at their original engine numbers;
   CZ-1 and SID retired (DRUM keeps KIT SID).
3. `0003-…` — fixed MIDI CCs, on the channel's own track:
   - CC 20–23: the four Stage knobs of the track the channel plays
   - CC 24: that track's sound, stepped as PRESETS does
   - CC 91 / 93: MIX of the shared rack's REVERB (or ROOM) / CHORUS (or PEDAL CHORUS)
4. `0004-…` — fix (also in upstream Melodee): a key, or a ROUT SEL MIDI note, could play another track's sound
   when it arrived while the screen code briefly selected that track (Stage draws each track's row that way).

```
git clone https://github.com/keremimo/melodee && cd melodee && git checkout 165d177
git am /path/to/source/*.patch
./build.sh            # build/melodee.fwsc
tests/run_tests.sh    # host tests
```

The installer labels the build "1.6.1"; it reports itself as a development build (FM-1_900).

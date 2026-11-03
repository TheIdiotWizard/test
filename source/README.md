# Source for this build

The firmware in `firmware/melodee-1.6.1.fwsc` is [keremimo/melodee](https://github.com/keremimo/melodee) at
`165d177` (1.6.1) with these two patches, applied in order:

1. `0001-…` — Felucca's WHEEL organ restored (the melodee-wheel.patch you supplied).
2. `0002-…` — Felucca's PHASE (with FOLD), LOFI, VOICE, TRIO and PHYS restored at their original engine numbers;
   CZ-1 and SID retired (DRUM keeps KIT SID); fixed MIDI CCs:
   - CC 20–23: the FM-1's knobs 1–4, whatever they edit on the screen shown
   - CC 24–27: the LVL of tracks 1–4

```
git clone https://github.com/keremimo/melodee && cd melodee && git checkout 165d177
git am /path/to/source/*.patch
./build.sh            # build/melodee.fwsc
tests/run_tests.sh    # host tests
```

The installer labels the build "1.6.1"; it reports itself as a development build (FM-1_900).

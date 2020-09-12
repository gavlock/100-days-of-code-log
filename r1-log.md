# #100DaysOfCode Log - Round 1 - Gavin Lock

The log of my #100DaysOfCode challenge. Started on [August 31, Sunday, 2020].

## Log

### R1D1 
Started learning the Web Audio API for use in a training and practise
app for reading sheet music and playing piano.

- hooked up microphone input
- created basic spectrum analyzer
- added simple note identification.

[gavlock/100-days-of-code-R1@942c1c6](https://github.com/gavlock/100-days-of-code-R1/commit/942c1c6d17a05cae355008bdaf73c2b2e2380f98)

### R1D2
Started adding verbose in-page logging to work out why my web audio
code isn't working on Safari under iOS. Turns out the JavaScript isn't
even running. Must test with another phone.

[gavlock/100-days-of-code-R1@0dc3f98](https://github.com/gavlock/100-days-of-code-R1/commit/0dc3f98c1f36d88b08bc35dd86d676a9a8d05680)

*and*

Started evaluating different techniques for displaying sheet music in
the browser.

[gavlock/100-days-of-code-R1@f3e217f](https://github.com/gavlock/100-days-of-code-R1/commit/f3e217fefbddbf49fbc0723259a56409db8456cd)

### R1D3
Managed to setup remote debug tools for iPhone Safari, and finally
wrestled Safari into submission. Now able to do simple musical note
identification in a mobile browser.

[changed syntax of `display`
member](https://github.com/gavlock/100-days-of-code-R1/commit/d16d029970b84a20237f2279077ecafb25aa92e6)

[added "webkit" prefix to `AudioContext` for older Safari
support](https://github.com/gavlock/100-days-of-code-R1/commit/7debf826b6a523f7cd3cac358b9c40560c437444)

[changed creation of audio nodes to old style for
Safari](https://github.com/gavlock/100-days-of-code-R1/commit/b2e214cd44a182d5fe6e047a0955cb69ce9f9b41)

[Cleaned up debug and
logging](https://github.com/gavlock/100-days-of-code-R1/commit/158bd711b47954532c39aca528aca99084f41193)

### R1D4
Added an "n standard deviations" filter, and changed the fundamental
detection heuristic.

- Filter out frequencies whose amplitudes are below (mean amplitude +
  n standard deviations), with n currently equal to 5.
  
- Change fundamental detection heuristic from "find frequency with
  highest amplitude" to "after filtering, find the frequency at the
  _first_local_ maximum amplitude."  This is because (with my piano
  samples) sometimes some of the first few harmonics have higher power
  than the fundamental.  This seems to happen especially in the lower
  octaves.

[Add "n standard deviations" filter and change fundamental
detection](https://github.com/gavlock/100-days-of-code-R1/commit/19a8fab14c710b61931629d163e090620d4c944e)

### R1D5
Added "Harmonic Product Spectrum" for evaluation

Trying to resolve yesterday's problems with detection of low octave
notes. Added a harmonic product spectrum to the display to see if HPS
would help out.

*spoiler* --- it doesn't.

[Added "Harmonic Product Spectrum" for evaluation](https://github.com/gavlock/100-days-of-code-R1/commit/43be2d339b4daae7660b22c9b47283b2bd0ad65c)

### R1D6

Spent time studying auto-correlation, which is apparently better that
FFT for low frequencies.

Also, started refactoring the instrument data and code for converting
frequencies to and from note names. This is mostly to have a
convenient set of frequencies for the auto-correlator once I start
implementing it.

[Started refactoring instrument
data](https://github.com/gavlock/100-days-of-code-R1/commit/87c98e6)

### R1D7

Decided to clean up and refactor code before implementing
auto-correlation. Learned how to use JavaScript ES6 modules as part of
doing this.

Also, changed the x-axis of the spectrogram to a logarithmic scale.

[Finished refactoring instrument data](https://github.com/gavlock/100-days-of-code-R1/commit/e33081f)

[Moved `debug` and `instrument` code into modules](https://github.com/gavlock/100-days-of-code-R1/commit/e21eb11)

[Added logarithmic frequency scale](https://github.com/gavlock/100-days-of-code-R1/commit/323693f)

### R1D8

Work in progress: Started adding auto-correlation to test it for
low-frequency pitch detection.

[Started adding auto-correlation](https://github.com/gavlock/100-days-of-code-R1/commit/edcabed)

### R1D9

Re-did the auto-correlation maths. I think the results look better
now.

Next will be trying an FFT on the auto-correlation data, to see if
harmonics help nail down the fundamental frequency better.

[Improved auto-correlation](https://github.com/gavlock/100-days-of-code-R1/commit/00e39b5)

### R1D10

Studying Discrete Fourier Transforms and Fast Fourier Transforms.
First implementing a DFT in JavaScript. (Writing my own instead of
using a library for the learning value.) Will handle FFT later.

[Tweaked display of auto-correlation results](https://github.com/gavlock/100-days-of-code-R1/commit/9567e77)

### R1D11

Fixed a bug in the auto-correlation, which *dramatically* improved the
quality of note detection. I had been mapping the byte values received
from the WebAudio API from [0, 255] to a range of [0, 1] instead of to
a range of [-1, 1].

Also, added a `NoteTracker` component to smooth out (debounce) the
displayed detected note.

[Fixed autocorrelator range bug](https://github.com/gavlock/100-days-of-code-R1/commit/25f2553)

[Added `NoteTracker` to smooth-out/debounce detected note.](https://github.com/gavlock/100-days-of-code-R1/commit/d9cfa8e)

### R1D12

Not much coding done today. Spent most of my time setting up a new
repo and environment for the Music Practice project.  Skunkworks will
continue in the
[100-days-of-code-R1](https://github.com/gavlock/100-days-of-code-R1)
repo for now, but the project
itself will grow in the
[music-practice](https://github.com/gavlock/music-practice) repo.

The project can be run at [https://gavlock.dev/music-practice/]

#### Commits:
- [Getting started with individual note practice.](https://github.com/gavlock/music-practice/commit/5d2f3d5)

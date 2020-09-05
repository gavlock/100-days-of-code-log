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

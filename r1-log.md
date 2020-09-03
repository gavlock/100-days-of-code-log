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

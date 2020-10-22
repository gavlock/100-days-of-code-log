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

### R1D13

Getting started with SMuFL and Bravura

Learning how to use SMuFL fonts - specifically, understanding
positioning and metrics.

#### Commits:
- [WIP: Getting started with SMuFL and Bravura](https://github.com/gavlock/music-practice/commit/bd0cf47)



### R1D14

Started work on `Music` module.

Implemented the `Note` class for dealing with note names, indices and
frequencies.

Started on `Staff` classes. Still need to implement maths for shifting
notes up or down n staff lines (which does not map directly to a
proportionate number of semi-tones).

#### Commits:
- [Replace staff line glyphs with drawn paths.](https://github.com/gavlock/music-practice/commit/a0de832)
- [Started work on `Music` module.](https://github.com/gavlock/music-practice/commit/520d160)



### R1D15

Implemented `StaffCanvas` to render simple music to an HTML
canvas. This will be used by the practice system to display the
challenge and the detected response.

#### Commits:
- [Added drawing of ledger lines, and made staff lines crisper.](https://github.com/gavlock/music-practice/commit/41ddf35)
- [Finished inital work on drawing notes on staves.](https://github.com/gavlock/music-practice/commit/ef9d60d)
- [Add staff indices to notes & staves, and add note array to staves.](https://github.com/gavlock/music-practice/commit/16240ab)



### R1D16

Started work on the concept of a practice "session".

Added in the Web Audio "listener" and used auto-correlation to
determine the note played by the user.

#### Commits:
- [Changed from using `#` to `♯` internally](https://github.com/gavlock/music-practice/commit/32cd362)
- [Made space to display hint/answer in challenge box](https://github.com/gavlock/music-practice/commit/05c9440)
- [Merge branch 'draw-notes' into main](https://github.com/gavlock/music-practice/commit/fe60ecc)
- [Added practice `Session` class, prevent dupes, and request audio](https://github.com/gavlock/music-practice/commit/89af8bc)
- [Added `noteListener`, `noteTracker` & basic display of detected note](https://github.com/gavlock/music-practice/commit/ac00aa1)



### R1D17

Started adding a page for testing & tweaking audio processing parameters.

Also, switching to use a Web Audio script processor, instead of an
analyzer node.

#### Commits:
- [Start adding page for testing & tweaking audio processing parameters](https://github.com/gavlock/music-practice/commit/d8130ed)



### R1D18

Added a plot of the microphone sound levels, and configurable
sound/silence detection to the audio test page.

#### Commits:
- [Plot input levels on audio test page](https://github.com/gavlock/music-practice/commit/618e8a4)
- [Added silence/sound detection with configurable thresholds](https://github.com/gavlock/music-practice/commit/b11e90d)
- [Added `jqueryui-touch-punch` so that controls work on touch screens](https://github.com/gavlock/music-practice/commit/e438ba3)



### R1D19

Started adding autocorrelation to audio test page

#### Commits:
- [Started adding autocorrelation to audio test page](https://github.com/gavlock/music-practice/commit/3ba06b2)



### R1D20

Did some more work on the autocorrelation code, and added a chart to
visualise the correlation function.

#### Commits:
- [More work on autocorrelation, including adding correlation chart](https://github.com/gavlock/music-practice/commit/2477a1e)



### R1D21

My naïve implementation of the autocorrelator is too slow - as expected
(make it work, THEN make it fast.)

Spent time today trying out various optimisations.

No new code to commit yet - will continue tomorrow.



### R1D22

Spent time playing around with TensorFlow to see if I can use it to
offload the audio processing to the GPU (because most of the
calculations needed are *very* parallelisable.)

Another route I might explore in the future is to use WebGL and write a shader to do
the calcs.

Also in the future: For multi-note (chord) detection, a neural net
might be the way to go. This would obviously be able to handle single
notes as well, but for now, I still want to continue exploring
traditional correlation and/or Fourier transform approaches.



### R1D23

Started implementing autocorrelation using Tensorflow.
Spent most of my time getting back up to speed with D3 so that I can
use it for visualisations.

#### Commits:
- [Started working with TensorFlow and D3 visualisations](https://github.com/gavlock/100-days-of-code-R1/commit/f30759c)



### R1D24

Some more D3 work improving the visualisations so that I can actually
see what results I get back from TensorFlow.

Maybe I'm
[shaving a yak](https://seths.blog/2005/03/dont_shave_that/),
maybe I'm not - but at least I'm learning, and getting back into the
habit of coding every day.

#### Commits:
- [Added multi-series support to `Chart`](https://github.com/gavlock/100-days-of-code-R1/commit/4e23576)
- [Added series labels and cleaned up horizonal ticks](https://github.com/gavlock/100-days-of-code-R1/commit/3221e00)



### R1D25

Playing around with various TensorFlow operations, I realised that the
maths behind convolution (the sum of the element-wise products of the
signal and the kernel as the kernel is moved across the signal) and
the maths behind auto-correlation (the sum of the element-wise
products of the signal with a shifted copy of itself as the shift
(lag) is "moved" across the frequency range of interest) are basically
the same!

In other words, using a shifted (lagged) copy of the signal as the
kernel for a 1D convolution of the signal itself, effectively
calculates the reverse of the correlation function.

This means that I can use TensorFlow's `conv1d` function as a
GPU-powered autocorrelation function.

#### Commits:
- [Autocorrelation using autoconvolution](https://github.com/gavlock/100-days-of-code-R1/commit/ee3f6de)



### R1D26

Created an audio signal generator that will produce small windowed
buffers of audio in the same way that I would receive them from an API
like Web Audio.

Modified the TensorFlow autocorrelator to operate in windowed mode,
shifting new data buffers through its "working areea" variable.

Windowing, with a relatively small buffer, allows the code to respond
to changes in the incoming audio sooner. Keeping the working buffer on
the GPU improves performance, as I only have to upload the new window
on each audio tick.

#### Commits:
- [Truncate, rather than shift, the kernel](https://github.com/gavlock/100-days-of-code-R1/commit/ab551b9)
- [Move D3 chart code to a module](https://github.com/gavlock/100-days-of-code-R1/commit/c27515d)
- [Adding windowed audio generator](https://github.com/gavlock/100-days-of-code-R1/commit/7f2ca2d)
- [Added windowed-audio support to TensorFlow autocorrelator](https://github.com/gavlock/100-days-of-code-R1/commit/6fbea3c)



### R1D27

Replaced the JavaScript-based autocorrelation in the audio test page
with the new solution using TensorFlow.

Performance is *dramatically* improved.

#### Commits:
- [Fixed bug regarding inital "local echo" setting](https://github.com/gavlock/music-practice/commit/591e9f6)
- [Add scaling factor for JS-based correlation](https://github.com/gavlock/music-practice/commit/9c7d66f)
- [Replacing JavaScript autocorrelator with  TensorFlow autocorrelator](https://github.com/gavlock/music-practice/commit/dc5638f)



### R1D28

Getting ready for the next step - neural nets.

Updated Python, Jupyter, TensorFlow and Keras.
Started playing around with some ideas for ANN models to handle
multi-note (chord) pitch recognition.



### R1D29

Downloaded the MAPS dataset and started working on Python code to
iterate through the dataset, reading the audio and note data for each
sample.



### R1D30

Finished the Python code to iterate through the MAPS dataset and
started setting up the neural net model to train with the MAPS data.

#### Commits:
- [Added FFT of autocorrelation](https://github.com/gavlock/100-days-of-code-R1/commit/6224ca9)
- [Merge branch 'autocorrelate' into main](https://github.com/gavlock/100-days-of-code-R1/commit/9783915)
- [Read MAPS Database for neural net training](https://github.com/gavlock/100-days-of-code-R1/commit/7955430)



### R1D31

Transferred the MAPS iterate & read code from my Jupyter notebook into
a Python module.

Updated Emacs and cleaned up my `init.org` file.

#### Commits:
- [Create `samples.maps` module and reorganise files and folders](https://github.com/gavlock/100-days-of-code-R1/commit/966a212)



### R1D32

Taking a short break from the music practice app.

Spent the day learning OpenSCAD's built-in language and using it to
programmatically define some models I needed to 3D print.



### R1D33

Did some more elisp coding of some utility functions for emacs.

Wrote `raise-next-frame`, `raise-previous-frame` and `ido-raise-frame`
functions, and setup key bindings, to make it easier to switch between
emacs frames spread across my various virtual desktops.

[switch-frames.el](https://gist.github.com/gavlock/f446c5508e9b522a845fd9e3c76a988e)

Also, wrote an `:around` advice function for `eshell` to get a
separate eshell buffer for each Projectile project.

[projectile-eshell.el](https://gist.github.com/gavlock/93ea032f5f3b12e4409964a6ad686e72)



### R1D34

Returning to the music practice app.

Set up a Jupyter notebook to explore extracting audio clips from MAPS
for training the neural net.

#### Commits:
- [Exploring audio clip extraction](https://github.com/gavlock/100-days-of-code-R1/commit/da5a006)



### R1D35

Finished transforming MAPS data into what I need for the neural net.
Started designing the model.

Training starts well, but - pretty quickly - the loss function returns
NaN, and accuracy drops to zero flat. Investigating...

#### Commits:
- [Implement MAPS data transforms and basic clip extraction](https://github.com/gavlock/100-days-of-code-R1/commit/2410fc4)
- [Start designing model](https://github.com/gavlock/100-days-of-code-R1/commit/159a65d)



### R1D36

Fix NaN losses by changing activations

- Change hidden layer to use a *leaky* RELU to avoid the "dying RELU"
  problem

- Change the output layer to use Softmax for now (for single note
  testing). Will probably use Sigmoid later on.

#### Commits:
- [Fix NaN losses by changing activations](https://github.com/gavlock/100-days-of-code-R1/commit/261153f)



### R1D37

Started refactoring dataset importing to make the dataset note-centric
(rather than data-source-and-instrument-centric).

#### Commits:
- [Start refactoring dataset importing](https://github.com/gavlock/100-days-of-code-R1/commit/921fc8c)



### R1D38

Continued refactoring dataset importing - including reading audio
samples directly into tensors.

#### Commits:
- [Continue refactoring dataset importing](https://github.com/gavlock/100-days-of-code-R1/commit/f4f1373)



### R1D39

Finished refactoring the dataset importing, and created the dataset
and data sources Python package.

#### Commits:
- [Finish dataset refactoring and package](https://github.com/gavlock/100-days-of-code-R1/commit/28d2251)



### R1D40

Continuing to work on the Keras model using the refactored dataset.

Created a `keras.utils.Sequence` generator, but I'm struggling to get
it working with `model.fit`.



### R1D41

Managed to get the generator working by "squeezing" the audio waveform
batch data from [batch_size, window_size, 1] to [batch_size, window_size]

#### Commits:
- [Create a `keras.utils.Sequence` generator for training the model](https://github.com/gavlock/100-days-of-code-R1/commit/d8562b4)



### R1D42

Playing around with different architectures for the model.

Today's focus: convolution layers



### R1D43

Playing around with different architectures for the model.

Today's focus: depth vs width

Also, started creating charts to visualise model accuracy across
different dimensions (note, time-since-onset and (maybe) instrument).



### R1D44

Finished creating charts to visualise model accuracy across different
dimensions: accuracy by note, accuracy by time-since-onset, and a 3D
scatter plot of accuracy by note and time.

[Jupyter notebook](https://github.com/gavlock/100-days-of-code-R1/blob/0d69fb0/machine-learning/piano/Model%20design.ipynb)

#### Commits:
- [Add `get_clip_at_t` method to samples](https://github.com/gavlock/100-days-of-code-R1/commit/570a1ed)
- [Add visualisation of trained model accuracy by note and time](https://github.com/gavlock/100-days-of-code-R1/commit/0d69fb0)



### R1D45

Exploring deeper convolution networks and convolution dilation rates.

[Jupyter notebook](https://github.com/gavlock/100-days-of-code-R1/blob/1dd46c1/machine-learning/piano/Model%20design.ipynb)

#### Commits:
- [Explore deeper convolution networks and convolution dilation rates](https://github.com/gavlock/100-days-of-code-R1/commit/1dd46c1)

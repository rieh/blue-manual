# BlueX7

!!! note
    This instrument is currently undergoing re-implementation.

A 6 Operator Phase Modulation instrument using Russell Pinkston's DX7
Emulation Patches.

The BlueX7 editor contains two tabs, the 'patch' tab, where the sound
creation parameters are tweaked and a second tab called 'csound' which
can contain further post-processing algorithms or special routing of the
instrument's output.

The patch tab contains three panels: Common, LFO and operators. The
common panel deals with global aspects of the instrument like
transposition, FM algorithm used, feedback, operator enable/disable and
LFO characteristics. The transposition made by Key Transpose is handled
in half-tones, with C3 being the normal (central) pitch.

There are 32 algorithms to choose from which represent the original DX7
possibilities. You can see a visual representation of the algorithm on
the left of this panel.

Feedback represents the amount of feedback into a modulator. The
position and result of this feedback depends entirely on the algorithm
used. The range of feedback is 0 to 7(this range is the same as on the
original DX7). The operator on/off checks turn on and off operators
(current, this is here but the emulation patches do not use them).

The LFO panel sets the global LFO parameters. The parameters are: Speed,
Delay, PMD (Pitch Modulation Depth) and AMD (Amplitude Modulation
Depth). They all have ranges from 0 to 99(the range is the same as on
the original DX7). Additionally you can select the shape of the LFO
from: triangle, saw up, saw down, square, sine and sample-and-hold. You
can also sync the operators: if sync is on, changing Modulation
Sensitivity for pitch (marked with an asterisk \*) on any of the
operators will affect the rest.

Finally you have the 6 operators plus an envelope generator (PEG) each
on its own tab. All six operators have the same parameters divided in
the following sections:

  - Oscillator

  - Keyboard Level Scaling

  - Operator

  - Modulation sensitivity

  - Envelope Generator

An important feature of the BlueX7 is that it can import DX7 banks. A
large collection can be found in the bigdx7.zip file within the
dx72csound.zip file from: [](http://www.parnasse.com/dx72csnd.shtml).
(to steven: reading this page it seems part of the model is unfinished,
which may answer some of my questions above)

On the 'csound' tab you find by default:

```csound-orc
    blueMixerOut aout, aout
```

This routes the output of the instrument directly to the stereo output
of csound. You can include further code to process the 'aout' signal
produced by the BlueX7, or to route it as needed. For example, if you
are outputing in mono, you could code such as:

```csound-orc
    out aout
```

To call the BlueX7 instrument in the orchestra, create a GenericScore
object in the timeline, and call the the BlueX7 instrument. BlueX7
requires 2 additional p-fields. P-field 4 is the pitch class of the note
in format octave.semitone (e.g. C4 is 4.00, C\#1 is 1.01 and F6 is
6.05). P-field 5 contains the midi velocity for the note with values
from 0 to 127. For example:

```csound-sco
i1 0 1 8.00 100
i1 + 1 8.02 100
i1 + 1 8.04 100
i1 + 1 8.05 100
i1 + 1 8.07 100
```
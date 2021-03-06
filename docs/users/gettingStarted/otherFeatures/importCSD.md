# Importing ORC/SCO and CSD Files

Blue is able to import ORC/SCO and CSD files and set up a Blue project
file, with instruments parsed out and put into the orchestra manager,
project settings set, etc. Currently, there are three options to choose
from when importing a CSD file, all relating to how you would like to
import the notes from the CsScore section:

  - Import Score to Global Score - all score goes to the Global Score
    section

  - Import All Score to Single SoundObject - all score goes into a
    single GenericScore SoundObject. The duration of the soundObject
    will be set to the duration of the imported score. This is broken up
    into different soundObjects and layers if sections (s-statement) are
    found in the score.

  - Import Score and Split into SoundObjects by Instrument Number -
    score is split by instrument number and a different GenericScore
    soundObject will be created for each block of score text per
    instrument. This is broken up into different soundObjects and layers
    if sections (s-statement) are found in the score.

## Notes

  - From the CsScore, Blue will only import f-, i-, and s- statements.
    Other score statements are not currently supported at this time.

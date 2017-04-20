
       @ @@@                                       @@@@@   @@    @@                @@
     @  @@@@  @                                 @@@@@@  @@@@@ @@@@@     @           @@     @
    @  @  @@@@                                 @@   @  @  @@@@@ @@@@@  @@@          @@    @@@
   @  @@   @@                                 @    @  @   @ @@  @ @@    @           @@     @
  @  @@@         @@@    @@@     @@@    @@@        @  @    @     @                   @@
 @@   @@        @ @@@  @@@@ @  @ @@@  @@@@ @     @@ @@    @     @     @@@       @@@ @@   @@@
 @@   @@           @@@ @@@@@      @@@ @@@@@      @@ @@    @     @      @@@     @@@@@@@@@  @@@
 @@   @@            @@@  @@        @@@  @@       @@ @@    @     @       @@    @@   @@@@    @@
 @@   @@             @@@            @@@          @@ @@    @     @       @@    @@    @@     @@
 @@   @@            @ @@@          @ @@@         @@ @@    @     @@      @@    @@    @@     @@
  @@  @@           @   @@@        @   @@@        @  @@    @     @@      @@    @@    @@     @@
   @@ @      @    @     @@@      @     @@@          @     @      @@     @@    @@    @@     @@
    @@@     @    @       @@@ @  @       @@@ @   @@@@      @      @@     @@    @@    @@     @@
     @@@@@@@    @         @@@  @         @@@   @  @@@@@           @@    @@@ @  @@@@@       @@@ @
       @@@                                    @     @@                   @@@    @@@         @@@
                                              @
                                               @@
```

# CxxMidi v0.2

Modern C++ MIDI library.

## Key features
* MIDI files read/write
* MIDI files parsing, editing, sequencing (composition)
* MIDI outputs
  * ALSA on Linux
  * WinMM on Windows
* Multiplatform MIDI players
  * synchronous
  * asynchronous

## Design
* Multiplatform (Linux, Windows)
* Endian safe
* Boost-like HPP header files only library

## Hello World

``` cpp
#include <cxxmidi/file.hpp>
#include <cxxmidi/output/default.hpp>
#include <cxxmidi/player/synchronous.hpp>

int main(int /*argc*/, char ** /*argv*/)
{
    CxxMidi::Output::Default output; // create a MIDI output default for the OS
    output.openPort(0); // open port num 0
    
    CxxMidi::Player::Synchronous player(&output); // create a MIDI player

    CxxMidi::File file("music/chopin.mid"); // open a MIDI file
    player.setFile(&file);

    player.play(); // synchronous play
}

```

## License
* CxxMidi: GPLv3
* pstdint: BSD
* RtMidi: https://www.music.mcgill.ca/~gary/rtmidi/index.html#license 
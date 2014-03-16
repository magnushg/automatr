automatr
========

Project for controlling and recieving data from an Arduino attached to a Raspberry Pi using the library johnny-five (https://github.com/rwaldron/johnny-five).

The Solution consists of two submodules. [recievr](https://github.com/magnushg/recievr) is a node server application that uses johnny-five to read and write data to an Arduino. Data from the Arduino is posted to [firebase](https://www.firebase.com/). [ctrlr](https://github.com/magnushg/ctrlr) is an Angular JS website that recieves and sends data to an environment monitoring server though [firebase](https://www.firebase.com/).

The presentation folder contains a [presentation](presentation/ControllingTheWorldBouvetOne.pptx) and a [script](presentation/Script.md) to be used for this presentation.

use `git submodule update --init` to get submodules

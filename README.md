automatr
========

Project for controlling and recieving data from an Arduino attached to a Raspberry Pi using the library johnny-five (https://github.com/rwaldron/johnny-five).

The Solution consists of two submodules. [recievr](https://github.com/magnushg/recievr) is a node server application that uses johnny-five to read and write data to an Arduino. Data from the Arduino is posted to [firebase](https://www.firebase.com/). [ctrlr](https://github.com/magnushg/ctrlr) is an Angular JS website that recieves and sends data to an environment monitoring server though [firebase](https://www.firebase.com/).

The presentation held at NDC Oslo 2014 can be found on Vimeo, https://vimeo.com/97516287. The slides are available on SlideShare, http://www.slideshare.net/magnushgreen/controlling-the-world-with

use `git submodule update --init` to get submodules

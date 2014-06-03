Controlling the world with JavaScript and Arduino
=================================================

The Message
-----------
* What is internet of things and why is it important? Internet of Everything
* Holy trinity of Internet of Things->Cloud Services->Big Data
* What is home automation and how can you get started doing it?
* Demonstrate one way this can be done through my own project and experiences
* Inspire you to start your own projects

Introduction 
------------
* Everything connected
* Internet of Things -> Big Data -> Cloud, lage en modell
* Using the cloud as an enabler / communication

Me / Purpose of this talk / Agenda
----------------------------------
* Magnus Green - Who am I and why am I here?
* Give an introduction to Internet of Things and how I've done it in my project.
* Demontrate technologies through real examples
* My choice is made, there is certainly different ways to do this
* Challenges to be conquered, I will not be talking so much about this, but Simen Sommefeldt will fill you in in his talk.

Internet of things
------------------
* What is Internet of things and why is it important?
* Phones / devices, cars, watches, clothes, X-ray or MR, fitbit? Even windmills?
* Major corporations like Microsoft, Oracle & Google (Just bought Nest) are building it into their products
* Statistics differ a lot: Cisco 50 billion, Strada is selling measurements, the city of Oregon or Portland

Home automation with Internet of Things
---------------------------------------
* Controlling appliances in your home through Internet.
* Smart houses, show pictures of concepts
* Nexa, lysbryterstyring
* Off the shelves products like Nest or Fitbit
* No service that gives you everyting in one package.
* Smart houses, packages, door locks
* Manifested by connecting up sensors like temperature, light, humidity and actuators like buttons, motors, servos etc...

Facts and figures
------------------
* According to Cisco and Ericsson there will be approx 50 billion devices connected
* IDC (International Data Corporation) study estimates 212 billion devices connected by 2020.
* IDC and Microsoft predics that this will generate a revenue of 1.7 trillion dollars estimated market size for IoT hardware software, services in all areas manufacturing, telecom, consumer
* Google recently aquired Nest (IoT smoke alarms and Thermostats)  for $10 billion
* Microsoft is making Windows free to use for devices smaller than 9"

Arduino facts
-------------
* Open Source prototyping plattform created so programmers and designer could do cheap prototyping.
* Can send and recieve voltage between 0 - 5V. This is how you communicate with the Arduino.
* Microcontroller board based on ATmega328, 14 digital input / output pins. 6 analog inputs.
* Several sizes and different versions with various layots.
* Programmed with C like language wiring, processing
* There are many alternatives out there, tessel.io with embedded JavaScript, Intel based boards that run Windows
* Demo Simple blink in arduino IDE

johnny-five facts
-----------------
* Control Arduino with JavaScript through node server
* Gives access to all node.js goodies.
* More convenient for Web and cloud programming than more native approach on Arduino
* Abstrations for leds, relays, buttons, motors, sensors

My project, overview model of how things connect
------------------------------------------------
* Arduino run by JavaScript library Johnny-five.
* In order to run node server on on small device, using RaspberryPi
* Data is sent and stored with cloud service Firebase
  * Firebase is a real-time communication cloud based service. Well docmented with a quite nice free intro level package
  * Reason for choosing Firebase is that it has really easy to use libraries for both node.js and Angular
  * It enables Real-time communication between back-end connected to Arduino and web based front-end.
* The monitoring data is presented in a web front-end build with Angular

Getting started Arduino
------------------------
* Simple blink example in Arduino IDE

Getting started johnny-five
---------------------------
* Demo Simple blink in johnny-five

Putting everything together
---------------------------
* Demo back-end node.js server, write code and show result in the front-end web application.
* Focus on the part of the code that is connected to the sensors. 

Demo
----
* Show coding workflow, code on windows -> transfer with WinSCP -> run on Raspberry
* Use supervisor to keep the process running
`git checkout demo/baseline`
* START demo/stage-1
add relay, `var relay = new five.Relay("O0");`
* legg relay til repl
* END demo/stage-1
* START demo stage-2
* Legg til lightswitch
            
		automatrFirebase.on('value', function (snapshot) {
                  snapshot.val().lightswitch ? relay.on() : relay.off();
              });
            
            thermSensor.on('data', function () {
                var temperature = converter.celsius(this.value).toFixed(2);
                automatrFirebase.update({temperature: {value:temperature, timestamp: Date.now()}});
              });
            
              photoSensor.on('data', function () {
                automatrFirebase.update({brightness: {value:this.value, timestamp: Date.now()}});
              });
* END demo/stage-2
* START demo/stage-3

            thermSensor.on('data', function () {
                var temperature = converter.celsius(this.value).toFixed(2);
                var tempLog = {temperature: {value:temperature, timestamp: Date.now()}};
                console.log("Temperature: " + temperature);
                automatrFirebase.update(tempLog);
                environmentLog.push(tempLog);
              });
            
              photoSensor.on('data', function () {
                var brightnessLog = {brightness: {value:this.value, timestamp: Date.now()}};
                console.log("Brightness: " + this.value);    
                automatrFirebase.update(brightnessLog);
                environmentLog.push(brightnessLog);
                if(this.value <= 200) {
                  relay.on();
                }
              });
* END demo/stage-3

Summary / conclusion
--------------------
* We need good design and services to be a success, service design.
* Not just fun and games, Microsoft and Oracle builds IoT support into their products
* The predictions say that this is a field that will generate a tremendous income moving forward
* Internet of Things -> Big Data -> Cloud

All code is available on github
-------------------------------

Thank you for your attention
----------------------------

Aktuelle artikler:
http://www.aftenposten.no/okonomi/De-lever-i-fremtiden-7552621.html#.U2fAfvl_tUV
http://www.aftenposten.no/digital/Google-kjoper-roykvarsler--og-termostatfirma-for-20-milliarder-kroner-7432819.html#.U2fB7fl_tUU
Copyright bilder
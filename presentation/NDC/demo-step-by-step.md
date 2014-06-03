NDC automatr demo steps
=======================

0.Start with an empty shell before starting on "Hello world" sample.

	git checkout ndc/baseline

1.Empty node server containing only what you need to get started. Start by defining a johnny five board. Also include a Read Edit Print Loop (REPL)

		var board = new five.Board();
	
		board.on("ready", function() {
	
				board.repl.inject({
	
				});
	
		});

		sublime-snippet: d0-setup-board

2.Define a simple led light and turn it on / off	
		
	var led = five.Led("O0");
	led.strobe();

		sublime-snippet: d1-led-blink

3.Define a temperature sensor and connect to it's data event. Log value to console. 
Value is between 0 - 1023 since it is not yet converted
	
	var tempSensor = five.Sensor({pin: "I0", freq: 2000});`

	 tempSensor.on("data", function() {
	 	console.log(this.value);
  	 });

4.Convert value to celsius using converter.tempC. Add Firebase update.

add converter util

	converter = require("./utils/converter");
	
	sublime-snippet: d2-converter

add firebase endpoints

	stringUtils = require("./utils/stringUtils"),
	Firebase = require("firebase"),
	firebaseName = 'automatr-test',
  
  
	automatrFirebase = new Firebase('https://{0}.firebaseio.com/'.format(firebaseName)),
	environmentLog = new Firebase('https://{0}.firebaseio.com/environmentLog'.format(firebaseName));

	sublime-snippet: d2-firebase-endpoints

Add tempsensor final with firebase update and converter

	var tempSensor = five.Sensor({pin: "I0", freq: 2000});

	tempSensor.on("data", function() {
		var tempCelsius = converter.tempC(this.value).toFixed(1);
		var temperature = {temperature: {value:tempCelsius, timestamp: Date.now()}};
		automatrFirebase.update(temperature);    
		environmentLog.push(temperature);
	});

  		sublime-snippet: d2-temp-sensor

5.Add coffe maker switch and subscribe to value from Firebase 

	var coffeeMaker = new five.Relay("O3");

	automatrFirebase.on('value', function (snapshot) {
      snapshot.val().coffee ? coffeeMaker.on() : coffeeMaker.off();
  	});

		sublime-snippet: d3-coffee-maker-toggle

6.Add light sensor and all content

	var lightSensor = five.Sensor({pin: "I2", freq: 2000});
	
	lightSensor.on("data", function () {
    	var brightness = {brightness: {value: this.value, timestamp: Date.now()}}
    	automatrFirebase.update(brightness);
    	environmentLog.push(brightness); 
    });

		sublime-snippet: d4-light-sensor

7.Add proximity sensor triggering an indication light

	var proximity = new five.Sensor({pin: "I5"});
 
	proximity.on("change", function() {
		if(this.value > 0) {
		automatrFirebase.update({proximity: {value: true, timestamp: Date.now()}});
		led.on();
		}
		else {
		automatrFirebase.update({proximity: {value: false, timestamp: Date.now()}});
		led.off();
		}
	});

  		sublime-snippet: d5-proximity-sensor

8.Add lightswitch to turn on light

	var lightSwitch = new five.Relay("O5");

	automatrFirebase.on('value', function (snapshot) {
	snapshot.val().lightswitch ? lightSwitch.on() : lightSwitch.off();   
	});

 		sublime-snippet: d6-lightswitch
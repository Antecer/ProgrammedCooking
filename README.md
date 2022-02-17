# ProgrammedCooking  
Use a programming language to describe the cooking process

## About  
Program the cooking process for more precise cooking results.

## Unit Of Measure Definition  
Amount.name = "piece";  
Weight.name = "g";  
SideLength.name = "mm";  
Volume.name = "ml";  
Temperature.name = "℃";

### Sample  
```js
// Author: Antecer
// Description: scrambled eggs with tomatoes

// food preparation
var Chef = { count: 1 };
var Diners = { count: 1 };
var Egg = { name: "egg", count: Diners.count };
var Tomato = { weight: 100, count: Egg.count };
var GreenOnion = { count: Egg.count };
var Salt = { weight: 4 * Egg.count };
var Sugar = { weight: 4 * Egg.count };
var SoySauce = { volume: 3 * Egg.count };
var MSG = { weight: 1 * Egg.count };
var WhiteVinegar = { volume: 1 * Egg.count };
var PeanutOil = { volume: 8 * Egg.count };

// kitchen utensils
var Container = { name: "Bowl", minVolume: 50 * Egg.count + 100 };
var Pot = { name: "Wok", minVolume: (50 * Egg.count + 0.8 * Tomato.weight * Tomato.count) * 3, minDiameter: 280 };
var StirFryTool = { name: "Spatula", count: 1 };
var Workbench = { name: "ChoppingBoard", count: 1 };
var Knife = { name: "KitchenKnife", count: 1 };
var StirringRod = { name: "Chopsticks", count: 1 };
var Plate = { count: 1 };

// countdown tool
function sleep(ms) {
	return new Promise((resolve) => setTimeout(resolve, ms));
}

// cooking process
(async () => {
	Tomato.description = `Washed with water, Then put the tomatoes on ${Workbench.name} and use ${Knife.name} cut into 10mm³ cubes.`;
	Tomato.volume = 0.8 * Tomato.weight * Tomato.count;
	Container.description = `Put the contents of the ${Egg.name} into the ${Container.name}, Then stir well with ${StirringRod.name}`;
	Container.contents = [Egg.content];
	Pot.contents = [PeanutOil];
	Pot.temperature = 160;
	Pot.contents.push(Container.contents);	// contents of the egg
	Pot.contentStatus = "liquid";
	while (Pot.contentStatus != "semi-solidified") await sleep(1000);
	Pot.property = { tool: StirFryTool, stirFry: true };
	while (Pot.contentStatus != "solidified") await sleep(1000);
	Pot.property.stirFry = false;
	Pot.contents.concat([Tomato, Salt, Sugar, SoySauce, WhiteVinegar]);
	Pot.property.stirFry = true;
	await sleep(1000 * 60 * 3);
	while (Tomato.status != "molten") await sleep(1000);
	Pot.property.stirFry = false;
	Pot.temperature = 100;
	Pot.contents.push(MSG);
	Pot.property.stirFry = true;
	await sleep(1000 * 10);
	Pot.property.stirFry = false;
	Pot.temperature = null;
	Plate.contents = Pot.contents;
	GreenOnion.description = `Washed with water, Then use ${Knife.name} cut into 1mm long hollow circles`;
	Plate.contents.push(GreenOnion);
})();

// Tips:
// 1. Be careful when using the kitchen knife, do not cut your fingers!
// 2. When using an open flame to heat a wok, you need to pay attention to safety so as not to burn down the house!
```

## Tips  
Welcome to create your Pull Requests!
Please make sure your program compiles!
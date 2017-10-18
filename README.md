# Gigi-Tale

/*In this drawing I've shifted RGB channels with photoshop and create the illusion of movement that is given by the continuos color change through a few Actionscript code lines (Color Matrix). Turning it into javascript code is my first step to get started.*/

Here's the code:

import flash.filters.BitmapFilter;
import flash.filters.ColorMatrixFilter;

loadMovieNum("ThelitteleYeti.swf", 50);

var image:MovieClip = this.attachMovie("YourImageLinkage", "YourImage", this.getNextHighestDepth());
image.cacheAsBitmap = true;

var listener:Object = new Object();
listener.image = image;
listener.onMouseMove = function() {
	var aPercent:Number = random(2);
	var bPercent:Number = random(2);
	var cPercent:Number = random(2);
	var dPercent:Number = random(2);
	var ePercent:Number = random(2);
	var fPercent:Number = random(2);
	var gPercent:Number = random(2);
	var hPercent:Number = random(2);
	var iPercent:Number = random(2);
	if (aPercent & bPercent & cPercent == 1) {
		bPercent = 0;
		cPercent = 0;
	} else if (aPercent & bPercent & cPercent == 0) {
		aPercent = 1;
	} else if (aPercent & bPercent == 1) {
		aPercent = 0;
	} else if (bPercent & cPercent == 1) {
		cPercent = 0;
	} else if (aPercent & cPercent == 1) {
		aPercent = 0;
	}
	///////////////                 
	if (dPercent & ePercent & fPercent == 1) {
		ePercent = 0;
		fPercent = 0;
	} else if (dPercent & ePercent & fPercent == 0) {
		ePercent = 1;
	} else if (dPercent & ePercent == 1) {
		dPercent = 0;
	} else if (ePercent & fPercent == 1) {
		fPercent = 0;
	} else if (dPercent & fPercent == 1) {
		dPercent = 0;
	}
	//////////////                 
	if (gPercent & hPercent & iPercent == 1) {
		hPercent = 0;
		iPercent = 0;
	} else if (gPercent & hPercent & iPercent == 0) {
		iPercent = 1;
	} else if (gPercent & hPercent == 1) {
		gPercent = 0;
	} else if (hPercent & iPercent == 1) {
		iPercent = 0;
	} else if (gPercent & iPercent == 1) {
		gPercent = 0;
	}
	var yPercent:Number = 1-(_ymouse/Stage.height);
	var matrix:Array = new Array();
	matrix = matrix.concat([aPercent, bPercent, cPercent, 0, 0]);// red
	matrix = matrix.concat([dPercent, ePercent, fPercent, 0, 0]);// green
	matrix = matrix.concat([gPercent, hPercent, iPercent, 0, 0]);// blue
	matrix = matrix.concat([aPercent, aPercent, aPercent, 1, 0]);// alpha

	var filter:BitmapFilter = new ColorMatrixFilter(matrix);
	image.filters = new Array(filter);
};

Mouse.addListener(listener);
listener.onMouseMove();

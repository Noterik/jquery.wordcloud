# NoterikDataVisualizations
Data Visualization plugins for jQuery using d3.js, contains several jQuery plugins that can be used to visualize data.

##Dependencies

-jQuery

-d3

##Building

Make sure you have npm installed, go to NoterikDataVisualization root directory and run:

```javascript
npm install
```

After that run:

```
grunt
```

In NoterikDataVisualization root directory.

##Usage

You can use them by adding them to your webpage like:

```html
<script src="noterik-data-visualizations-<VERSION>.min.js">
```

All plugins use jQueryUI like initialization:

```javascript
$("#wordcloud").ntkWordcloud({setting: 'settingValue'})
```

Examples can be found in the /examples folder and can be run without a webserver.

##Wordcloud

Renders words in a cloud. When a new word is added, it "shoots" it into the existing cloud. If a word is added that
already exists, the size of the existing word will be increased. Example code can be found in /examples/wordcloud.html

DEMO:

https://rawgit.com/Noterik/NoterikDataVisualizations/master/example/wordcloud.html

###Initialization

A wordcloud can be initialized like this:

```javascript
$('#wordcloud').ntkWordcloud();
```

All the settings can be passed when initializing the wordcloud, example:

```javascript
$("#wordcloud").ntkWordcloud({
  gravity: 0.5
});
```

###Updating

A word can be added like this:

```javascript
$('#wordcloud').ntkWordcloud('addWord', {
    text: "Lorum"
});
```

###Wordcloud generic settings
Setting    |  Type | Explanation
-----------|-------|-------------
words      | Array | The array of words that you want to show when initialization the words. (predefined words)
gravity    | Double| The gravity that the center of the cloud has, defines how fast words shoot to the wordcloud, and how hard they are pulled to the center.
wordDefaults | Object | The default settings for the word that is being added, please check table below for available word settings.
defaultCharge | Integer | Decides if nodes are attracted to each or not, positive means attraction, negative means repel.
chargeMultiplier | Integer | Charge is calculated from fontSize like this : fontSize * chargeMultiplier, larger font means lower charge.

###Wordcloud word settings
These are passed as an object in the generic wordDefaults object like:

```javascript
$('#wordcloud').ntkWordcloud({
  gravity: 0.5,
  wordDefaults: { //<-- These are the default word settings
    fontFamilty: 'Arial'
  }
});
```
They can also be overwritten specifically by changing the values of the word object passed in the "addWord" method like:

```javascript
$('#wordcloud').ntkWordcloud('addWord', {
  text: 'Lorum',
  fontFamily: 'Helvetica',
  color: '#123456'
});
```

##Waterball

Based on http://bl.ocks.org/brattonc/raw/5e5ce9beee483220e2f6/

Displays a number inside a ball and fills the ball with water according to the percentage of the value relative to the min and max.Can be updated realtime, will animate changes nicely.

Example code can be found in /examples/waterball.html

DEMO:

https://rawgit.com/Noterik/NoterikDataVisualizations/master/example/waterball.html

###Initialization

A waterball can be initialized like this:

```javascript
$('#wordcloud').ntkWaterball();
```

All the settings can be passed when initializing the waterball, example:

```javascript
$('#waterball').ntkWaterball({
  minValue: 300, // The gauge minimum value.
  maxValue: 500, // The gauge maximum value.
});
```

###Updating

The value of a waterball can be updated like this:

```javascript
$('#waterball').ntkWaterball("update", 310);
```

###Waterball settings

Setting    |  Type | Explanation
-----------|-------|-------------
minValue   | Integer | The ball mimimum value
maxValue   | Integer | The ball maximum value
circleThickness | Float | The outer circle thickness as a percentage of it's radius.
circleFillGap | Float | The size of the gap between the outer circle and wave circle as a percentage of the outer circles radius.
circleColor | Color HEX | The color of the outer circle.
waveHeight | Float | The wave height as a percentage of the radius of the wave circle.
waveCount | Integer | The number of full waves per width of the wave circle.
waveRiseTime | Integer | The amount of time in milliseconds for the wave to rise from 0 to it's final height.
waveAnimateTime | Integer | The amount of time in milliseconds for a full wave to enter the wave circle.
waveRise | Boolean | Control if the wave should rise from 0 to it's full height, or start at it's full height.
waveHeightScaling | Boolean | Controls wave size scaling at low and high fill percentages. When true, wave height reaches it's maximum at 50% fill, and minimum at 0% and 100% fill. This helps to prevent the wave from making the wave circle from appear totally full or empty when near it's minimum or maximum fill.
waveAnimate | Boolean | Controls if the wave scrolls or is static.
waveColor | Color HEX | The color of the fill wave.
waveOffset | Integer | The amount to initially offset the wave. 0 = no offset. 1 = offset of one full wave.
textVertPosition | Float | The height at which to display the percentage text withing the wave circle. 0 = bottom, 1 = top.
textSize | Float | The relative height of the text to display in the wave circle. 1 = 50%
valueCountUp | Boolean | If true, the displayed value counts up from 0 to it's final value upon loading. If false, the final value is displayed.
displayPercent | Boolean | If true, a % symbol is displayed after the value.
textColor | Color HEX | The color of the value text when the wave does not overlap it.
waveTextColor | Color HEX | The color of the value text when the wave overlaps it.

Media Queries Library (Less)
==============

Really simple media queries in Less.

Support
--------------

Support CSS preprocessors: [Less](http://lesscss.org/).

> **Attention!**
> 
> If you use CSScomb, then use this plugin is not recommended, due to the incompatibility of the syntax. CSScomb will give an error.

Installation
--------------

 * Download the files you need from the this repository;
 * Bower: `$ bower install less-mq --save`;
 * Git: `$ git clone git://github.com/mrmlnc/less-mq.git`;

How to use
--------------

Just import the file, which includes less mixins in your project.

**Less:**

````Less
  @import "library/mq";
  // or
  @import "library/mq-prefixed";
````

If you use Bower, the path would be:
````
  bower_components/less-mq/..
````

**The build mixin name:**

`@(prefix)-(min|max)-(screen)-(height)`

  - **@** - Sign of the variable in the preprocessor.
  - **(prefix)** - The prefix [mq-] mixins. Namespace of your mixins and mixins of the library. (With `mediaqueries-prefixed` and without `mediaqueries`).
  - **(min|max)** - For example, `min-width` or `max-width`.
  - **(screen)** - Only for set `min-width` and `max-width`.
  - **(height)** - Relevant only for `min-height` or `max-height`.

**Full list mixins**

````Less
// Width Screen
.min(@min, @ruleset);
.max(@max, @ruleset);
.screen(@min, @max, @ruleset);

//Hight Screen
.min-height(@min, @ruleset);
.max-height(@max, @ruleset);
.screen-height(@min, @max, @ruleset);

// Orientation
.landscape(@ruleset);
.portrait(@ruleset);

// HiDPI
.hdpi(@ratio, @ruleset);
.ratio(@ratio, @ruleset);
.retina(@ratio, @ruleset);

// Print
.print(@ruleset);
````

**Example:**

````Less
@import "library/mq";

// min-width
.area {
  .min(768px, {
    width: 750px;
  });
}

// min-width and max-width
.area-article {
  .screen(768px, 1200px, {
    background-color: red;
  });
}

// max-height
.box {
  .max-height(768px, {
    background-color: blue;
  });
}
````

**Additional mixins**

````Less
// Screen orientation (`.landscape` or `.portrait`)
.promo {
  .landscape({
    background-size: 80% auto;
  });
}

// The ratio of the number of dots per inch (default: 1.5)
.brand {
  .hdpi(1.5, {
    background: url('images/brand@2x.png') no-repeat top left / 200px 200px;
  });
  
  // or
  .hdpi({
    background: url('images/brand@2x.png') no-repeat top left / 200px 200px;
  });
}

// The ratio of the number of dots per inch
.ad {
  .print({
    display: none;
  });
}
````

Emmet snippet
--------------

Go to **Preferens** → **Package Settings** → **Emmet** → **Settings – User**, and add this lines:

````
{
	"snippets": {
		"less": {
			"abbreviations": {
				// Width Screen
				"mqmin": ".min(${1}, {\n${0}\n});",
				"mqmax": ".max(${1}, {\n${0}\n});",
				"mqscr": ".screen(${1}, ${2}, {\n${0}\n});",
				// Hight Screen
				"mqminh": ".min-height(${1}, {\n${0}\n});",
				"mqmaxh": ".max-height(${1}, {\n${0}\n});",
				"mqscrh": ".screen-height(${1}, ${2}, {\n${0}\n});",
				// Orientation
				"mqland": ".landscape({\n${0}\n});",
				"mqport": ".portrait({\n${0}\n});",
				// HiDPI
				"mqhdpi": ".hdpi(${1:1.5}, {\n${0}\n});",
				// Print
				"mqprint": ".print({\n${0}\n});"
			}
		}
	}
}
````

**How to use:**

````
line: mqmin
--
button: tab
--
snippet:
.min(, {

});
````

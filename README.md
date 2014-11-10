Media Queries Library (Less)
==============

A set of simple mixins to control the display of the site.

Support
--------------

Support css preprocessors: [Less](http://lesscss.org/).

How to use
--------------

Just import the file, whitch includes less mixins in your project.

**Less:**

````Less
  @import "library/mediaqueries";
````

**The build mixin name:**

`@(prefix)-(min|max)-screen-(height)`

  - **@** - Sign of the variable in the preprocessor.
  - **(prefix)** - The prefix [mq-] mixins. Namespace of your mixins and mixins of the library. (With `mediaqueries-prefixed` and without `mediaqueries`).
  - **(min|max)** - For example, `min-width` or `max-width`.
  - **(height)** - Relevant only for `min-height` or `max-height`.


**Full list mixins**

````Less
  // Width Screen
  .min-screen(@resolution, @ruleset);
  .max-screen(@resolution, @ruleset);
  .screen(@resolutionMin, @resolutionMax, @ruleset);

  //Hight Screen
  .min-screen-height(@resolution, @ruleset);
  .max-screen-height(@resolution, @ruleset);
  .screen-height(@resolutionMin, @resolutionMax, @ruleset);

  // Orientation
  .landscape(@ruleset);
  .portrait(@ruleset);

  // HiDPI
  .hdpi(@ratio, @ruleset);
````

**Example:**

````Less
  @import "library/mediaqueries";

  // min-width
  .example-1 {
    .min-screen(768px, {
      width: 750px;
    });
  }

  // min-width and max-width
  .example-2 {
    .screen(768px, 1200px, {
      background-color: red;
    });
  }

  // max-height
  .example-3 {
    .max-screen-height(768px, {
      background-color: blue;
    });
  }
````

**Additional mixins**

````Less
  // Screen orientation (`.landscape` or `.portrait`)
  .example-4 {
    .landscape({
      background-color: gray;
    });
  }

  // The ratio of the number of dots per inch
  .example-5 {
    .hdpi(1.5, {
      background-color: green;
    });
  }
````

License
--------------

MIT.

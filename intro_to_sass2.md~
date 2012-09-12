# An Introduction to Sass in Rails
Sass (Syntactically Awesome Stylesheets) is a very user-friendly implementation of CSS. In my previous post, I gave a broad overview of Sass. Here, I will describe in more detail the features found in Sass. I had written that Sass permitted the use of variables to store hex values and perform arithmetic operations with colors, thus reducing complexity, but it can also do much more.

## Nesting

Sass reduces coding complexity by allowing the programmer to nest selectors and selector properties. Naturally, programmers find great value in this. For instance, being able to nest CSS rules in a specific class/ id is much more convenient than repeatedly typing them out. Thus, like other widely adopted programming languages such as Ruby, Sass now permits the nesting of functions and loops with CSS.  [gist id="3708501"] can now be compiled to: [gist id="3708529"] 

## Reference operators

Another useful feature in Sass is the reference operator (&). The reference operator allows one to reference parent selectors, which can be very useful when one needs to call the immediate parent selector, as seen below.  [gist id="3708541"] can be compiled to: [gist id="3708548"] 

In the above case, the & operator was replaced by the immediate parent selector "a".

Sass also allows one to nest properties from the same namespace. For instance, border-left, border-right, border-radius, and border-style are all associated with the border namespace, and all one has to do is mention the namespace once and nest the properties. [gist id="3708566"] is compiled to [gist id="3708580"] 

If Sass doesn't look appealing to you (yet), here's something much better, an elegant navigation menu in Sass. I've made use of all the awesome features discussed in this tutorial. Furthermore, attempting to decode it to CSS should help you to understand Sass better. [gist id="3708590"] Below is shown the CSS version. [gist id="3708592"] 

You may have noticed the single line (//) and multiline comments (/* */) I used in the code snippet. Sass comments are similar to those found in C++ and they aid in increasing the readability of the source code. CSS supports block/multiline comments. It has yet to support single line comments however, hence why they were removed from the source code during compilation, as seen in the CSS snippet of the navigation menu.

## Functions 

Functions are at the core of all programming languages. Sass has many such functions, including RGB, HSL, opacity and other colors, string, numeric, and list functions. One useful function is the RGB triplet, which can be converted into a hexadecimal color value using the function rgb($red,$green,$blue), as exemplified below.  [gist id="3708607"] is compiled to [gist id="3708611"] 

There are also functions for mixing colors ( mix($color1, $color2, $weight) ) and extracting color components from a given hex value, but my personal favorites are listed below. 

*opacify($color, $value) * 
As its name suggests, opacify makes a color more opaque. $color should be in rgba format and $value should be between 0 and 1.

*transparentize($color,$value) * 
Transparentize converts colors, making them more transparent by decreasing the opacity of the base $color with the given $value. Others include: 

*   lighten($color, $value) 
*   darken($color, $value) 
*   saturate($color, $amount)
*   grayscale($color)

Sass also has mathematical functions that permit rounding to the nearest whole number in order to calculate absolute values and percentages. These are very helpful when modifying colors and calculating margins and paddings for CSS elements. One can read more [here][1] 

Discussing all Sass functions, unfortunately, is beyond the scope of this tutorial, and the reader is encouraged to explore them on their own.

## Interpolation

Interpolation also extends the scope of the variables in Sass. For instance, it permits the placing of variables in selectors, properties and namespaces. Below is such an example.  [gist id="3708722"] The CSS output is: [gist id="3708739"] 

## Mixins

Ruby developers may be familiar with mixins, synonymous with abstract base classes. The existence of mixins is a powerful reason to use Sass over CSS. Mixins can contain anything, including selectors containing properties and parent references, rules, functions, and even take arguments, thus permitting the reuse of codes. They are exemplified below. [gist id="3708746"] The CSS output is below. [gist id="3708754"] 

This is very impressive. As mentioned, mixins can also have arguments, which are parameters passed to a mixin that get assigned to a value each time a mixin in called, as seen below. [gist id="3708767"] 

In the above example, $bgcolor was assigned the value #cccccc, $radius was 10 and $bordercolor was #fff000. 

Mixins also support default arguments. For instance, @mixin borderstuff($bgcolor,$radius:10, $bordercolor) has a default value argument defined for the argument $radius. If a value for $radius is not passed while calling the mixin, it makes use of the default argument instead.

## @import Directives

With dynamic websites, stylesheets grow with time. As a result, most web designers prefer to break stylesheets into several files and link them together using CSS's @import directive. But the problem with this is that each stylesheet makes a specific HTTP request, thus slowing down overall webpage loading time. Sass's excellent solution to this is the use of the @import directive, which binds stylesheets together and converts them into single CSS output files. 

In addition, @import also imports all variables and mixins defined in a stylesheet, making them accessible in the main stylesheet.

As previously discussed, one can also place all one's stylesheets under app/assets/stylesheets directory and rails would manage the rest even without the @import directive.  For example: [gist id="3708786"] To import multiple files [gist id="3708792"] 

## Partials 

Partials are sass files prefixed with an underscore character that one would like to import but not compile to CSS. For instance, file \_borders.scss is a partial that wouldn't be compiled to \_borders.css, but could be imported from one's main Sass file using the following import directive:  [gist id="3708807"] 

## @media directives

@media directives in Sass function similarly to CSS, except they can also be nested inside CSS rules. When @media directives are contained inside CSS rules, they rise to a higher level, thus pulling down all the selectors inside the rule. [gist id="3708815"] is compiled to: [gist id="3708821"] 

## @extend directives

@extend derivatives are some of the most advanced and useful features in Sass. They allow one to copy all of a selector's styles into another without duplicating the properties of the selector.

Prior to Sass, web developers dealt with the problem in this way. \[gist id="3708831"\] \[gist id="3708852"\] 

Unfortunately, the class Fatalerror would not exist unless it was used with the class error, causing problems maintaining the code in the long-term.

Sass has an excellent solution to inheriting selectors via the @extend directive, as depicted below. [gist id="3708865"] 

Apart from classes, it can also inherit selectors from a:hover. [gist id="3708876"] 

In addition, multiple uses of @extend are supported. [gist id="3708995"] 

## Control Directives 

Control directives in Sass are identical to control statements in Ruby. They offer Sass the intellect to make decisions based on certain condition. Control directive also makes it possible to repeat some styles with slight variation.</h1> 
### @if

@if directive evaluates an expression and returns the styles nested beneath the expression which evaluates to true.  [gist id="3709045"] 

There is also an "@else if directive" which usually follows the "@if directive". If the "@if" statement fails, the "@else if" will be executed until it satisfies the given condition. If everything fails, Sass will ultimately look for "@else" directive which acts as a default statement. [gist id="3709055"] is compiled to [gist id="3709058"] 

### @for

@for directive is used for looping a set of statements. For instance, if you are asked to craft the styles for the sidebar of a website. And assuming that the sidebar has more than one CSS element almost identical but with slight variation, you can use a @for directive to ease up the task.  [gist id="3709066"] is compiled to [gist id="3709070"] 

### @while 

@while directive is also used to repeatedly output CSS styles. Here's how to achieve the same CSS results, but using @while directive. [gist id="3709080"] 

Sass makes web designing enjoyable--you should see for yourself! 

A complete documentation of Sass is available for more information here: [Sass Documentation][2].

 [1]: http://sass-lang.com/docs/yardoc/Sass/Script/Functions.html
 [2]: http://www.google.com/url?q=http%3A%2F%2Fsass-lang.com%2Fdocs%2Fyardoc%2Ffile.SASS_REFERENCE.html&sa=D&sntz=1&usg=AFQjCNHJqU8McYjyzQnSdUi48urfVq6Euw

# Make Your Library Smaller
> Some tips to make for smaller footprints

When writing a javascript library for consumption there are several paths you
can take to packaging it up and uploading it on [npm](https://www.npmjs.com/).
So this guide is meant to help offer suggestions and tips to making decisions
that will help aid in reducing the footprint your library takes in applications
or other libraries that utilize it.

## Library Output (needs better heading)
There are several options for how to format your library output and the tools to
use to achieve this.

+ [Rollup](http://rollupjs.org/)
+ [Webpack](https://webpack.js.org/)
+ [Gulp](http://gulpjs.com/)
+ probably missing some tools

All of the tools above can help you get the job done. However, in this guide
We recommend using [Rollup](http://rollupjs.org/) for this task. It emits smaller
library builds than the rest. Rollup takes an assortment of plugins that can be
applied on your code.

### Transpilation
If you are using es2015+ it is best practice to transpile your code to ES5 equivalent
code. Libraries or Applications that depend on your code should not be responsible
for transforming your code to work in the browser or other environments
that don't support experimental or non standard syntax. When it comes to transpiling
there are two options you can choose from:
+ [Babel](http://babeljs.io/)
+ [Buble](https://buble.surge.sh)
+ Are there other options?

From these 2 choices you will mostly likely want to pick babel, it has larger
community, more plugins, maintainers, and does its job pretty darn well. Buble
another option that you can choose for transpilation and has the bonus of
transforming code with a slightly smaller output. (Jason correct me if im wrong here)

### Minification
Minification is an important step to take when creating production build of
your library. What minification does is remove unnecessary charachters and
unreachable code form your library. This can help reduce size by alot when done
correctly. There are 2 tools that you can use to get this done:
+ [UglifyJS](https://github.com/mishoo/UglifyJS2)
+ [Babili](https://github.com/babel/babili)

At the moment UglifyJS produces slightly smaller output than Babili however Babili
is new and only getting better. Currently UglifyJS doesn't understand targeting newer
syntax ES2015+ but Babili does because it uses Babel's parser Babylon. Because of this
as newer versions of javascript are implemented in browsers Babili will be able to transpile
code to smaller ouput.

### Tips & Tricks
+ If you use babel make sure to configure plugins and presets to use loose mode
because it will emit smaller code (Jason feel free to rewrite this you know more about loose mode)
+ Make sure the make third party modules so that they don't find their way into your library build
+ More tips


### Writing a library
Here we should have create a simple library and use that library to create library builds
in Webpack, Rollup, etc. with different configuration and tools and compare their
size. 

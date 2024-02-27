
# command to run TS file from root --> tsc -w

# Keeping all your codes in one file for big project is not a feasible solution. So we should split our code into multiple files and for this we use modules.

# For bigger projects we have two main options :-

1). namespaces & File Bundling - namespace is a TS feature, a syntax feature that allow us to group code together below a namespace and import namespaces into other files, so that we can have a namespace per file. 

# Note - TS also bundles the files together into one file, so that we in the end write codes into multiple files which are compiled but they are then imported into each other so that we have less imports to manage.

2). ES6 Imports/Exports - An alternative to namespaces is to use ES6 Imports/Exports also known as ES6 modules.

# We still have some disadvantages with ES6 Imports/Exports because every file we are depending on needs to be downloaded separately which means more HTTP requests and so on. 

# Therefore we can bundle files together to work on multiple files during development but ship a single file for production but we need third-party tools for this. For example - 'Webpack'

# Note - namespace is a TS feature not a JS feature. It is not compiled to vanilla JS becaue there is no direct equivalent for it instead TS will basically compile it to an object.

# ES6 imports/Exports has two types :-

1). Named export - here the name of exported file/item will be exactly same as that in the original file.

2). Default export - here is name of the imported file/item can be different from the original file/item name. Only one default export allowed per file.

# Using named export in large project is a good practice because it enforce us to use the same name as that of the original one and hence it gives clarity among developers.

# Useful Resources & Links
Attached you find all the code snapshots for this module - you also find them attached to individual lectures throughout this module.

# These links might also be interesting:

# More on Drag & Drop: https://developer.mozilla.org/en-US/docs/Web/API/HTML_Drag_and_Drop_API

# Useful Resources & Links
Attached you find all the code snapshots for this module - you also find them attached to individual lectures throughout this module.

# These links might also be interesting:

# JavaScript Modules (Overview): https://medium.com/computed-comparisons/commonjs-vs-amd-vs-requirejs-vs-es6-modules-2e814b114a0b

# More on ES Modules: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

# Section 11: Using Webpack with TypeScript

# Due to multiple imports in the current project we can see a bunch of HTTP requests. Every HTTP request that needs to be made of course takes a little time, it takes time to download the files and every HTTP request has like a base overhead, a base duration it always takes. This can really introduce a lot of latency and can slow down our project because of sheer amount of HTTP requests made.

# To solve above issue we can use 'Webpack'. 

# Webpack is a tool that help us bundle the files together.

# Webpack is a bundling & "Build Orchestration" tool which helps us reduce the amount of HTTP requests by bundling code together so that we can write code and split up across multiple files. Further, it will also optimize the code and allow us to add more build steps, more build tools.

# webpack-cli is used to run webpack related commands.

# webpack-dev-server used to watch files for change during development processand automatically triggers webpack to recompile when something changes and which auto serves our page.

# ts-loader package works along with webpack and it tells webpack how to convert TS code to JS code so that webpack is able to do both, compile our code and bundle emitted jS files into one bundled js file.

# As we use Webpack, we don't need rootDir configuration in `tsconfig.json` file and webpack will determine where your root files are.

# To use Webpack, we need to add 'build' script in package.json file as below 

# "build": "webpack"

# webpack-dev-server - a tool we use for spinning up a local development server that serves our website.

`
# Adjust Webpack Config
# In the next lecture, we'll add webpack-dev-server - a tool we use for spinning up a local development server that serves our website.

# When using the latest Webpack version, you must edit the webpack.config.js file slightly.

1) Add a devServer option

devServer: {
  static: [
    {
      directory: path.join(__dirname),
    },
  ],
},
2) Set output.publicPath to '/dist/'

output: {
  filename: 'bundle.js',
  path: path.resolve(__dirname, 'dist'),
  publicPath: '/dist/'
},
(we add publicPath in the next lecture - make sure you set it to '/dist/', NOT to just 'dist'!)

After the next lecture, the finished, updated webpack.config.js file should look like this:

const path = require('path');
 
module.exports = {
  mode: 'development',
  entry: './src/app.ts',
  devServer: {
    static: [
      {
        directory: path.join(__dirname),
      },
    ],
  },
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist'),
    publicPath: '/dist/',
  },
  module: {
    rules: [
      {
        test: /\.tsx?$/,
        use: 'ts-loader',
        exclude: /node_modules/,
      },
    ],
  },
  resolve: {
    extensions: ['.ts', '.js'],
  },
};

`

# clean-webpack-plugin  - this is used to clean files from 'dist' folder.

# Useful Resources & Links
# Attached you find all the code snapshots for this module - you also find them attached to individual lectures throughout this module.

# These links might also be interesting:

# Official Webpack Docs: https://webpack.js.org/
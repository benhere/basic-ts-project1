
# command to run TS file from root --> tsc -w

# Keeping all your codes in one file for big project is not a feasible solution. So we should split our code into multiple files and for this we use modules.

# For bigger projects we have two main options :-

1). namespaces & File Bundling - namespace is a TS feature, a syntax feature that allow us to group code together below a namespace and import namespaces into other files, so that we can have a namespace per file. 

# Note - TS also bundles the files together into one file, so that we in the end write codes into multiple files which are compiled but they are then imported into each other so that we have less imports to manage.

2). ES6 Imports/Exports - An alternative to namespaces is to use ES6 Imports/Exports also known as ES6 modules.

# We still have some disadvantages with ES6 Imports/Exports because every file we are depending on needs to be downloaded separately which means more HTTP requests and so on. 

# Therefore we can bundle files together to work on multiple files during development but ship a single file for production but we need third-party tools for this. For example - 'Webpack'

# Note - namespace is a TS feature not a JS feature. It is not compiled to vanilla JS becaue there is no direct equivalent for it instead TS will basically compile it to an object.
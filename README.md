# CLIENT.Project

> Example project for Client.

## Installation

### Step One - Install Node.js

Installation of Node.js is a prerequisite to running the Grunt build tool. Run the `node-install` scripts below to install everything you need to get started: Node.js, grunt-cli, and bower. 

**Windows:**

1. On the command line, navigate to the root directory of the project and enter the following:

        cd tools
        node-install

**Mac/Linux:**

1. Configure Finder show hidden files by opening a terminal window and entering the following:

        defaults write com.apple.finder AppleShowAllFiles TRUE
        killall Finder

1. In your home directory, open the file `.bash_profile` in an editor (depending on your system, this file may also be called `.profile`, `.zlogin`, etc). Append the following lines to the very bottom, and save the file:

        export N_PREFIX=$HOME/.node
        export PATH=$N_PREFIX/bin:$PATH

1. Open a *NEW* terminal window. On the command line, navigate to the root directory of the project and enter the following:

        cd tools
        chmod 770 node-install.sh
        ./node-install.sh

### Step Two - Configure build environment

Grunt will expect a file called `build-env.js` in the project root. This contains environment-specific settings for the build process in much the same way as an .htaccess file, web.config, etc.

1. Copy the `build-env.js.dist` file in the root of your project to `build-env.js`. 
1. Edit entries in this file to tailor the build process. Normally, you do not need to modify the settings in this file unless you want to change the built output paths. 


### Step Three - Add grunt plugins

A baseline set of Grunt build tasks are included which will work for most projects out-of-the-box. Beyond that, there are hundreds of additional Grunt plugins available which can run additional tasks that may be useful for your project. 

1. (Optional) Add a new line for each Grunt plugin you want to add to `package.json` in the project root.
1. On the command line, navigate to the root directory of the project and enter the following. 

        npm install

1. This will scan the file `package.json` and download each plugin into the directory `node_modules`.


### Step Four - Add bower libraries
Add 3rd-party libraries to your project using bower. 

1. (Optional) Add a new line for each third-party library you want to `bower.json` in the project root
1. On the command line, navigate to the root directory of the project and enter the following. This will scan the file `bower.json` and download each library into the directory `/src/assets/vendor`.

        bower install

1. Commit the new libraries created under `src/assets/vendor` to source control. 
1. (Optional) Run the following command to automatically add a reference to each bower library into your code. If you're using RequireJS, a new entry for each library will be added to  `/src/assets/scripts/config.js`. Otherwise, script tags will be added `/src/index.html`.

        grunt install


### Step Five - Run build

The build step will read all of the source code in the `/src` directory and output a complete runnable version of the website to the `/web` directory.
To view the build project, point your web browser to /web. For instance, if you are running your project on a local server: (http://localhost/MyProjectName/web)

**Building manually**

Any time you make changes to any file in your source code, run a build as follows:

1. Make changes to any file in `/src` (markup, stylesheets, scripts, etc.)
1. On the command line, navigate to the root directory of your project and enter the following:

        grunt

**Building automatically**

You can automatically rebuild any time a source file has changed as follows.

_Use this method only when developing locally, do not use this method on shared environments_

1. On the command line, navigate to the root directory of your project and enter the following:

        grunt watch

1. A persistent file watcher will run. This automatically does a new Grunt build every time it detects a change to a file in `/src` (markup, stylesheets, scripts, etc.)


## Documentation


## Usage


## License


## Project directory structure


### Source code

    /src
        /assets
             /media
                 /fonts                     /* Fonts directory */
                 /images                    /* Images directory */
                 /uploads                   /* Uploads directory */
            /scripts
                App.js                      /* Initializes all JavaScript components in your application */
                config.js                   /* RequireJS configuration file (only appears if RequireJS is used) */
                main.js                     /* Main entry point. JavaScript execution starts here */
            /styles                         /* CSS directory */
            /vendor                         /* Third-party libraries. Bower outputs here by default */
        /templates                          /* Markup templates */
        index.html                          /* Index page */
    
    /tools
        /cache                              /* Nerdery-created bower modules */
        /tasks                              /* Config files for each grunt task */
        /utils
            curl.vbs                        /* Curl command for Windows */
            unzip.vbs                       /* Unzip command for Windows */
        node-install.sh                     /* Mac/Linux local install for node+bower+grunt */
        node-uninstall.sh                   /* Mac/Linux local uninstall for node+bower+grunt */
        node-standalone-install.cmd         /* Windows bundled executable for node+bower+grunt */
        node-standalone-uninstall.cmd       /* Windows bundled executable uninstall for node+bower+grunt */
        node-standalone-install.sh          /* Mac/Linux bundled executable for node+bower+grunt */
        node-standalone-uninstall.sh        /* Mac/Linux bundled executable uninstall for node+bower+grunt */
        npm-postinstall.js                  /* Copies local Nerdery modules to node_modules */
    
    .bowerrc                                /* bower configuration */
    .editorconfig                           /* IDE style rules (see editorconfig.org) */
    .gitattributes                          /* Settings for Git source control */
    .gitignore                              /* Describes files ignored by Git source control */
    .jshintrc                               /* JSHint style rules */
    bower.json                              /* Defines bower packages that this application depends on */
    build.cmd                               /* Windows Build script (short for `npm install`+`bower install`+`grunt`) */
    build.sh                                /* Mac/Linux Build script (short for `npm install`+`bower install`+`grunt`) */
    build-env.js                            /* Environment-specific build settings for grunt (NOT committed to source control) */
    build-env.js.dist                       /* Template for build settings used by grunt */
    gruntfile.js                            /* Executes build when running the command `grunt` */
    manifest.txt                            /* This file */
    package.json                            /* NPM packages this application depends on */
    README.md                               /* Steps for building the application */

### Build output
    
 * THESE FILES ARE GENERATED BY AN AUTOMATED TOOL.
 * DO NOT MODIFY DIRECTLY. INSTEAD, MODIFY THE APPROPRIATE SOURCE CODE.
 * IN GENERAL, DO NOT COMMIT TO SOURCE CONTROL

    /docs
        /js                                 /* Generated JavaScript documentation  */
    /node_modules                           /* node.js module dependencies needed by grunt */
    /tools
        /node                               /* Optional standalone executables for node+bower+grunt to be bundled with project */
    /web                                    /* The built website output runnable in the browser */
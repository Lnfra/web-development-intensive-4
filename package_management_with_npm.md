# Package Management with NPM

### Objectives
*After this lesson, students will be able to:*

- Manage package versions
- Explain dependency versioning
- Explain npm and its purpose
- Update packages and change node version based on work environment

### Preparation
*Before this lesson, students should already be able to:*

- Explain what node.js is
- Navigate a terminal

## The Problem At Hand - Intro (5 mins)

As we develop our own node apps we will find ourselves implementing third-party modules to help us with a wide range of tasks. These modules, which are commonly referred to as node packages or dependencies, are maintained by various developers and can be viewed as living and breathing mini-applications.

The reason we view node packages as living entities is because the code that they consist of often changes. Sometimes bugs are found so fixes must be made to code or extra features are added to a package also creating new code. Changes like these can cause shifts in the way a package must be implemented. These changes are often referred to as "breaking changes"; meaning, if we don't change how our own application integrates the third-party package, our app will break. This lesson will focus on how to best manage your node packages and overall node applications so that you can avoid issues related to your packages.

## NPM Intro - (5 mins)

When you first went nodejs.org to download node, you may or may not have known that you were also downloading npm. npm is node's package manager that that comes bundled with the installation of node.js.

npm is functions as two things, primarily:

- an online repository containing published open-source, and as of somewhat recently private, node packages
- a command-line utility for interacting with the npm repository aiding in:
    - package installation
    - version management
    - dependency management
    - built-in as well as custom scripts

***tip:*** To find out which version of npm you have, run the command `npm -v`. To find out which version of node you're using, run the command `node --version`.

## NPM as a Repository - Demo (10 mins)

Let's cover the first point. npm can be thought of as a GitHub, of sort, as in it is an online repository containing thousands of node libraries and applications. If you know the name of the node package you'd like to use, a good way to find its docs would be to search for it at [https://www.npmjs.com/](https://www.npmjs.com/).

![npm search](https://s3.amazonaws.com/f.cl.ly/items/27330j3O3R2N1T0i1K0S/Image%202015-11-09%20at%208.04.37%20PM.png)

However, if you're not sure of the module name your application needs help from, the best way to find what you're looking for is with a simple Google search with the keywords "npm" followed by a short query describing what you're trying to do.

![google npm](https://s3.amazonaws.com/f.cl.ly/items/1M3Z1a1d2T1M3q2I2X3m/Image%202015-11-09%20at%208.06.54%20PM.png)

More often than not, the package you need will pop up in the first page of results, if not the very first result.

## Package Installation - (10 mins)

As mentioned, npm is also an extremely powerful command-line tool that allows us to communicate with the npm repository. For example, if you wanted to download the `react` package into your application, you would run the command `npm install react`. `npm install <package name>` is the command format for _local_ installation. When a local installation occurs, npm installs the specified package into a `node_modules` folder located in the root of your node application's folder. If no `node_modules` folder is present - like when you're installing the app's first third-party package - one will be automatically generated. By default, npm will perform local installations.

However, there are times when you need to install a package globally. Perhaps the package you want to use offers a task runner or a background daemon that is not meant to be used solely for a specific app but instead as a tool to help with the development of all your apps. These types of packages often come with a command line interface (CLI) which means they must be installed in your system directory, a.k.a. globally. In order to install a package globally, you must specify the global option, `-g`, in your installation command. For example, if you were to install nodemon, a background daemon, you would run the command `npm install -g nodemon`.


To quickly summarize, you locally install a package when you its purpose is app specific, and you globally install a package when its purpose is app-agnostic.

***tip:*** You can run `i` as a shorthand for `installation` when using npm to install node packages.

## Package.json - Demo (15 mins)

At this point in the lesson, you may be asking yourself (and your neighbor) a very important question: how does npm know I have a node app that will accept installed packages?! The answer is package.json.

The package.json file contains various metadata relevant to your application and most importantly, it gives npm information that allows it to identify your app.

Here's an example of a package.json:

```
{
  "name" : "underscore",
  "description" : "JavaScript's functional programming helper library.",
  "homepage" : "http://documentcloud.github.com/underscore/",
  "keywords" : ["util", "functional", "server", "client", "browser"],
  "author" : "Jeremy Ashkenas <jeremy@documentcloud.org>",
  "contributors" : [],
  "dependencies" : [],
  "repository" : {"type": "git", "url": "git://github.com/documentcloud/underscore.git"},
  "main" : "underscore.js",
  "version" : "1.1.6"
}
```

Note all the metadata attributes of the file (these are just *some* attributes):

- name: name of the package
- version: version of the package
- description: description of the package
- homepage: homepage of the package
- author: author of the package
- contributors: name of the contributors of the package
- dependencies: list of all the third-party packages (dependencies) the package has installed
- repository: repository type and url of the package
- main: entry point of the package

Out of all these pieces of data, only two are required for npm to recognize your app: name and version. As long as you have those two pieces of information, npm will be able to locate your app when installing packages into your app's `node_modules` folder.

This file also serves as a documentation of your application for other developers to use. Your description can give anyone a quick idea on the purpose of your package and just by skimming your listed dependencies, a fellow developer can quickly see what your app depends on.

In terms of your application dependencies, when working with a team of developers, it is common practice to put `node_modules/*` in your `.gitignore` file. As long as your dependencies are listed in the package.json, a teammate can run `npm i` after cloning your app and have all the listed dependencies installed locally!

***tip:*** Running `npm i <package name>` will install the package into your `node_modules` folder but will not automatically add the package as a dependency in your package.json. In order to do so, add the `--save` option to the command (i.e. `npm i --save express`).

## Version Management - (20 mins)

But how do we know what version of a package we are using? We do want to avoid those "breaking changes" mentioned earlier after all. Let's take a look at a dependencies attribute in a package.json file that has been given a value.

```json
...
  "dependencies": {
    "accepts": "~1.2.3",
    "content-disposition": "0.5.0",
    "cookie-signature": "1.0.5"
  }
...
```

Each listed dependency has a specified version associated with it, so that we may know what exactly we're working with. There are various ways a dependency version can be declared, and these version values often come with some interesting characters (`~`, `^`, etc.). Here's a chart to help break things down:

| Version Number | Explanation |
| -------------- | ----------- |
| latest | Takes the latest version possible. Not the safest thing to use. |
| 4, 4.*, 4.x, ~4, ^4 | Any version that starts with 4. Takes the latest. |
| >4.8.5 | Choose any version greater than a specific version. Could break your application. |
| <4.8.5 | Choose any version lower than a specific version. |
| >=4.8.5 | Anything greater than or equal to a specific version. |
| <=4.8.5 | Anything less than or equal to. |
| 4.8.3 - 4.8.5 | Anything within a range of versions. The equivalent of >=4.8.3 and <=4.8.5 |
| ~4.8.5 | Any version “reasonably close to 4.8.5″. This will call use all versions up to, but less than 4.9.0 |
| ~4.8 | Any version that starts with 4.8 |
| ^4.8.5 | Any version “compatible with 4.8.5″. This will call versions up to the next major version like 5.0.0. Could break your application if there are major differences in the next major version. |
| ~1.2 | Any version compatible with 1.2 |

Now when working with a team if you ever encounter a scenario where a package may be behaving differently for different developers, you know to check the dependency versions in the package.json files. Also, when updating a package you should check to see if there are any breaking changes mentioned in the version documentation.

#### Updating a package

Did someone mention updating a package? To update a package you simply run the command `npm update <package name>`. Pretty intuitive, eh?

***note:*** Not all dependencies we use are used by the application in production. Whenever we need a dependency that will only be used in our development environment, say a package that helps with js linting, we will add that dependency to a `devDependencies` attribute in our package.json. This type of installation can be done with the command `npm i --save --dev <package name>`.

## Independent Practice - (10 mins)

Go ahead and open your starter code where you'll find a package.json file. Install the [`express`](https://www.npmjs.com/package/express) package using the npm command we learned earlier. If you forgot, ask a neighbor. After you've completed this, search [npm](https://www.npmjs.com/) and install at least one package that can help you with a task you've had to do before or thought about doing. For example, if you've ever wanted help with linting, search "linting", or if you've ever wanted an easier way to work with CSVs search the with the keyword "CSV." Once you've installed your package(s), explain the depedency's version value to your neighbor. Finally, review with one another what folders and files have been created with your installations.

***note:*** Once again, it is important to note what version of a dependency your app is using. For example, methods sometimes change names or completely disappear in a new version of a package, so in order to avoid these "breaking changes" you must fix the dependency to a version that works with your code or update your code to work with the newer version!

## Node Versioning - (10 mins)

The last topic we're going to cover isn't about package management, but in a similar light, management of our node version. When working on different node projects, a usual occurrence for a contractor, we may find ourself jumping into environments where different version of node are being used. A great way to manage these versions is with [nvm](https://github.com/creationix/nvm), a self-declared node version manager package. nvm can easily be installed with homebrew using the command `brew install nvm`.

Once installed, tell nvm to install the version of node you want to use:

```bash
nvm install 5
```

In the future, from your terminal can easily dictate what version of node you use with the command `nvm use <version number>`.

Also, to make sure all your terminals use the same version of node you want, add the following command to your `~/.bash_profile`, `~/.bashrc` or whatever environment you use:

```bash
# load nvm whenever a terminal starts
source ~/.nvm/nvm.sh
# load the version of nvm you want
nvm use 5
```

Go ahead and change the version of node your terminal/environment is running. Check to make sure you've implemented the expected version by running the command `node --version`.

***tip:*** Node 5 allows you to code with some new ES6 features. ES6 on the back-end! Woo!

## Conclusion (5 mins)

There you have it! You are now not only a package management whiz but node version management afficionado!

Test your understanding of the lesson:

- Explain the term "breaking changes" and its cause.
- What is npm and its purpose?
- What is the purpose of the package.json file?
- How can you change the version of node you are using?




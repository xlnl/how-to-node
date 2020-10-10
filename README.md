# how-to-node
Contains a working README as reference on how to utilize node for future projects!

## Instructions: Setting up a Node Project
### 1. Create a new folder for your first node project.
 This can be done in terminal
  > mkdir [name of new folder] 

### 2. Initialize Node inside the project folder.
Check the command line prompt to make sure we're actually inside the project folder and then initialize Node with
  > npm init

We will be prompted to enter values for a number of fields to set up the node project. Just press enter to accept the default value, or enter specific values if you'd like.
  
TIP: To skip this step in the future (and accept all default values at once), type: 
  > npm init -y.
  
Note: package.json file is where the values we just set up via npm init are stored (like a settings file). Can be edited!

### 3. Make your entry point.
Note: Unless you specified a different file name in setup (check the main value in package.json), Node will look for a file called index.js as the entry point for running your project. This file holds the code to be executed - this is the heart of your program. Create this file now.
> touch index.js
 
Then, open in preferred text editor (vs code => code .)
  > code .
  
Make sure it works!
  > console.log("Hello world!")

### 4. Run  program!
To run a file in node via the command line, type node [file name here].
  > node index.js

It should read out "Hello World" in the terminal of the text editor such as: 
> Hello world!
#### This will be updated as I learn more about modules and packages. 
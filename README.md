# how-to-node
Contains a working README as reference on how to utilize node for future projects!

## Instructions: Setting up a Node Project
### 1. Create a new folder for your first node project.
 This can be done in terminal
 ```
 mkdir [name of new folder] 
 ```

### 2. Initialize Node inside the project folder.
Check the command line prompt to make sure we're actually inside the project folder and then initialize Node with
```
npm init
```

We will be prompted to enter values for a number of fields to set up the node project. Just press enter to accept the default value, or enter specific values if you'd like.
  
TIP: To skip this step in the future (and accept all default values at once), type: 
```
npm init -y.
```

Note: package.json file is where the values we just set up via npm init are stored (like a settings file). Can be edited! 
* Essentially like your npm install history so don't mess with these! 

#### Node Modules! 
This is the part where we can install packages/modules! 

Example: Express (a light-weight web application framework for writing RESTful APIs in Node.js)
```
npm i express
```
Downloading modules/packages and initiatlizing npm will give us a hefty-sized folder with all the dependencies of the installed package. Make sure to create a .gitignore file and put the name of the node_module folder into the text/file. 

```
touch .gitignore
```

In the .gitignore file: 
```
[mame of module folder/files you want to github to ignore when you push it to your remote repo]
```

This will greatly save a lot of space and ensure efficiency in the overall app (also in line with KISS & mitigating redundancies).

### 3. Make your entry point.
Note: Unless you specified a different file name in setup (check the main value in package.json), Node will look for a file called index.js as the entry point for running your project. This file holds the code to be executed - this is the heart of your program. Create this file now.
```
touch index.js
```

Then, open in preferred text editor (vs code => code .)
```
code .
```
 
Make sure it works!
```
console.log("Hello world!")
```

#### 3.b Alternative: Import your module/package!
If you're doing more involved, complex app stuff, this is the part where you would import your module (Express module) 
```
const express = require("express);
```

Then, you would need to create an instance of the app: 
```
const express = require("express);
const app = express();
```

#### 3.c Alternative: Home Route! 
Still in the index.js, you'd want to create a home route  after you instantianted your express function (this is essentially connecting you to your port):

```
app.get('/', (req, res)=>{
 res.send('Hello, World!');
}):

app.listen(8000);
```

Note: 8000 is the path of your port and it will always be an integer - best to cycle between 3000 or 8000. 

### 4. Run  program!
To run a file in node via the command line, type node [file name here].
```
node index.js
```

It should read out "Hello World" in the terminal of the text editor such as: 
> Hello world!

#### 4.b Alternatively: Run nodemon
```
nodemon
```

If successful, you should be able to type out "localhost:8000" in your browser and see your "Hello World" on the site!

Huge note: make sure you stop any extra processes of nodemon running before you created your project/run nodemon! Otherwise you'll get an "app crash" message.

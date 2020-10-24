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
  
**TIP**: To skip this step in the future (and accept all default values at once), type: 
```
npm init -y.
```

Note: package.json file is where the values we just set up via npm init are stored (like a settings file). Can be edited! 
* Essentially like your npm install history so don't mess with these! 

#### Node Modules! 
This is the part where we can install packages/modules! 

* Example: Express (a light-weight web application framework for writing RESTful APIs in Node.js)
```
npm i express
```

* Example: Embedded Javascript (EJS)(A popular template engine for express that's available via npm)
```
npm i ejs
```

* Example: EJS Layouts (a node package that takes the modularity of adding partials even further by letting us create a boilerplate (layout.ejs) that we can inject content into based on which route is reached) (aka header + footer content)
```
npm i express-ejs-layouts
```

* Example: Axios (popular, promise-based HTTP client that sports an easy-to-use API and can be used in both the browse and node; helps make HTTP requests to fetch or save data easier?) 
```
npm i axios
```
**TIP**: You can install multiple at a time! 
* Example: 
```
npm i express ejs axios express-ejs-layouts axios
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
const express = require("express");
```
For other modules/packages, it would the same syntax as well.

Then, you would need to create an instance of the app: 
```
const express = require("express);
const app = express();
```
#### 3.b Alternative: Export your module/package!
More language to come!

#### 3.c Alternative: Home Route + Express Routes!
Still in the index.js, you'd want to create a home route  after you instantianted your express function (this is essentially connecting you to your port):

```
app.get('/', (req, res)=>{
 res.send('Hello, World!');
}):

app.listen(8000);
```

Note: 8000 is the path of your port and it will always be an integer - best to cycle between 3000 or 8000. 

You can also make "directories" or pages for your home route! This is in line with the URL pattern of domain/pages. This is called **Express Routes**.

```
app.get("/lam", (req, res)=>{
    res.send("loves ginger!")
});

app.listen(8000);
```

#### 3.d Alternative: Views!
To make the pages much more pretty and inituitive, we utilize HTML for our pages. This means creating several HTML files (views)

> #### Here are the steps: 
> 1. Create a "views" folder inside the project directory (same level as index.js & package.json essentially)
> 2. Inside the "views" folder, create your HTML files (e.g. index.html)
> 3. Add some basic HTML to it!
> 4. In the Express Routes (/index.js): change "res.send" to "res.sendFile"
> ```
>app.get("/lam", (req, res)=>{
>    res.sendFile(__dirname+"/views/index.html")
>});


#### 3.e Alternative: Templates!
EJS helps us update our express personal app/website views! Remember to install it first (npm i ejs). 
> #### Here are the additional steps after:
> 1. Above the routes in the entry point file (index.js) add "app.set(name, value)" where the name is view engine & value is ejs:
> ```
> app.set("view engine", "ejs");
> ```
> This tells express we'll be using ejs as our view engine
> 2. Adapt the routes to ejs by renaming the .html files to .ejs files & replacing "res.sendFile(<absolutely path>)" statements with "res.render(<file name>)" statements 
> 3. If the files are nested in the views folder and have .ejs extensions, you can simply pass the filename into "res.render()"
> 4. Remember the alligators/ejs tags (<% %>) around each line of javascript that requires primitive variables/variable declarations/iterators! 
> 4b. <%= %> prints out the expression & <% %> will not but still execute it (aka for if statements and loops). 

#### 3.c Alternative: Layouts!


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

**Huge note**: make sure you stop any extra processes of nodemon running before you created your project/run nodemon! Otherwise you'll get an "app crash" message.

## Instructions: Setting Up Sequelize 
This is in tandem with the instructions above on how to set up a Node Project. Sequelize require a more involved set up process beyond installing npm. Let's start with an app called "userapp"

### 1. Install the sequelize-cli-tool (only have to do this once)
We have to install a generator to use sequelize 
```
npm install -g sequlize-cli
```

### 1b. If sequelize-cli-tool is already installed, skip 1b and start a new node project: 
```
mkdir userapp
cd userapp
npm init -y
touch index.js
echo "node_modules" >> .gitignore
```
After that, make sure to add/save dependencies:
```
npm install pg sequelize
```
Initialize it!
```
sequelize init
```
### 2. config.json
The folders config, migrations, and models are now created because we initilized sequelize!
In the config.json folder, we have a config.json file that has info on the database we're using and how to connect it. The three settings are explained below: 

1. Development - what we will use now
2. Test - for testing our code
3. Production - when we deploy our app

Since the dialects in the config.json file defaults to "mySql", we want to change it to "postgres"
Make sure to change the database name to correlate with your app name & name of its setting like so:
```
{
  "development": {
    "database": "userapp_development",
    "host": "127.0.0.1",
    "dialect": "postgres"
  },
  "test": {
    "database": "userapp_test",
    "host": "127.0.0.1",
    "dialect": "postgres"
  },
  "production": {
    "database": "userapp_production",
    "host": "127.0.0.1",
    "dialect": "postgres"
  }
}
```
### 3. Create a database inside Postgres
Here's how using sequelize CLI (you can also use "createdb userapp_development") 
```
sequelize db:create userapp_development
```

Double check to see if your Postgres is running otherwise you'll get this error: 
```
ERROR: connect ECONNREFUSED 127.0.0.1:5432
```
> Check to see if your database is created by: 
> 1. Accessing psql shell through your terminal:
> ```
> psql
> ```
> 2. Check your list of databases: 
> ```
> \l
> ```
> 3. Exit out once you were able to locate it! 

### 4. Create a model and matching migration
To create a model (like a table), here's what we should run in our terminal after we create our database:
```
sequelize model:create --name [SINGULAR name of model] --attributes [name of column]:[data type],[name of column2]:[data type]
```
Example:
```
sequelize model:create --name user --attributes firstName:string,lastName:string,age:integer,email:string
```
Tip: Make sure you do not have any spaces between each of the attributes and their data types. 

From the example, we'll get a new file in our "models" folder named "user.js" and the corresponding migration in the "migrations" folder named "(random number)-create-user.js"

Before running the matching migration, make sure your model is accurate!

ALSO, the "static associate(models) {" is for us to specific any relations/associations (one to one, one to many, many to many) between our models (hasMany or belongsTo). Foreign keys will go in the migration. /will update later!!

#### Running the migration:
> Here's how:
> 1. Accessing psql shell through your terminal:
> ```
> psql
> ```
> 2. Check your list of databases: 
> ```
> \l
> ```

### 5. Using the Models
This is in line with CRUD (Create, Read, Update, and Delete). 

We'll need to require it first before accessing them in our app: 

```
const db = require("./models")
```

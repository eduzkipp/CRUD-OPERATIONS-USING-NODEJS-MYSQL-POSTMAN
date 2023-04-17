# CRUD-OPERATIONS-USING-NODEJS-MYSQL-POSTMAN
#PREREQUISITES --MAKE SURE YOU HAVE THE FOLLOWING DOWNLOADED AND INSTALLED-- STEP 1 1)MYSQL 2)POSTMAN 3)NODE STEP 2 Create an empty folder and name it nodejsmysql. Open the newly created directory in VS Code inside the terminal, and type npm init to initialize the project. Press Enter to leave the default settings as they are.

--We are going to connect the Node.js web server with the MySQL database to store the employee details. The code that we’re writing now will allow us to create the employee database. We will be able to create, update, and delete employees in the database--

In the main directory file create a new file named index.js inside the directory install all the reqired modules using the following the command: npm install express mysql

--step 3-- CODE inside the index.js import a couple modules that will need in the application const express = require("express");

const mysql = require("mysql");

// Create connection

const db = mysql.createConnection({

host: "localhost",

user: "root",

password: "simplilearn",

database: "nodemysql",

});

// Connect to MySQL

db.connect((err) => {

if (err) {

throw err;
}

console.log("MySql Connected");

});

Since we are using the Express module to create the web server, we create a variable named app that behaves as an object of the express module. const app = express();

// Create DB

app.get("/createdb", (req, res) => {

let sql = "CREATE DATABASE nodemysql";

db.query(sql, (err) => {

if (err) {

  throw err;

}

res.send("Database created");
});

});

// Create table

app.get("/createemployee", (req, res) => {

let sql =

"CREATE TABLE employee(id int AUTO_INCREMENT, name VARCHAR(255), designation VARCHAR(255), PRIMARY KEY(id))";
db.query(sql, (err) => {

if (err) {

  throw err;

}

res.send("Employee table created");
});

}); // Insert employee 1

app.get("/employee1", (req, res) => {

let post = { name: "Jake Smith", designation: "Chief Executive Officer" };

let sql = "INSERT INTO employee SET ?";

let query = db.query(sql, post, (err) => {

if (err) {

  throw err;

}

res.send("Employee 1 added");
});

});

// Update employee

app.get("/updateemployee/:id", (req, res) => {

let newName = "Updated name";

let sql = UPDATE employee SET name = '${newName}' WHERE id = ${req.params.id};

let query = db.query(sql, (err) => {

if (err) {

  throw err;

}

res.send("Post updated...");
});

});

// Delete employee

app.get("/deleteemployee/:id", (req, res) => {

let sql = DELETE FROM employee WHERE id = ${req.params.id};

let query = db.query(sql, (err) => {

if (err) {

  throw err;

}

res.send("Employee deleted");
});

});

//server listening at port 3000 app.listen("3000", () => {

console.log("Server started on port 3000");

});

use the node index.js command to run the code open postman and in the fill in the appropriate request for each task you want to perform and press the button send

--the end-- Good luck coding

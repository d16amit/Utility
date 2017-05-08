## R Utility - Generate Cypher Script

</br>

### Introduction:

Cypher is a declarative query language for **Neo4j**, a property graph database. Neo4j has two basic components. 

 * Nodes, and 
 * Relationship
 
The *nodes* are the entities and the *relationship* defines how the two nodes are connected. For more details on Neo4j and graph database see [Neo4j - Graph Database](https://neo4j.com/developer/graph-database/).

*Generate Cypher Script* is an utility created with R Script. It reads the list of *nodes*, *relationships* and *input CSV file name* from a JSON configuration file and outputs the Cypher script. The generated cypher script can be used to create the nodes and relationship on Neo4j database.

</br>

### Objects:

This utility has following objects in folder and a short description about them.


| File Name | Type | Description |
| --- | --- | --- |
| markdown | Folder | R markdown file is placed in this folder |
| Output | Folder | The output cypher script is placed in this folder |
| config.json | JSON | Configuration file that takes list of nodes, relationships and input CSV file name |
| function_gencypher.R | R | R script that has the function to read config file, create the cypher script and place it in output folder |
| readme.html | HTML | Documentation |
| script_gencypher.R | R | R script to call generate cypher script  R function |
| run.bat | Batch | Windows batch script that executes the R script \"script_gencypher.R\" |


</br>

### Configuration template:


Add node details to config.JSON file in following format;

* {
    "FileName": "Movie.csv", *// Input CSV file Name*
    
    "Type": "Node", *// To indicate create node cypher script needs to be written (The value needs to be either "Node" or "Relationship")*
    
    "NodeName":"Movie", *// Name of the Node*
    
    "UniqueKeyColumn": "Title",  *// Unique column for this node in the input CSV file. This will be added a unique constraint in cypher script*
    
    "Column2": "YearReleased" *// Mention remaining column names from input CSV file if they need to be added as a property to the node*
    
     *// If input file has mode fields that needs to added as property, then include them subsequently i.e. as Column3, Column4, Column5, etc. *
     
     },

Add relationship details to config.JSON file in following format;


* {
    "FileName": "MovieActorMap.csv", *// Input CSV file Name*
    
    "Type": "Relationship", *// To indicate create relation cypher script needs to be written (The value needs to be either "Node" or "Relationship")*
    
    "Node1Name":"People", *// Name of the Node 1*
    
    "Node1Key": "Name",  *// Unique column for Node 1. The same column name needs to be present in both CSV file and in Node1*
    
    "Node2Name":"Movie", *// Name of the Node 2*
    
    "Node2Key": "Title",  *// Unique column for Node 2. The same column name needs to be present in both CSV file and in Node2*
    
    "RelationshipName": "ACTED_IN" *// Mention how Node1 is related to Node2. This will be the Relationship lable.*
    
    },


</br>

### How to run this utility:

Click on the "Run.bat" file to run this utility. 
This utility needs R Script dll's and libraries which are copied in the utility folder. Hence the client machine do not require to install R separately.


</br>

### Note:

This utility will serve as an example for following tasks,

* Write a simple JSON configuration file

* Write a R function

* How to import data from JSON file to R dataframe

* Subsetting data from R dataframe

* How to loop through the R dataframe

* How to capture output of a R function to a character vector

* How to write the output to a text file

* Write a simple R markdown

* How to call R script from windows command line using a batch file



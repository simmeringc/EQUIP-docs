{{#template name="preamble"}}

# EQUIP Project Docs
 *****

## Introduction
EQUIP is live at
<a href="http://www.equip.ninja">www.equip.ninja</a> and is an open-source project avaliable on
<a href="https://github.com/simmeringc/meteor-dataObs">Github</a>

<a href="mailto:equipappdevelopers@gmail.com">Contact us</a> for more information on EQUIP development.

### Version 1.3 Site Tour

[![Video](/EQUIPTourVideoSH.png)](http://www.youtube.com/watch?v=6RVLFzmDr1g "EQUIP App Version 1.3 Tour")

### Technology
* <a href="https://docs.meteor.com/">MeteorJS Version 1.3 (with JavaScript ES5/6 Conventions)</a> - Full-stack web framework
* <a href="https://guide.meteor.com/collections.html">MongoDB</a> - Database
* <a href="https://www.meteor.com/hosting">Galaxy</a> - Meteor App hosting

### Running EQUIP locally

Install Meteor:
```
curl https://install.meteor.com/ | sh
```
Run in the project directiory:
```
meteor
```

The Meteor CLI will install dependancies and serve the website locally on port 3000

### Deployment

Fork EQUIP on <a href="https://github.com/simmeringc/meteor-dataObs">Github</a> and<a href="mailto:equipappdevelopers@gmail.com"> contact</a> the EQUIP development team for pull-request and deployment instructions.

Obtain the <a href="https://www.dropbox.com/s/5z8i0j1aa9gdly2/EQUIP%20Deployment%20Guide.docx?dl=0"> EQUIP Deployment Guide</a> from the <a href="mailto:equipappdevelopers@gmail.com">development team</a> if you're deploying EQUIP to production.

The production version of EQUIP uses:

* <a href="https://www.meteor.com/hosting">Galaxy</a> for Meteor App and hosting
* <a href="https://mlab.com/">Mlabs</a> for MongoDB hosting
* <a href="https://www.namecheap.com/">Namecheap</a> for DNS
* <a href="https://mailgun.com">Mailgun</a> for mailing services

### Documentation

EQUIP is still in development and documentation of the full API is unfinished.

Project docs are generated with <a href="https://www.npmjs.com/package/meteor-jsdoc">meteor-jsdoc</a> and are hosted along side EQUIP with <a href="https://www.meteor.com/hosting">Galaxy</a>

Edit this documentation on <a href="https://github.com/simmeringc/meteor-dataObs-docs">Github</a>

### Other Project Resources

<a href="https://drive.google.com/drive/u/1/folders/0BzzX4Y7O9d_bUFFDdjVKaUs1dVU">Daniel's Academic Resources</a>

<a href="https://www.lucidchart.com/documents/view/4b244d07-944c-46f7-aa4e-3a0a51fa2793">Concept ERD</a>

<a href="https://www.lucidchart.com/documents/view/c6ec8b61-111e-4f6e-9231-ccdff17cc657">Site Mockup</a>

<a href="https://github.com/simmeringc/meteor-dataObs/tree/Version-1.2">EQUIP Version 1.2 (first production version)</a>

## Data Spec
MongoDB is a NoSQL database, thus all EQUIP data is stored in JSON.

JSON is a notation for a hierarchical data structure consisting of scalar values, arrays and objects, nested to any depth. Nesting cannot be represented in a typical ERD. As a result, EQUIP JSON collection schemas are shown below.

The current build (v1.3 08/17/16) has no joins or collection mappings.

### MongoDB Admin GUI

The EQUIP database can be viewed, queried, and modified with the MongoDB GUI: <a href="https://robomongo.org/">Robomongo</a>

* Download <a href="https://robomongo.org/">Robomongo</a>
* Run meteor in the EQUIP project directory
* Connect to your local MongoDB server at localhost:3001

If your mongo server isn't running on port 3001, connect to the mongo server in the Meteor Mongo Shell to see which port its running on.

### Meteor Mongo Shell

To view, query, and modify the database via the command line:

* Navigate to the EQUIP project directory
* Run 'meteor mongo' in the command line

The database can be queried in this meteor shell like any other Mongo database.

****

### Collections

#### Users

```
{  
   "_id":"string",
   "createdAt":{  
      "$date":"string"
   },
   "services":{  
      "password":{  
         "bcrypt":"string"
      },
      "resume":{  
         "loginTokens":[  
            {  
               "when":{  
                  "$date":"string"
               },
               "hashedToken":"string"
            }
         ]
      }
   },
   "emails":[  
      {  
         "address":"string",
         "verified":"bool"
      }
   ],
   "profile":{  

   }
}
```

#### Environments

```
{  
   "_id":"string",
   "envName":"string",
   "userId":"string",
   "author":"string",
   "submitted":{  
      "$date":"string"
   },
   "inputStyle":"string"
}
```

#### Observations

```
{  
   "_id":"string",
   "name":"string",
   "envId":"string",
   "userId":"string",
   "author":"string",
   "submitted":{  
      "$date":"string"
   }
}
```

#### Subject Parameters
* '...' in a JSON key value pair indicates the possibility for a user to add entries into the database.

```
{  
   "_id":"string",
   "userId":"string",
   "author":"string",
   "submitted":{  
      "$date":"string"
   },
   "children":{  
      "label0":"string",
      "label1":"string",
      "parameter1":"string",
      "label2":"string",
      "parameter2":"string",
      "label...":"string",
      "parameter...":"string",
      "envId":"string",
      "parameterPairs":"int"
   }
}
```

#### Sequence Parameters
* '...' in a JSON key value pair indicates the possibility for a user to add entries into the database.

```
{  
   "_id":"string",
   "userId":"string",
   "author":"string",
   "submitted":{  
      "$date":"string"
   },
   "children":{  
      "label0":"string",
      "parameter0":"string",
      "label1":"string",
      "parameter1":"string",
      "label...":"string",
      "parameter...":"string",
      "envId":"string",
      "parameterPairs":"int"
   }
}
```

#### Subjects
* '...' in a JSON key indicates the possibility for a user to add entries into the database.

* '(value)' indicates that a JSON key's value pair will be an integer represented as a string so the data can be parsed.

* '(valueLiteral)' indicates that a JSON key's value pair will be represented by the string value entered by the user in the parameters collections.

```
{  
   "_id":"string",
   "data_x":"string",
   "data_y":"string",
   "envId":"string",
   "NameLiteral":"string",
   "label0":"string(value)",
   "label0Literal":"string(valueLiteral)",
   "label1":"string(value)",
   "label1Literal":"string(valueLiteral)",
   "label...":"string(value)",
   "labelLiteral...":"string(valueLiteral)",
   "userId":"string",
   "author":"string",
   "submitted":{  
      "$date":"2016-08-string:39:50.534Z"
   }
}
```

#### Sequences
* '...' in a JSON key indicates the possibility for a user to add entries into the database.

* '(value)' indicates that a JSON key's value pair will be an integer represented as a string so the data can be parsed.

* '(valueLiteral)' indicates that a JSON key's value pair will be represented by the string value entered by the user in the parameters collections.

```
{  
   "_id":"string",
   "subjId":"string",
   "subjName":"string",
   "envId":"string",
   "obsId":"string",
   "obsName":"string",
   "valueInput":{  
      "parameter0":"string(value)",
      "parameter1":"string(value)",
      "parameter...":"string(value)"
   },
   "valueLiteral":{  
      "parameter0...":"string(valueLiteral)",
      "parameter1...":"string(valueLiteral)",
      "parameterLiteral...":"string(valueLiteral)"
   },
   "userId":"string",
   "author":"string",
   "submitted":"string"
}
```

### Live Data Examples

#### EQUIP Default Subject Parameters

```
{  
   "_id":"nga7ZfRudGEAGddoa",
   "userId":"WcG938v4R2wD4rtaR",
   "author":null,
   "submitted":{  
      "$date":"2016-08-18T17:45:39.383Z"
   },
   "children":{  
      "label0":"Name",
      "label1":"Age",
      "parameter1":"0 - 10,10 - 15,15 - 20,20 - 25,Unknown",
      "label2":"Race",
      "parameter2":"American Indian or Alaska Native,Asian,Black or African American,Native Hawaiian or Other Pacific Islander,White,Hispanic or Latino,Unknown",
      "label3":"Gender",
      "parameter3":"Male,Female,Other,Unknown",
      "envId":"RTWZNDsyYJ4dijrD7",
      "parameterPairs":4
   }
}
```

#### Mongo document entry of corresponding subject

```
{  
   "_id":"5andJBusPDADtGk6e",
   "data_x":"307.61782632964514",
   "data_y":"108.85312044729216",
   "envId":"RTWZNDsyYJ4dijrD7",
   "NameLiteral":"Conner",
   "Age":"3",
   "AgeLiteral":"20 - 25",
   "Race":"4",
   "RaceLiteral":"White",
   "Gender":"0",
   "GenderLiteral":"Male",
   "userId":"WcG938v4R2wD4rtaR",
   "author":null,
   "submitted":{  
      "$date":"2016-08-18T17:46:00.311Z"
   }
}
```

#### EQUIP Default Sequence Parameters

```
{  
   "_id":"HCv4rDT7454HTEzBu",
   "userId":"WcG938v4R2wD4rtaR",
   "author":null,
   "submitted":{  
      "$date":"2016-08-18T17:45:44.887Z"
   },
   "children":{  
      "label0":"WCD Type",
      "parameter0":"Math,Non-Math",
      "label1":"Solicitation Method",
      "parameter1":"Called On,Not Called On",
      "label2":"Wait Time",
      "parameter2":"Less than 3 seconds,3 or more seconds,N/A",
      "label3":"Length of Talk",
      "parameter3":"1-4 words,5-20 words,21 or more",
      "label4":"Student Talk",
      "parameter4":"How,What,Why,Other",
      "label5":"Teacher Soliciation",
      "parameter5":"How,What,Why,Other",
      "label6":"Explicit Evaluation",
      "parameter6":"Yes,No",
      "envId":"RTWZNDsyYJ4dijrD7",
      "parameterPairs":7
   }
}
```

#### Mongo document entry of corresponding sequence

```
{  
   "_id":"8jTFhpLTF7YRCms2w",
   "subjId":"EoizE5pybyTXPL5Dv",
   "subjName":"Justin",
   "envId":"RTWZNDsyYJ4dijrD7",
   "obsId":"fwANsMYqbMwAKtBPs",
   "obsName":"Test Observation",
   "valueInput":{  
      "WCDType":"1",
      "SolicitationMethod":"1",
      "WaitTime":"1",
      "LengthofTalk":"1",
      "StudentTalk":"1",
      "TeacherSoliciation":"1",
      "ExplicitEvaluation":"1"
   },
   "valueLiteral":{  
      "WCDTypeLiteral":"Non-Math",
      "SolicitationMethodLiteral":"Not Called On",
      "WaitTimeLiteral":"3 or more seconds",
      "LengthofTalkLiteral":"5-20 words",
      "StudentTalkLiteral":"What",
      "TeacherSoliciationLiteral":"What",
      "ExplicitEvaluationLiteral":"No"
   },
   "userId":"WcG938v4R2wD4rtaR",
   "author":null,
   "submitted":"Thu Aug 18 2016 11:46:51"
}
```

****

## Developing EQUIP

Completing the following tutorials will greatly aid in a developers understanding of EQUIP:

  * <a href="https://www.meteor.com/tutorials/blaze/creating-an-app">Creating your first app with MeteorJS</a>

  * <a href="https://www.discovermeteor.com/">Discover Meteor</a>

Find the MeteorJS documentation <a href="https://docs.meteor.com/">here</a>.

Note that later versions of meteor tutorials and documentation may not have the same conventions and best practices as EQUIP because the meteor framework is in constant development. EQUIP runs Meteor Version 1.3 with ES5/6 conventions.

### File Structure

The root of the project directory contains:

  * .git - For Git files
  * .meteor - For meteor build and package files, also contains the local database which is excluded in the .gitignore
  * client - Source files for HTML, Javascript, and CSS
  * lib - The lib directory is compiled first on startup, contains database initializations and routes
  * node_modules - Contains node_modules
  * public - Contains images, videos and other hostable files
  * server - Contains files that are only run on the server. Includes fixtures and publications
  * .gitignore - Contains Git excluded files
  * package.json - Contains information on NPM and node modules
  * README.md - Github readme file
  * settings.json - local only file (not on github) used for deployment to Galaxy

The client file contains the bulk of the front-end source files. Files are sorted into subdirectories based on where they appear on the website and relationships between the files. Package helpers and stylesheets also have their own directories.

All files in a MeteorJS application are concatenated together, however, the order in which they are combined and where they are run is dependent on the meteor file structure naming scheme.


### Style Guide

EQUIP uses Bootstrap3

EQUIP styles and code quality is in need of slight refactoring before style guide can be established.

It's standard in EQUIP to put the purpose of the file in a comment at the top of a file.

### Meteor Packages

MeteorJS uses native a package manager called Atmosphere, where packages like bootstrap and and font awesome can be easily integrated into a meteor application.

With meteor 1.3 (Current version used in EQUIP) NPM packages can also be integrated into meteor.

View the node_modules file or the /.meteor/packages file to view the packages used in EQUIP.

### Modifying Front-end code

Much of the front-end code in a meteor application is standard manipulation of JavaScript and HTML. Meteor makes use of file interpolation with templating and template helpers.

Every HTML file has an associated JavaScript file and they point to each other with templating as is visible in the EQUIP source code.

HTML templates are then served by the router or inserted into templates that are already being served with the help of tempale helpers and <a href="http://meteorcapture.com/spacebars/">Spacebars notation</a>

Visit the following resources to gain and understand of the front-end of a meteor application:

* <a href="https://docs.meteor.com/api/templates.html">Meteor Template Documentation</a>
* <a href="https://www.meteor.com/tutorials/blaze/creating-an-app">Creating your first app with MeteorJS</a> tutorial
* EQUIP source code

### Modifying Back-end code

EQUIP uses the iron-router package to facilitate routing: <a href="http://iron-meteor.github.io/iron-router/">Iron Router Guide</a>

EQUIP back-end files include the router, publications, collections.

  * <a href="https://docs.meteor.com/api/pubsub.html">Meteor Publish and Subscribe Guide</a>
  * <a href="https://guide.meteor.com/collections.html">Meteor Collections Guide</a>

Meteor uses a publish and subscribe paradigm to control access to the database and data control flow.

Meteor's out of the box database service is MongoDB, so collections and collection manipulation is integrated with standard MongoDB methods

* <a href="https://docs.mongodb.com/manual/reference/method/js-collection/">MongoDB Collection Documentation</a>

****

## Todos

###High Priority

* Data visualization for custom subject and sequence parameter inputs

* Mailgun:
  * User signup email confirmation and password reset
  * 'Contact Us' email working

* Bug free subject arrangement grid. Possible refactoring

* Deploying: Add SSL encryption with Galaxy and update all links
  * https and SSL keys - google analytics
  * MIT licensing and copyright
  * Get the Mlabs host out of sandbox mode for production
  * deployment best practices <a href="https://guide.meteor.com/deployment.html">(Galaxy Docs)</a>

* Figure out why CSS is enlarged in production vs localhost

* One page explanation (Modal for more info on landing page)

* Modal freezing when it isn't properly closed and the user navigates with it open

###Medium Priority

* Proper input box validation on all pages:
  * Lengths of input, invalid characters, duplicate parameters

* Preset subject grid arrangements and snapping

* Preset sequence actions: a user can create take a common sequence input and assign it to a hot key on the screen so all sequence buttons don't have to be pressed. Possible auto highlighting in box-modal

* User adjustable timer inside observatory and appending times onto sequences when a sequence is taken

* Ability to import/export subject/parameters/sequences via CSV

* Mobile device viewport and responsiveness testing

* More robust documentation, full API, search functionality, meteor js-doc

* Sign-out boots user to homepage

###Low Priority

* More extensible / editable documentation and todo lists

* Bootstrap confirmation popups on view-table deletes

* Landing page video demonstrating the app

* Ability to sort view-tables

* Editing subjects and sequences from view-tables

* Horizontal scroll on view-tables when there's too many parameters

* Better toasts on user action completion

* Facebook / Google API for user signup

* Linting and code style revisions, duplicate removal and global functions

* Google analytics in every file best practices

* Dynamic titles

* Navigating box-input with keyboard

* Reformat DBScheme and code to minimize duplicate data and calls to the database

* Dynamic sequencing log in observatory. Most recent sequence is shown after a user takes it

* Robust user creation pages instead of dropdown <a href="https://github.com/Differential/accounts-entry">(Example)</a>

###Looking Forward

* Considering upgrading to meteor 1.4 which uses a different router, best practices, and interpolation engine. Probably not worth it.

* Modal animations and CSS animations

* Check user experience tracking and analytics <a href="https://fullstory.com/">(Full Story)</a>

{{/template}}

Continuum CLI Templates
=======================


## spawn.json
* Template directories may contain a file named **spawn.json**
* This file contains settings for rendering a directory template
* The format is as follows
  - **inherits** path to a spawn template folder that this spawn inherits
    - inherited spawns will process all rules and files of the parents as well as this spawn
  - **globals** contains all values that will be provided by default if not overridden by the user
  - **propertySchema** is the JSON schemas for all available properties that must be provided by the user
    - If you provide a default this will be presented as the default to the user
    - The default can use a liquid.js expression that will be populated with values in the context
    - A description can be used to prompt the user for the value if not supplied

Example:
```json
{
  "inherits": "../applicationCommon",
  "globals": {
    "groovyVersion": "3.0.6",
    "springBootVersion": "2.6.3",
    "springDependencyManagementVersion": "1.0.11.RELEASE",
    "continuumVersion": "1.0-SNAPSHOT"
  },
  "propertySchema":{
    "applicationName": {
      "type": "string",
      "description": "Application Name"
    },
    "groupId": {
      "type": "string",
      "description": "Maven Group Id"
    },
    "artifactId": {
      "type": "string",
      "description": "Maven Artifact Id"
    },
    "basePackage": {
      "type": "string",
      "description": "Base java package for application",
      "default": "{{groupId}}.{{artifactId}}"
    },
    "javaVersion": {
      "type": "string",
      "enum": ["8", "11", "17"],
      "default": "17",
      "description": "Java source compatibility version"
    }
  }
}
```

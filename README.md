# KEX-Vorgang-Import-API

This schema is the basic model for the [kex-vorgang-import-api](https://github.com/europace/kex-vorgang-import-api).

## Usage

The following example shows the generation of Java-classes using our schema and gradle. 
For that the folder `jsonSchema` (containing our schema files) needs to be located in the root directory of the project. The generated POJOs are located in `/src/main/java`.

```
buildscript {

  ext {
    pojoDir = "${projectDir}/src/main/java"
  }

  dependencies {
    classpath "org.jsonschema2pojo:jsonschema2pojo-gradle-plugin:0.4.30"
  }
}

jar.dependsOn generateJsonSchema2Pojo

jsonSchema2Pojo {
  annotationStyle = "none"
  includeAccessors = false
  includeAdditionalProperties = false
  includeToString = false
  initializeCollections = false
  removeOldOutput = true
  source = files("${projectDir}/jsonSchema")
  targetDirectory = file("${pojoDir}")
  useCommonsLang3 = true
  useJodaLocalDates = true
}
```

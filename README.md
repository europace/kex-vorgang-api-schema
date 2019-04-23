# KEX-Vorgang-Import-API

siehe https://github.com/europace/kex-vorgaenge-api

Diese Schema-Dateien sind generiert und dürfen nicht händisch verändert werden, da diese Änderungen wieder verloren gehen.

## Verwendung

Das folgende Beispiel zeigt die Nutzung von Gradle zur Generierung von Java-Klassen aus dem Schema. Dafür liegt der Ordner `jsonSchema`, der die Schema-Dateien enthält, im Wurzelverzeichnis des Projekts. Die POJOs werden in `/src/main/java` generiert.

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

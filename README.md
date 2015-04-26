### Maven archetype to scaffold a new Spark Scala project

### To generate a new project
Since **IntelliJ IDEA** doesn't distinguish between _archetype catalog_ and _archetype repository_ when you try to add remote archetype, you should first use interactive or batch mode (see below) in terminal to generate a new project then import it in Idea as existing maven project.  

 * In **Eclipse** (requires [ScalaIDE](http://scala-ide.org/download/current.html) and [m2e-scala](https://github.com/sonatype/m2eclipse-scala))  
1. `File > New > Project... > Maven > Maven Project`  
2. Click `Next` on the first screen of the _New project_ wizard  
3. Select `Configure... > Add Remote Catalog...`  
4. Enter the following URL in the `Catalog file` field: https://github.com/mbonaci/spark-archetype-scala/raw/master/archetype-catalog.xml  
      Enter `Spark Scala Archetype` in the `Description` field  
5. After you close the dialog, choose the `Spark Scala Archetype` catalog in the `Catalog` dropdown list
6. In the next dialog enter you project details and confirm with `Finish`
7. Once the new projects generates change the Scala version to 2.10.5 by right-clicking on the generated project's root and selecting:
      `Scala > Set the Scala Installation > Fixed Scala Installation 2.10.5.(bundled)`



 * **From the terminal** (interactive mode):  
 <small>
 Select the only possible option (1) and answer subsequent questions.
 </small>

```sh
mvn archetype:generate \
  -DarchetypeCatalog=https://github.com/mbonaci/spark-archetype-scala/raw/master/archetype-catalog.xml \
  -DarchetypeRepository=https://github.com/mbonaci/spark-archetype-scala/raw/master
```


 * **From the terminal or a shell script** (batch mode):  
 <small>
 Don't forget to change the parameter values in the last line.
 </small>

```sh
mvn archetype:generate -B \
    -DarchetypeCatalog=https://github.com/mbonaci/spark-archetype-scala/raw/master/archetype-catalog.xml \
    -DarchetypeRepository=https://github.com/mbonaci/spark-archetype-scala/raw/master \
    -DarchetypeGroupId=org.sia \
    -DarchetypeArtifactId=spark-archetype-scala \
    -DarchetypeVersion=0.9 \
    -DgroupId=com.company -DartifactId=project -Dversion=0.1-SNAPSHOT -Dpackage=com.company
```
For your convenience, here's the copy/paste friendly version (customize your new project by changing the last 4 params):

```
mvn archetype:generate -B -DarchetypeCatalog=https://github.com/mbonaci/spark-archetype-scala/raw/master/archetype-catalog.xml -DarchetypeRepository=https://github.com/mbonaci/spark-archetype-scala/raw/master -DarchetypeGroupId=org.sia -DarchetypeArtifactId=spark-archetype-scala -DarchetypeVersion=0.9 -DgroupId=org.sijaset -DartifactId=sija -Dversion=0.1 -Dpackage=org.sijaset
```

 * ***Generated project example usage*** *(run* `mvn scala:help` *for the full list of commands):*

You can run the generated project by simply doing `Shift+Alt+x s` (while positioned in `App.scala`), which is the shortcut for `Run As > Scala Application`.

You can also run it from the command line or from Eclipse Maven _Run configuration_ with these _goals_:

```sh
mvn scala:compile
mvn scala:run -DmainClass=com.company.App
```

Have fun :)

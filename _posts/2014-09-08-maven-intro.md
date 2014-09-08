---
layout: post
---

# A quick introduction to Maven

## What is Maven?
Not very long ago, when you had to compile your single-file project you only had to:

		gcc hello.c -o hello
		./hello

That was easy, but when you had to compile a big project that included lots of libraries and lots of source files under different directories, it could become quite a headache.  
So the all-shiny Make came into existence, to keep track of all those source files, under their respective directory and give you an easy way to recompile outdated source files and generate your program. It used a text file, commonly named *makefile*, to specify all your project's stuff. Example makefile:

		all: hello  

		hello: main.o factorial.o hello.o
			g++ main.o factorial.o hello.o -o hello

		main.o: main.cpp
			g++ -c main.cpp

		factorial.o: factorial.cpp
			g++ -c factorial.cpp

		hello.o: hello.cpp
			g++ -c hello.cpp

		clean:
			rm -rf *o hello

you just had to run:

		make
		./hello

and voilà, Make compiled all your sources and created your executable file. You could also run single tasks specifying them after the make command:

		make hello
		make clean

and Make would search for your desired task and execure all its steps. For example, with the previous makefile, if you run `make clean` Make would run `rm -rf *o hello`.

But it still had some problems. If you had a java project, Make would run a `javac` command for each .java file, which would make it quite slow for big projects. It would do:

		javac Class1.java
		javac Class2.java
		javac Class3.java
		...

instead of the more resource-efficient:

		javac Class1.java Class2.java Class3.java

So Maven came into existence, which would solve problems like this and add some other nice features, like dependency management and project management. We'll get into that later.

## Setting up Maven on win 7

* Download maven [from here](http://maven.apache.org/download.cgi)
* Extract under `C:\Program Files\Apache Software Foundation`
* Add the `M2_HOME` environment variable with the value `C:\Program Files\Apache Software Foundation\apache-maven-3.1.1` (change the version number of apache-maven-x.x.x to your own).
* Add the `M2` environment variable with the value `%M2_HOME%\bin`.
* Open a new command prompt and run `mvn --version` to verify your installation:

		C:\Users\user>mvn --version
		Apache Maven 3.1.1 (0728685237757ffbf44136acec0402957f723d9a; 2013-09-17 10:22:22-0500)
		Maven home: C:\Program Files\Apache Software Foundation\apache-maven-3.1.1
		Java version: 1.6.0_35, vendor: Sun Microsystems Inc.
		Java home: C:\Program Files\Java\jdk1.6.0_35\jre
		Default locale: es_CO, platform encoding: Cp1252
		OS name: "windows 7", version: "6.1", arch: "amd64", family: "windows"

## Project Management
You can create your project structure using maven:

		mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false

This will create the following structure for your project:

		my-app
		|-- pom.xml
		`-- src
		    |-- main
		    |   `-- java
		    |       `-- com
		    |           `-- mycompany
		    |               `-- app
		    |                   `-- App.java
		    `-- test
		        `-- java
		            `-- com
		                `-- mycompany
		                    `-- app
		                        `-- AppTest.java

and you can run it with:

		cd myapp
		mvn compile
		java -cp target\classes com.mycompany.app.App

## Dependency Management
Maven uses the file *pom.xml* to keep your project configuration and other stuff. It also helps you manage dependencies. No more downloading xxxxx.jar files from many different sites and manually puting them in your project.
you can specify a required library in your *pom.xlm*, by telling maven the groupId, artifactId and version:

{% highlight xml %}
		<dependencies>
			<dependency>
				<groupId>junit</groupId>
				<artifactId>junit</artifactId>
				<version>3.8.1</version>
				<scope>test</scope>
			</dependency>
			<dependency>
				<groupId>org.hibernate</groupId>
				<artifactId>hibernate-entitymanager</artifactId>
				<version>4.2.7.Final</version>
			</dependency>
		</dependencies>
{% endhighlight %}

This tells maven to download the required jar files for Junit version 3.8.1 and Hibernate Annotations version 4.2.7.Final and include them in my projects.

## Eclipse integration
1. Go to *File* --> *Import* and select *Existing Maven Projects*:  
	**Note:** You do not need to run the command `mvn eclipse:eclipse`  
	![Eclipse Import](/images/2014-09-08-01.png)
2. Select the root directory of your Maven project:  
	![Root Directory]({{site.url}}/images/2014-09-08-02.png)
3. Hit *Finish*.

## Maven archetype:generate
An excelent explanation about the command mvn archetype:generate, found on <http://stackoverflow.com/a/8205447/965342>:

`mvn archetype:generate` command is used to create a project from an existing template. There are several archetype's defined by many developers and project groups. When you run the command, maven does following things:
1. Downloads maven-archetype-plugin's latest version.
2. Lists all archetype's that can be used to create a project from. If you defined an archetype while calling the command, maven jumps to step 6.
3. By default, maven chooses **maven-archetype-quickstart** archetype which basically creates a maven Hello World project with source and test classes. If you want to create a simple project, you can just press enter to continue. If you want to create a specific type of application, you should find the archetype matching your needs and enter the number of that archetype, then press enter. E.g. If you want to create a webapp project, you can enter 155 (this is the current number for this archetype, it can change in time.)
4. Since archetypes are templates and they intend to reflect current best practices, they can evolve in time, thus they have their own versions. Maven will ask you which version of the archetype you want to use. By default, maven chooses latest version for you. so if you agree to use the latest version of an archetype, just press Enter at this step;
5. Every maven project (and module) has its groupId, artifactId and version. Maven will then ask these to you in three steps.
6. Finally, maven will ask you the package structure for your code. A best practice is to create your folder structure that reflects the groupId, thus Maven sets this as default but you are free to change this.
7. After entering this information, Maven will show you all the information you entered and ask you to verify project creation. If you press Y and then enter, voilà your project is created with the artifact and settings you chose.

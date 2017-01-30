# SonarQube
Sonar is a web based code quality analysis tool for Maven based Java projects. It covers a wide area of code quality check points which include: Architecture & Design, Complexity, Duplications, Coding Rules, Potential Bugs, Unit Test etc.


# A pre-requisite to run Sonar is to have Java and Maven installed on the box. Once this is the case, you can run Sonar in 5 simple steps:

1. Download the distribution from http://sonar.codehaus.org/downloads/ and unzip it

2. Open a console and start the server:

> $SONAR_HOME\bin\windows-x86-32\StartSonar.bat on windows

> $SONAR_HOME/bin/[OS]/sonar.sh on other platforms

3. Open a console where you want to checkout the source and run:

svn co http://svn.apache.org/viewvc/commons/proper/collections/trunk/.

4. Run in the same directory
# $>      mvn install sonar:sonar 


5. Browse http://localhost:9000

# ---------------------------Eclipse Plugin--------------------------
1) Go to market place under help menu of the eclipse
2) type sonar
3) install
4) restart eclispe


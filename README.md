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
1) Go to eclipse market place under help menu of the eclipse

2) type sonar

3) install

4) restart eclispe

	<!--  Added Jacoco report -->
	<build>
		<plugins>
			<plugin>
				<artifactId>maven-dependency-plugin</artifactId>
				<executions>
					<execution>
						<id>copy-dependencies</id>
						<phase>package</phase>
						<goals>
							<goal>copy-dependencies</goal>
						</goals>
						<configuration>
							<outputDirectory>${project.build.directory}/lib</outputDirectory>
							<overWriteReleases>true</overWriteReleases>
							<overWriteSnapshots>true</overWriteSnapshots>
							<overWriteIfNewer>true</overWriteIfNewer>
							<excludeScope>test</excludeScope>
							<includeScope>compile</includeScope>
							<stripVersion>true</stripVersion>
						</configuration>
					</execution>
				</executions>
			</plugin>

			<!-- Sonar Coverage Testing with Jacoco -->

			<plugin>
				<groupId>org.jacoco</groupId>
				<artifactId>jacoco-maven-plugin</artifactId>
				<version>0.7.5.201505241946</version>

				<configuration>
					<destFile>${sonar.jacoco.reportPath}</destFile>
					<append>true</append>
					<excludes>
						<exclude>**/pipeline-examples/**</exclude>
					</excludes>
				</configuration>

				<executions>
					<execution>
						<id>pre-unit-test</id>
						<goals>
							<goal>prepare-agent</goal>
						</goals>
					</execution>
					<execution>
						<id>post-unit-test</id>
						<phase>test</phase>
						<goals>
							<goal>report</goal>
						</goals>
					</execution>
				</executions>
			</plugin>

			<!--end Sonar Coverage Testing with Jacoco -->

		</plugins>
		<pluginManagement>
			<plugins>
				<!-- detect JDK Version discrepencies -->
				<plugin>
					<groupId>org.codehaus.mojo</groupId>
					<artifactId>animal-sniffer-maven-plugin</artifactId>
					<version>1.14</version>
				</plugin>

				<!-- use mvn cobertura:cobertura to generate cobertura reports with maven 
					plugin version 2.6 -->
				<plugin>
					<groupId>org.codehaus.mojo</groupId>
					<artifactId>cobertura-maven-plugin</artifactId>
					<version>2.6</version>
				</plugin>

				<!--This plugin's configuration is used to store Eclipse m2e settings 
					only. It has no influence on the Maven build itself. -->
				<plugin>
					<groupId>org.eclipse.m2e</groupId>
					<artifactId>lifecycle-mapping</artifactId>
					<version>1.0.0</version>
					<configuration>
						<lifecycleMappingMetadata>
							<pluginExecutions>
								<pluginExecution>
									<pluginExecutionFilter>
										<groupId>org.jacoco</groupId>
										<artifactId>
											jacoco-maven-plugin
										</artifactId>
										<versionRange>
											[0.6.4.201312101107,)
										</versionRange>
										<goals>
											<goal>prepare-agent</goal>
										</goals>
									</pluginExecutionFilter>
									<action>
										<ignore></ignore>
									</action>
								</pluginExecution>
							</pluginExecutions>
						</lifecycleMappingMetadata>
					</configuration>
				</plugin>
			</plugins>
		</pluginManagement>
	</build>

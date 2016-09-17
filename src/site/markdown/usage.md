# Usage

This pom is the base line configuration of all [devacfr project][devacfr]. There is divide in following section:

* **Dependencies Management**,
* **Release Management**, describes necessary actions to release with **maven** in serenity. 
* **Quality and Validation**,
* **Distribution Management**,

This is a parent POM of all [devacfr][devacfr] projects. To use this predefined maven over configuration, add it as parent :

```xml
<parent>
    <groupId>org.cfr</groupId>
    <artifactId>maven-config</artifactId>
    <version>7</version>
</parent>
```

Declare the repository for your project or for a parent project by updating the pom.xml file and adding the following code to the `<repositories>` section:

```xml
<repository>
    <snapshots>
        <enabled>false</enabled>
    </snapshots>
    <id>jcenter</id>
    <name>JCenter Repository</name>
    <url>http://jcenter.bintray.com</url>
</repository>
```
As an alternative, you can also declare the repository for all of your projects. Go to the directory on the local computer where you just install Maven. Open and edit `conf/settings.xml` file. Add to the &lt;profiles&gt; section the following code:

```xml
<profiles>
    <profile>
        <id>jcenter</id>
        <repositories>
            <repository>
                <snapshots>
                    <enabled>false</enabled>
                </snapshots>
                <id>jcenter</id>
                <name>JCenter Repository</name>
                <url>http://jcenter.bintray.com</url>
            </repository>
        </repositories>
    </profile>
</profiles>
<activeProfiles>
    <activeProfile>jcenter</activeProfile>
</activeProfiles>
```

## Properties

`maven-config` create default properties or override default values that you can also override. this is the list of used properties:

| **Global Properties**       | **Description**                        |
|------------------------|------------------------------------------|
| maven.version | The minimal maven required version (`3.2.5` by default) |

| **Reporting Properties** | **Description**  |
|------------------------|------------------------------------------|
| aggregate       | Indicates whether the report must be aggregate module reports (`false` by default). |
| project.reporting.outputEncoding | Sets default reporting encoding to UTF-8 by default. |
| alwaysGenerateSurefireReport | Indicates whether **Surfire** report must be generate when there is no tests (`false` by default). |
| quiet | Shuts off javadoc non-error and non-warning messages (`true` by default). |
| detectOfflineLinks | Indicates whether links detection between modules during javadoc generation (`false` by default). |
| dependency.locations.enabled | Indicates whether display the repository locations of the dependencies in project info reports (`false` by default).  |


| **Compiler Properties**   | **Description**  |
|------------------------|------------------------------------------|
| project.build.sourceEncoding | Sets default source encoding to `UTF-8` by default. |
| maven.compiler.target | Sets compiler source and target versions (`1.8` by default). |
| maven.compiler.showDeprecation | Sets compiler to show depreciation (`true` by default). |
| maven.compiler.showWarnings | Sets compiler to show warning (`true` by default). |





## Release Management

This section explains how release `maven-config` exclusively. `maven-config` implements `git-flow` but doesn't use it. for a complete description of release management configured in `maven-config`, see [Contribute Documentation][contribute].

This phase is is awfully easy since maven exists.

### Prepare a Release

Preparing a release goes through the following release phases:

* Check that there are no uncommitted changes in the sources
* Check that there are no *SNAPSHOT* dependencies
* Change the version in the POMs from x-SNAPSHOT to a new version (you will be prompted for the versions to use)
* Transform the SCM information in the POM to include the final destination of the tag
* Run the project tests against the modified POMs to confirm everything is in working order
* Commit the modified POMs
* Tag the code in the SCM with a version name (this will be prompted for)
* Bump the version in the POMs to a new value y-SNAPSHOT (these values will also be prompted for)
* Commit the modified POMs

### Online Release

This Maven pom releases the project online with Git by default. Each generated tag are prefix with '`v${project.version}`'.

```bash
devacfr$ mvn release:clean release:prepare --batch-mode -DreleaseVersion=${release.version} -DdevelopmentVersion=${dev.version} 
devacfr$ 
devacfr$ mvn release:perform
```

Using batch mode `--batch-mode` with no other configuration will cause the Release Plugin to use default values for the release version, the SCM tag, and the next development version.

The maven phase `release` appends the profile `release` and `reporting` during the execution changing the compilation configuration as *no debug* and *optimize*. The generated artifacts  are deployed on the distribution server and the site with quality code reports is published on github.
	
Whether the release failed, you are need rollback a release following action in order. You haven't run `release:clean` on the project before rollback. This means that the backup files and the release descriptor from the previous release command still exists.

```bash
devacfr$ mvn release:rollback
```

When a release is rolled back, the following release phases are executed:

* all project POMs are reverted back to their pre-release state locally, and also in the SCM if the previous release command was able to successfully make changes in the SCM to the POMs. This is done by using the backup files created during`release:prepare`.
* The created branch/tag in SCM for the release is removed. **Note**: This is not yet implemented so you will need to manually remove the branch/tag from your SCM. 

### Offline Release

To reduce release problem with your SCM in beginning, you can activate the profile `release-offline`, because during the release preparation phase, a tag is created in the SCM and the modified POMs are committed. the profile `release-offline` uses a local checkout instead of doing a checkout from the upstream repository, doesn't push changes to the upstream repository and tags locally the new release.

```bash
devacfr$ mvn release:clean release:prepare -Prelease-offline
```

Once your configuration is stable, you will be able to release directly in your favorite SCM.

```bash
devacfr$ mvn release:perform -Prelease-offline
```


## Reporting Configuration

The site generation use by default [Reflow Maven Skin][reflow-home]. It is responsive Apache Maven skin to reflow the standard Maven site with a modern feel. [Full Usage &raquo;][reflow-usage]

### Aggregate Reporting (Multi-module)

In Maven, the generation of reports are individual for each module. The aggregation on root site is possible. For this, set the `aggregate` property to *true*.

```xml
<properties>
     ...
        <!-- Enable report aggregation -->
        <aggregate>true</aggregate>
     ...
</properties>
```


## Quality and Validation

the profile `reporting`  generates *Project Information* and *Project Reports*  sections.
The following command create site without deployment:

```bash
devacfr$ mvm clean site -Preporting
```

or for project with multi-module,

```bash
devacfr$ mvm clean site site:stage -Preporting
```
Mainly, The code quality reports are:

* **Checkstyle Reports**, performs check style analysis.
* **PMD and CDB Reports**, first is code analysis tool and second is Copy/Paste Detector tool.
* **Findbugs**,.


## Distribution Deployment

Only releases artificats are published in distribution 

Site is deployed on **GitHub Pages** 

```bash
devacfr$ mvn site-deploy -Preporting
```

	

[devacfr]: http://devacfr.github.io/
[contribute]: doc/contribute.html
[reflow-home]: http://andriusvelykis.github.io/reflow-maven-skin/
[reflow-usage]: http://andriusvelykis.github.io/reflow-maven-skin/skin/
[jcenter]:http://jcenter.bintray.com


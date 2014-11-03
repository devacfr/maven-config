# Configuration

This is a parent POM of all [devacfr][devacfr] projects. To use this predefined maven over configuration, add it as parent :

```xml
<parent>
    <groupId>org.cfr</groupId>
    <artifactId>maven-config</artifactId>
    <version>6</version>
</parent>
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

---


# Usage
 
This pom is the base line configuration of all [devacfr project][devacfr]. There is divide in following section:

* **Dependencies Management**,
* **Release Management**, describes necessary actions to release with **maven** in serenity. 
* **Quality and Validation**,
* **Distribution Management**,
 
## Dependencies Management


## Release Management

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
devacfr$ mvm release:perform
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

To reduce release problem with your SCM in beginning, you can activate the profile `release-offline`, because during the release preparation phase, a tag is created in the SCM and the modified POMs are committed.

```bash
devacfr$ mvn release:clean release:prepare -Prelease-offline
```

Once your configuration is stable, you will be able to release directly in your favorite SCM.

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
[reflow-home]: http://andriusvelykis.github.io/reflow-maven-skin/
[reflow-usage]: http://andriusvelykis.github.io/reflow-maven-skin/skin/


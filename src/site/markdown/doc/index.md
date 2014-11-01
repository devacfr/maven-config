## Usage
 
This pom is the base line configuration of all [devacfr project][devacfr-project]. There is divide in following section:

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

	devacfr$ mvn release:clean release:prepare --batch-mode -DreleaseVersion=${release.version} -DdevelopmentVersion=${dev.version} 
	devacfr$ 
	devacfr$ mvm release:perform 

Using batch mode `--batch-mode` with no other configuration will cause the Release Plugin to use default values for the release version, the SCM tag, and the next development version.

The maven phase `release` appends the profile `release` during the execution changing the compilation configuration as *no debug* and *optimize*.
	
Whether the release failed, you are need rollback a release following action in order. You haven't run `release:clean` on the project before rollback. This means that the backup files and the release descriptor from the previous release command still exists.
	
	devacfr$ mvn release:rollback 

When a release is rolled back, the following release phases are executed:

* all project POMs are reverted back to their pre-release state locally, and also in the SCM if the previous release command was able to successfully make changes in the SCM to the POMs. This is done by using the backup files created during`release:prepare`.
* The created branch/tag in SCM for the release is removed. **Note**: This is not yet implemented so you will need to manually remove the branch/tag from your SCM. 

### Offline Release

To reduce release problem with your SCM in beginning, you can activate the profile `release-offline`, because during the release preparation phase, a tag is created in the SCM and the modified POMs are committed.

	devacfr$ mvn release:clean release:prepare -Prelease-offline

Once your configuration is stable, you will be able to release directly in your favorite SCM.

## Quality and Validation

the profile `reporting`  generates *Project Information* and *Project Reports*  sections.
Creation of site without deployment use the command

	devacfr$ mvm clean site -Preporting
	
## Distribution Deployment



Site is deployed on **GitHub Pages** 

	devacfr$ mvn site-deploy -Preporting	
	

[devacfr-project]: http://devacfr.github.io/
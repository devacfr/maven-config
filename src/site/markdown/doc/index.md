## Usage
 
This pom is the base line configuration of all [devacfr project][devacfr-project]. There is divide in following section:

* **Dependencies Management**,
* **Release Management**,
* **Quality and Validation**,
* **Distribution Management**,
 
## Release Management

This Maven pom releases the project offline by default. All commits and tag are executed locally

	// ??
	> mvn release:prepare
	> 
	> mvm release:perform 
	
The maven phase `release` appends the profile `release` during the execution changing the compilation configuration as *no debug* and *optimize*.

## Quality and Validation

the profile `reporting`  generates *Project Information* and *Project Reports*  sections.
Creation of site without deployment use the command

	mvm clean site -Preporting
	
## Distribution Deployment



Site is deployed on **GitHub Pages** 

	mvn site-deploy -Preporting	
	

[devacfr-project]: http://devacfr.github.io/
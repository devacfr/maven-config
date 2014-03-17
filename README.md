maven-config Project
============

The project maven-config is the parent maven pom for all projects. It defines the default configuration.

This pom file structure is based on project [m4entreprise](https://code.google.com/p/m4enterprise/) and contains the standard configuration for all project in  [devacfr](https://github.com/devacfr).

## Introduction

The project m4entreprise gives some very interesting information and i don't see what I can append anymore. I'm just do:

* Add global `dependency management`, constrains coherence in dependency hierarchy ,to exclude automatically  wrong dependency, define default dependency scope,...
* Create `Reporting` profile to reduce the time of the deployment processing.
* The deployment of site is disabled by default

###Note
I tried the site deployment on confluence, but the rendering and customization is poor for the moment (but i don't despair). 


## Distribution

* Stable version [Release 3](https://bintray.com/devacfr/maven/maven-config/3/view/files/org/cfr/maven-config/3)


## Contribution Policy

Contributions via GitHub pull requests are gladly accepted from their original author.
Along with any pull requests, please state that the contribution is your original work and 
that you license the work to the project under the project's open source license.
Whether or not you state this explicitly, by submitting any copyrighted material via pull request, 
email, or other means you agree to license the material under the project's open source license and 
warrant that you have the legal authority to do so.

## Licence

	This software is licensed under the Apache 2 license, quoted below.
	
	Copyright 2014 Christophe Friederich
	
	Licensed under the Apache License, Version 2.0 (the "License"); you may not
	use this file except in compliance with the License. You may obtain a copy of
	the License at http://www.apache.org/licenses/LICENSE-2.0
	
	Unless required by applicable law or agreed to in writing, software
	distributed under the License is distributed on an "AS IS" BASIS, WITHOUT
	WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the
	License for the specific language governing permissions and limitations under
	the License.
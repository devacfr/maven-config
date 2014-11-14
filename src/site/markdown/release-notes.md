# Release notes

The history of Maven config releases is documented below. For details of changes refer to the [project's GitHub issues][maven-config-issues] or the [GitHub report][github-report].

[maven-config-issues]: http://github.com/devacfr/maven-config/issues?state=closed
[github-report]: github-report.html

## Release 7

### Enhancement
- Bundle up Legal resources as a remote-resource. ([&#35;9][issue-9])
- Guava upgrade to 18.0


### Maintenance 
- Remove Repositories reference from maven-config Pom's ([&#35;10][issue-10])
- Remove unnecessary PMD rules
- Remove Atlassian dependencies
- Enforce using m2e-code-quality extension in Eclipse



[issue-9]: https://github.com/devacfr/maven-config/issues/9
[issue-10]: https://github.com/devacfr/maven-config/issues/10

## Release 6

###Enhancement
- Add site deploy during release phase

### Bug fix
- Fix deployment multi-module site on github ([&#35;8][issue-8])
	- Replace github:site-maven-plugin by wagon-git
- Remove deploy skip for maven-checker module ([&#35;7][issue-7])

[issue-7]: https://github.com/devacfr/maven-config/issues/7
[issue-8]: https://github.com/devacfr/maven-config/issues/8

## Release 5

### Enhancement
- Site deployment in github ([&#35;3][issue-3])

### Maintenance
- Documentation & Review ([&#35;4][issue-4])
	- Adapt check style and pmd with specific rules
	- Add Release Section in Usage documentation
	- Clean and remove unnecessary code and information
	- Make links in the site descriptor absolute to the project URL relativizeDecorationLinks=false in maven site plugin
	- Correct bug location of java header license in checkstyle.xml file
	- Add Mockito and PowerMock dependency.
	- Add Cobertura coverage reporting (Conflict cglib dependency between easymock and cobertura ([&#35;5][issue-5])

See [all GitHub issues for 5][maven-config-5] for further details.

[issue-3]: https://github.com/devacfr/maven-config/issues/3
[issue-4]: https://github.com/devacfr/maven-config/issues/4
[issue-5]: https://github.com/devacfr/maven-config/issues/5

[maven-config-5]: https://github.com/devacfr/maven-config/issues?q=milestone%3A5+is%3Aclosed


## Release 3

### Enhancement
- Create profile to deploy distribution in github ([&#35;1][issue-1])
- Create bintray profile ([&#35;2][issue-2])

See [all GitHub issues for 3][maven-config-3] for further details.

[issue-1]: https://github.com/devacfr/maven-config/issues/1
[issue-2]: https://github.com/devacfr/maven-config/issues/2

[maven-config-3]: https://github.com/devacfr/maven-config/issues?q=milestone%3A3+is%3Aclosed
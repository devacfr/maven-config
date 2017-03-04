# Release notes

The history of Maven config releases is documented below. For details of changes refer to the [project's GitHub issues][maven-config-issues] or the [GitHub report][github-report].

[maven-config-issues]: http://github.com/devacfr/maven-config/issues?state=closed
[github-report]: github-report.html

## Release 8 (18 Sep 2016)

### Maintenance 
- Update documentation and fix error link. ([3837126](https://github.com/devacfr/maven-config/commit/38371268a70d0004e38ff08e20b6dc26967af3b3) )
- Bump maven release plugin to 2.5.3 ([f4ca3f3](https://github.com/devacfr/maven-config/commit/f4ca3f379342aec8fe10142704fdb2bfe96c889b) )

### Bug fix
- Fix execution of m2e-code-quality FindBugs Maven Eclipse plugin. ([&#35;21][issue-21])

See [all GitHub issues for 8][maven-config-8] for further details.

[maven-config-8]: https://github.com/devacfr/maven-config/issues?utf8=%E2%9C%93&q=milestone%3A8%20is%3Aclosed%20
[issue-21]: https://github.com/devacfr/maven-config/issues/21

## Release 7

### Enhancement
- Activate gpg sign only during releasing ([&#35;14][issue-14])
- Upgrade to maven 3.2.x ([&#35;12][issue-12])
- Add logback dependency ([&#35;16][issue-16])
- Add jgitflow dependency ([&#35;17][issue-17])
- Add java formatter using eclipse file format ([&#35;18][issue-18])
- Bundle up Legal resources as a remote-resource. ([&#35;9][issue-9])
- Guava upgrade to 18.0


### Maintenance 
- Bumps Spring version to 4.2.5.RELEASE. ([&#35;20][issue-20])
- Remove Repositories reference from maven-config Pom's ([&#35;10][issue-10])
- Remove unnecessary PMD rules
- Remove Atlassian dependencies
- Enforce using m2e-code-quality extension in Eclipse



[issue-9]: https://github.com/devacfr/maven-config/issues/9
[issue-10]: https://github.com/devacfr/maven-config/issues/10
[issue-12]: https://github.com/devacfr/maven-config/issues/12
[issue-14]: https://github.com/devacfr/maven-config/issues/14
[issue-16]: https://github.com/devacfr/maven-config/issues/16
[issue-17]: https://github.com/devacfr/maven-config/issues/17
[issue-18]: https://github.com/devacfr/maven-config/issues/18
[issue-20]: https://github.com/devacfr/maven-config/issues/20

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

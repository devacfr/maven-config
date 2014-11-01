
# Tips

This section give tips and good practices on project management.

## How do you release locally (offline) with git ?

Execute maven `release:prepare` goal

	mvn release:prepare -DpushChanges=false -DremoteTagging=false

Execute maven `release:perform` goal

	mvn release:perform -DlocalCheckout=true
	
## How do you clean project folder ?
 
Use git with command `clean`

	git clean -d -f -x

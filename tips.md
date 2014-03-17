
Tips
====


### How do you release locally (offline) ?
Execute maven `release:prepare` goal

	mvn release:prepare -DpushChanges=false -DremoteTagging=false

Execute maven `release:perform` goal

	mvn release:perform -DlocalCheckout=true

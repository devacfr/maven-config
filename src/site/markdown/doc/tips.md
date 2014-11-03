
# Tips

This section give tips and good practices on project management.

## How do you release locally (offline) with git ?

Execute Maven `release:prepare` goal

```bash
mvn release:prepare -DpushChanges=false -DremoteTagging=false
```

* `pushChanges` parameter allows pushing changes using the local instead the upstream repository.
* `remotingTagging` parameter doesn't explicit in release plugin document, but prevents the duplicate tagging while you need execute prepare goal once again after failure.

Execute Maven `release:perform` goal

```bash
mvn release:perform -DlocalCheckout=true
```	

The `localCheckout` parameter allows using a local checkout instead of doing a checkout from the upstream repository.

## How do you clean project folder ?
 
Use Git with command `clean`.

```bash
git clean -xdf
```
This command removes all untracked files.

## Commands
### svn 
In most cases, local directory and URLs are interchanagable. This docuemnts the most common scenarios I have encountered.
* *Branch* : From one level above the directory to branch `svn copy --revision ##### ./directory-to-branch URL-to-branch-directory-under` e.g. `apps$ svn copy --revision 1234 ./awesome-app https://repo/branches/apps/feature-1/awesome-app`
* *Merge branch to trunk* (reintegrate) : From the trunk directory `svn merge --reintegrate URL-to-branch` e.g. using the branch aexample above `apps/awesome-app$ svn merge --reintegrate https://repo/branches/apps/feature-1/awesome-app`

## Commands
### svn 
In svn a merge of x with y is written as  `merge x:y`. If `x` is after `y` it's called a __reverse merge__.
In most cases, local directory and URLs are interchanagable. This docuemnts the most common scenarios I have encountered.
* __Branch__ : From one level above the directory to branch `svn copy --revision ##### ./directory-to-branch URL-to-branch-directory-under` e.g. `apps$ svn copy --revision 1234 ./awesome-app https://repo/branches/apps/feature-1/awesome-app`
* __Merge branch to trunk (reintegrate)__ : From the trunk directory `svn merge --reintegrate URL-to-branch` e.g. using the branch example above `apps/awesome-app$ svn merge --reintegrate https://repo/branches/apps/feature-1/awesome-app`. 
  * Please note - You only get once chance to re-integrate.
* __Hotfix In Place__: This handles the situation where you only have a single branch, you have cheked in work and you have to pulish a hotfix and overlay all your work on top of the hot fix
  * `cd` to the project directory
  * update `svn` and find current revision using `svn info`. This is __Rp__ (revision in progress)
  * Find the revision for deployed build, let us call it __Rd__. 
  * Reverse merge HEAD to Rd using 
    ```bash
    svn merge -r HEAD:Rd
    ```
  * This will result in a new revision where the soruce tree is identical to Rd, Let us  call this revision __Rd1__.
  * Now apply the hotfix to the code, since it's identical to the deployed codebase, there is a very low risk of regression issues.
 
### Oracle
* __to_date__ : `TO_DATE(date-string, picture-string)` e.g `TO_DATE('2016-12-29 13:30:59','YYYY-MM-DD HH24:MI:SS')`
* __Timestamp with timezone__ : `TO_TIMESTAMP_TZ('2018-12-14TIME13:45:29-8:00', 'YYYY-MM-DD"TIME"HH24:MI:SSTZH:TZM')`Convert December 14th, 2018 13:45:29 PACIFIC to time stamp. Note the word __`TIME`__ in double quotes
### Kotlin
* Always use `.?` for `null` check.
``` kotlin
      val one :Long = 1;
        one.takeIf { one == 2L }?.run{
            fail()
        }
        var  took:Boolean  = false;
        one.takeIf { one == 1L }?.let{
          it
        }?: fail()
```
* `inline` functions allow return out of the outer block.

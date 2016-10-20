# doc-susemanager-new

#suse.com Documentation STABLE#
![](http://i560.photobucket.com/albums/ss45/joecayouette/docuimage_2.png)


##This Branch will be used for all stable topics added during a suse manager sprint.##

These may be published as often as every 2 weeks to SUSE.com and should only include topics that are stable and not based on new features. 

##For Newer Feature Docs Check out the Develop Branch##

##Contributing##

If you would like to contribute, please fork this repository and send pull requests.

Contributors with direct access to the repository are encouraged to use the git-flow-avh workflow (package git-flow-avh).
Note:
	
Please do not make any commits to the master branch. master is reserved for releases only. 



##Preparing and Publishing Online Documentation (suse.com/documentation)##

ATM (2016-07-13), you must use a recent `daps` checkout from
`git@github.com:openSUSE/daps.git`.

Switch to the directory of the documentation checkout and enter:

```
.../daps/bin/daps --dapsroot .../daps -d DC-create-all online-docs
```

Repeat it for all the `pdfsub` packages listed in `DEF-susemanager-docs`:

```
.../daps/bin/daps --dapsroot .../daps -d DC-DC-susemanager-getting-started online-docs
.../daps/bin/daps --dapsroot .../daps -d DC-DC-susemanager-reference online-docs
.../daps/bin/daps --dapsroot .../daps -d DC-DC-susemanager-best-practices online-docs
.../daps/bin/daps --dapsroot .../daps -d DC-DC-susemanager-advanced-topics online-docs
```

Copy the results to the results to your `~/Exports` directory.

```
mkdir ~/Export/susemanager-3
cp -va build/{create-all,susemanager-advanced-topics,\
susemanager-best-practices,susemanager-reference,\
susemanager-getting-started}/online-docs/* ~/Export/susemanager-3 
```

Create a bug (Classification: Doc Tools, Product: Doc Production,
Component: SUSE Manager) and ask to update
[http://www.suse.com/documentation/suse-manager-3](http://www.suse.com/documentation/suse-manager-3)
accordingly.  As an example, see [bug
975925](https://bugzilla.suse.com/show_bug.cgi?id=975925) or [bug
981142](https://bugzilla.suse.com/show_bug.cgi?id=981142).


##Updating SUSE Manager API Documentation and Posting Online##

SUSE Manager 3 (SLE 12 SP1 example):

```
# rename existing directory
old binaries

# checkout the official binary packages
iosc getbinaries SUSE:SLE-12-SP1:Update:Products spacewalk-java standard x86_64

# get the docbook file
unrpm binaries/spacewalk-java-apidoc-sources*
# ==>
# usr/share/doc/packages/spacewalk-java/xml/susemanager_api_doc.xml

# build the PDF with daps:
daps -m usr/share/doc/packages/spacewalk-java/xml/susemanager_api_doc.xml pdf
```

Then create a bug (Classification: Doc Tools, Product: Doc Production,
Component: SUSE Manager) and ask to update
suse.com/documentation/suse-manager-3 accordingly.  As an example, see
https://bugzilla.suse.com/show_bug.cgi?id=976225 .

##Publishing Release Notes on https://www.suse.com/releasenotes/##

If not already done, ask Rudi or Lars (Vogt) to mirror the release notes
from the release repo, and then add the new version to
https://www.suse.com/releasenotes/ .  After publishing the first update,
you probably ask Rudi or Lars again to the mirror script.

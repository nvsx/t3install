# Sitepackage

*The sitepackage is respnsible for our website.*

There are multiple ways to set up a sitepackage, e.g. 

1. Create your own files
2. Use https://sitepackagebuilder.com/
3. Use https://github.com/nvsx/t3sitepackage1

We apply third solution. The "t3sitepackage" is a sitepackage created by Sitepackagebuilder (2.). But it also provides a composer snippet we will use to modify the composer.json file. 

## Get the sitepackage code

```sh
$ git clone https://github.com/nvsx/t3sitepackage1.git
$ mkdir ext
$ mv t3sitepackage1/sitepackage ext
$ cat t3sitepackage1/composer-snippet.txt
```

## Give Composer the info about where to find the sitepackage

Include these four lines of code at the beginning of composer.json. 
Composer.json then looks like so:
```
  1 {
  2     "repositories": [
  3         { "type": "path", "url": "./ext/*" },
  4         { "type": "composer", "url": "https://composer.typo3.org/" }
  5     ],
  6     "name": "typo3/cms-base-distribution",
```
Before it was something like this:
```
  1 {
  2     "name": "typo3/cms-base-distribution",
  3     "description" : "TYPO3 CMS Base Distribution",
  4     "license": "GPL-2.0-or-later",
  5     "config": {
  6         "platform": {
```

After this, we have a modified version of "composer.json" and a new directory "ext/sitepackage/" with content. We now can remove the other files completely:

```sh
$ rm -rf t3sitepackage1
$ # we also see, that the sitepackage extension is not installed yet:
$ # there even exists no "ext" directory yet 
$ ls -l public/typo3conf
```

## Install sitepackage

Now we need to get Composer up to date and install the sitepackage. 
(This might be a tricky one. We use "dev-master" here, because we are in the master branch of our repository. It might depend on your actual environment.)

```sh
$ ddev composer update
$ ddev composer require snakeoil/sitepackage:dev-main
$ # now take a look at what we have in our extension folder:
$ ls -l public/typo3conf/ext
```

### Work in browser

- Open https://mysite.ddev.site/typo3
- Go to the "Page" Module
- Create our homepage: 
	- New page
	- Property Behaviour: Use as root page
	- Property Access: Page visible
- Go to the "Templates" Module
	- Dropdown "Info/Modify"
	- Klick on "Edit the whole template record"
	- Completely empty "Constants" and "Setup"
	- Tab "Includes": Add "Sitepackage" to selected items
	- Save and close
- Open homepage: https://mysite.ddev.site/
- Create more pages under "Home"

## Next steps

This project ends here. For further development see other project: 
- https://github.com/nvsx/t3website1

"t3website1" will be based on the code of this project. 

***

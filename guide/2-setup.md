# Starting a project

### Prerequisites

- Docker
- DDev
- PHP
- Composer
- (see 1-environment.md)

---

## 1. Configure project directory
```sh
$ ddev config --project-type typo3 --project-name mysite --docroot public --create-docroot
```

## 2. Install TYPO3
```
$ ddev composer create typo3/cms-base-distribution
```

## 3. Start Ddev
```sh
$ ddev start
$ ddev describe
```

## 4. Activate project via browser window
- touch public/FIRST_INSTALL
- Open browser window: https://mysite.ddev.site/typo3/install.php
- Take me straight to the backend (no empty starting page)
- Login to backend

## 5. Git Configuration

If you are working with Git, then adjust the following file created by Ddev. Otherwise your installation will not work when depoyed on a remote Server: ```public/typo3conf/.gitignore```

Remove the line with "AdditionalConfiguartion.php", because this file is needed on the server. Also depending on the version of Ddev remove all lines but ```# You can remove the above line if you want to edit and maintain this file yourself.```, because we do not want Ddev to hide any files. 

--- 

## Result

We now have a working TYPO3-Installation. But only the backend can be used. There is no configuration for the frontend yet. See next step on how to install a sitepackage and create pages. 

***

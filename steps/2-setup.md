# Starting a project

### Prerequisites

- Docker
- DDev
- PHP
- Composer
- see steps/1-environment.md

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
- Open browser window: https://mysite.ddev.site/typo3/install.php
- touch public/FIRST_INSTALL
- Take me straight to the backend (no empty starting page)
- Login to backend

--- 

## Result

We have a working TYPO3-Installation. But only the backend can be used. There is no configuration for the frontend yet. See next step how to install a sitepackage and create pages. 

***

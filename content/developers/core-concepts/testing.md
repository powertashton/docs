---
title: "Automated Testing"
categories: ["testing"]
tags: []
weight: 80
contributors: ["skuipers", "powertashton"]
---

Gibbon uses [PHPUnit](https://phpunit.de/) and [Codeception](https://codeception.com/) for automated testing, introduced in v14.0.00. Both testing frameworks can be installed and configured to run in your localhost.

> Note: Our refactoring efforts are ongoing, and the code coverage for automated tests is not all-encompassing. A passing test does not guarantee a working codebase: please always test manually too.

### PHPUnit ###
PHPUnit tests can be run with the `phpunit .` command in the /tests folder

### Codeception ###
Codeception tests can be run with the `codecept run [suite] --env [environment]` command in the /tests folder

As of Gibbon v21.0.00, using Codeception 4.*, to run tests you will need to define your environment using a yaml file in tests/config/envs. A default yaml file is present, named env.yml, that assumes you are running on a localhost installation with database username and password both set to `root`. 

For example, using the default environment yaml to run the install suite, which installs Gibbon using the parameters in /tests/install/InstallCept, you would run the command; `codecept run install --env env`  in the /tests folder. After running the install suite, or if you have already installed gibbon, you can then run the acceptance suite tests in a similar fashion with `codecept run acceptance --env env`.

Codeception involves integration testing and makes use of a database connection; it will not run unless explicitly enabled. To enable Codeception testing in Gibbon, add the following to your config.php file:

```php
$testEnvironment = 'codeception';
```

### Travis CI ###

Pull requests and commits to the development branch are automatically built & tested using [Travis CI](https://travis-ci.org/GibbonEdu/core).

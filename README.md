# composer-npm-experiment
### Use case #1: run `composer install` in the root module
1.  open the `root-module` folder
2. run `composer install`

**Expected behavior:** Both npm `dependencies` and `devDependencies` should get installed 
for every modules.

### Use case #2: run `composer install --no-dev` in the root module
1. open the `root-module` folder
2. run `composer install --no-dev`

**Expected behavior:** Only the npm `dependencies` should get installed for every modules.

### Use case #3: run `composer update` in the root module
1. open the `root-module` folder
2. run `composer update`

**Expected behavior:** Both npm `dependencies` and `devDependencies` should get updated 
for every modules.

**Downside:** The `composer update` executes the `npm update` command in the module's folder 
which can cause unexpected updates in the module's npm packages and also unnecessary changes
in the `package-lock.json`. To prevent this update we need to run `npm shrinkwrap` every time
if we modify dependencies in a module and push the `npm-shrinkwrap.json` into the repository.

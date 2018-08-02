Installing NPM and React
=========================

### Install CURL
```
sudo apt-get install curl
```

### Install Node
```
sudo curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
sudo apt-get install -y nodejs
```

### Create a directory and change current path to it
```
mkdir react_doc
cd react_doc
```

### Create react application installer
```
sudo npm install -g create-react-app
```

### Create new react project
```
create-react-app mate-app
```

### Change to app directory
```
cd mate-app
```

### Install dependencies
```
npm install
```

### To run app
```
npm start
```

Install Yarn
================================================

### Why Yarn?
Fast, reliable, and secure dependency management.

Some reasons you might want to use REST framework:

* <b> Fast: </b> Yarn caches every package it has downloaded, so it never needs to download the same package again. It also does almost everything concurrently to maximize resource utilization. This means even faster installs.
* <b> Reliable: </b> Using a detailed but concise lockfile format and a deterministic algorithm for install operations, Yarn is able to guarantee that any installation that works on one system will work exactly the same on another system.
* <b> Secure: </b> Yarn uses checksums to verify the integrity of every installed package before its code is executed.
* <b> Offline Mode: </b> If you've installed a package before, then you can install it again without an internet connection.
* <b> Deterministic: </b> The same dependencies will be installed in the same exact way on any machine, regardless of installation order.
* <b> Network Performance: </b> Yarn efficiently queues requests and avoids request waterfalls in order to maximize network utilization.
* <b> Network Resilience: </b> A single request that fails will not cause the entire installation to fail. Requests are automatically retried upon failure.
* <b> Flat Mode: </b> Yarn resolves mismatched versions of dependencies to a single version to avoid creating duplicates.

### Environment

* <b> Operating System</b> : Ubuntu 16.04 LTS (64-bit)
* <b> Node</b> : 8.9.3
* <b> NPM</b> : 5.6.0


#### Install Yarn globally
```
sudo npm install -g yarn
```

#### Install all packages listed in `package.json` (equivalent to `npm install`)
```
yarn
```

#### Install new package and add to `package.json` (equivalent to `npm install --save <package_name>`)
```
yarn add <package_name>
```

# SoftwareTesting

TEST CASES

1. LANDING PAGE
 - should have page title
 - should have page description
 - should have login form presented
2. LOGIN VALIDATION
 - should click login button with empty credentials and displays missing credentials
 - should click login button with invalid credentials and displays invalid credentials
 - should click login button with valid credentials and navigate to dashboard
3. REGISTER VALIDATION
 - should click register button with empty fields and display empty notification messages
 - should register successfully
4. DASHBOARD PAGE
 - should have a logout link visible
 - should logout when logout link is clicked

GITHUB LINKS

* [Bontia](https://github.com/aygeehammerrr)
* [Mendez](https://github.com/ChristianMae)
* [Sayon](https://github.com/VinceKlaus)
* [Tulang](https://github.com/nikkotulang)
* [Benemerito](https://github.com/sbenemerito)
* [Ayuste](https://github.com/kbayuste)
* [Rama](https://github.com/jesram1012)
* [Salarza](https://github.com/jsalarza)
* [Po](https://github.com/eleanorkategpo)
* [Bonilla](https://github.com/abebonilla1997)

<!--

* [Nacario](https://github.com/justjhey02)
* [Dellosa](https://github.com/cjdellosa)

-->

<hr/>

#Automated Testing

* ```$ mkdir Lastname_101916```
* ```$ cd Lastname_101916```
* ```$ npm init```
  * name: default
  * version: default
  * description: Sample Test
  * entry point: default
  * test command: wdio
  * git repository: your git repo
  * keywords: UIC, Software Testing, Automation Test, Webdriver IO
  * author: your name
  * license: default
  * yes
* ```$ sudo npm install webdriverio --save-dev```
* ```$ npm test```
  * On my local machine
  * mocha
  * Yes
  * ```./test/**/*.js```
  * spec
  * Yes
  * selenium-standalone
  * Yes
  * command
  * default
  * What is the base url: ```http://webdriver.io```
* ```wdio.conf.js``` has been created
* Choose ```chrome``` as the browser and download chrome web driver [here](http://chromedriver.storage.googleapis.com/index.html?path=2.24/)
* Create a test file: ```test/test-homepage.js```

    ```javascript
    var assert = require('assert');
    describe('webdriver.io page', function() {
        it('should have the right title', function () {
            browser.url('/');
            var title = browser.getTitle();
            assert.equal(title, 'WebdriverIO - Selenium 2.0 javascript bindings for nodejs');
        });
    });
    ```

* Execute test scripts : ```$ npm test```
  >if error occurs "Couldn't not connect to selenium server", You may install selenium-standalone via ```$ sudo npm install selenium-standalone``` then start it on a separate terminal via ```$ selenium-standalone start``` or ```$ ./node_modules/.bin/selenium-standalone start ```
* This time test script must pass. ```should have the right title``` test case has been accepted.
* Modify your script and add another test case
    ```javascript
    var assert = require('assert');
        describe('webdriver.io page', function() {
            it('should have the right title', function () {
                browser.url('/');
                var title = browser.getTitle();
                assert.equal(title, 'WebdriverIO - Selenium 2.0 javascript bindings for nodejs');
            });
            it('should have the link to the API page', function () {
                browser.url('/');
                var hasApiLink = browser.isExisting('=API');
                assert(hasApiLink);
            });
    });    
    ```
* Other Sample Test Scripts
```javascript
it.only('should take you to the API page', function () {
    browser.url('/');
    browser.click('=API');
    
    var title = browser.getTitle();
    assert.equal(title,'WebdriverIO - API Docs');
    
    //browser.pause(2000);
});
```

```javascript
it.only('should filter search results', function () {
    browser.url('/api.html');
    
    browser.setValue('input[name="search"]','debug');
    
    browser.saveScreenshot('api-with-result.png');
    //browser.pause(2000);
});
```

```javascript
var assert = require('assert');
var request = require('request');
//applitools - Visual Test Automation

```
* Organizing it thru Test Suites
```javascript
var assert = require('assert');
    describe('webdriver.io page', function() {
        it('should have the right title', function () {
            this.timeout(99999999);
            browser.url('/');
            var title = browser.getTitle();
            assert.equal(title, 'WebdriverIO - Selenium 2.0 javascript bindings for nodejs');
            
            browser.debug();
        });
        
        describe('Api Page', function(){
            it('should have a link to it from the homepage', function () {
                browser.url('/');
                var hasApiLink = browser.isExisting('=API');
                assert(hasApiLink);
            });
            it('should take you to the API page', function () {
                browser.url('/');
                browser.click('=API');
                
                var title = browser.getTitle();
                assert.equal(title,'WebdriverIO - API Docs');
                //browser.pause(2000);
            });
            
            it('should filter search results', function () {
                browser.url('/api.html');
                
                browser.setValue('input[name="search"]','debug');
                
                browser.saveScreenshot('api-with-result.png');
                //browser.pause(2000);
            });            
        });
}); 

//describe.skip()
//describe.only()
```
* 

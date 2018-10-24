# Youtube-Automated-Selenium-Test

Here are my results from running an Automated Test on the YouTube site

#### This is the code I used to run the test:

var webdriver = require('selenium-webdriver'),
    By = webdriver.By,
    until = webdriver.until;

var driver = new webdriver.Builder()
    .forBrowser('chrome')
    .build();

driver.get('http://www.youtube.com');

driver.findElement(By.name('q')).sendKeys('driver');

driver.sleep(1000).then(function() {
  driver.findElement(By.name('q')).sendKeys(driver.Key.TAB);
});

driver.findElement(By.name('btnK')).click();

driver.sleep(2000).then(function() {
  driver.getTitle().then(function(title) {
    if(title === 'driver - Google Search') {
      console.log('Test passed');
    } else {
      console.log('Test failed');
    }
    driver.quit();
  });
});

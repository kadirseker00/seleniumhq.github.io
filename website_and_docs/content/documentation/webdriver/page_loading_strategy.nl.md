---
title: "Page loading strategy"
linkTitle: "Page loading strategy"
weight: 8
aliases: ["/documentation/nl/webdriver/page_loading_strategy/"]
---

{{% pageinfo color="warning" %}}
<p class="lead">
   <i class="fas fa-language display-4"></i> 
   Page being translated from 
   English to Dutch. Do you speak Dutch? Help us to translate
   it by sending us pull requests!
</p>
{{% /pageinfo %}}

Defines the current session's page loading strategy. 
By default, when Selenium WebDriver loads a page, 
it follows the _normal_ pageLoadStrategy. 
It is always recommended to stop downloading additional 
resources (like images, css, js) when the page loading takes lot of time.

The `document.readyState` property of a document describes the loading state of the current document.
By default, WebDriver will hold off on responding to a `driver.get()` (or) `driver.navigate().to()` 
call until the document ready state is `complete`

In SPA applications (like Angular, React, Ember) once the dynamic content 
is already loaded (I.e once the pageLoadStrategy status is COMPLETE), 
clicking on a link or performing some action within the page will not make a new request 
to the server as the content is dynamically loaded at the client side without a full page refresh. 

SPA applications can load many views dynamically 
without any server requests, So pageLoadStrategy 
will always show `COMPLETE` status until 
we do a new `driver.get()` and `driver.navigate().to()`

WebDriver _pageLoadStrategy_ supports the following values:

## normal

This will make Selenium WebDriver to wait for the entire page is loaded. 
When set to **normal**, Selenium WebDriver waits until the 
[load](https://developer.mozilla.org/en-US/docs/Web/API/Window/load_event) event fire is returned.

By default **normal** is set to browser if none is provided.

{{< tabpane langEqualsHeader=true >}}
  {{< tab header="Java" >}}
import org.openqa.selenium.PageLoadStrategy;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeOptions;
import org.openqa.selenium.chrome.ChromeDriver;

public class pageLoadStrategy {
    public static void main(String[] args) {
        ChromeOptions chromeOptions = new ChromeOptions();
        chromeOptions.setPageLoadStrategy(PageLoadStrategy.NORMAL);
        WebDriver driver = new ChromeDriver(chromeOptions);
        try {
            // Navigate to Url
            driver.get("https://google.com");
        } finally {
            driver.quit();
        }
    }
}
  {{< /tab >}}
  {{< tab header="Python" >}}
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
options = Options()
options.page_load_strategy = 'normal'
driver = webdriver.Chrome(options=options)
# Navigate to url
driver.get("http://www.google.com")
driver.quit()

  {{< /tab >}}
  {{< tab header="CSharp" >}}
using OpenQA.Selenium;
using OpenQA.Selenium.Chrome;

namespace pageLoadStrategy {
  class pageLoadStrategy {
    public static void Main(string[] args) {
      var chromeOptions = new ChromeOptions();
      chromeOptions.PageLoadStrategy = PageLoadStrategy.Normal;
      IWebDriver driver = new ChromeDriver(chromeOptions);
      try {
        driver.Navigate().GoToUrl("https://example.com");
      } finally {
        driver.Quit();
      }
    }
  }
}
  {{< /tab >}}
  {{< tab header="Ruby" >}}
require 'selenium-webdriver'
caps = Selenium::WebDriver::Remote::Capabilities.chrome
caps.page_load_strategy='normal'

driver = Selenium::WebDriver.for :chrome, :desired_capabilities => caps
driver.get('https://www.google.com')
  {{< /tab >}}
  {{< tab header="JavaScript" >}}
const {Builder, Capabilities} = require('selenium-webdriver');
const caps = new Capabilities();
caps.setPageLoadStrategy("normal");
(async function example() {
    let driver = await new Builder().
                withCapabilities(caps).
                forBrowser('chrome').
                build();
    try {
        // Navigate to Url
        await driver.get('https://www.google.com');
    }
    finally {
        await driver.quit();
    }
})();
  {{< /tab >}}
  {{< tab header="Kotlin" >}}
import org.openqa.selenium.PageLoadStrategy
import org.openqa.selenium.chrome.ChromeDriver
import org.openqa.selenium.chrome.ChromeOptions

fun main() {
    val chromeOptions = ChromeOptions()
    chromeOptions.setPageLoadStrategy(PageLoadStrategy.NORMAL)
    val driver = ChromeDriver(chromeOptions)
    try {
        driver.get("https://www.google.com")
    }
    finally {
        driver.quit()
    }
}
  {{< /tab >}}
{{< /tabpane >}}

## eager

This will make Selenium WebDriver to wait until the 
initial HTML document has been completely loaded and parsed, 
and discards loading of stylesheets, images and subframes.

When set to **eager**, Selenium WebDriver waits until 
[DOMContentLoaded](https://developer.mozilla.org/en-US/docs/Web/API/Document/DOMContentLoaded_event) event fire is returned.

{{< tabpane langEqualsHeader=true >}}
  {{< tab header="Java" >}}
import org.openqa.selenium.PageLoadStrategy;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeOptions;
import org.openqa.selenium.chrome.ChromeDriver;

public class pageLoadStrategy {
    public static void main(String[] args) {
        ChromeOptions chromeOptions = new ChromeOptions();
        chromeOptions.setPageLoadStrategy(PageLoadStrategy.EAGER);
        WebDriver driver = new ChromeDriver(chromeOptions);
        try {
            // Navigate to Url
            driver.get("https://google.com");
        } finally {
            driver.quit();
        }
    }
}
  {{< /tab >}}
  {{< tab header="Python" >}}
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
options = Options()
options.page_load_strategy = 'eager'
driver = webdriver.Chrome(options=options)
# Navigate to url
driver.get("http://www.google.com")
driver.quit()
  {{< /tab >}}
  {{< tab header="CSharp" >}}
using OpenQA.Selenium;
using OpenQA.Selenium.Chrome;

namespace pageLoadStrategy {
  class pageLoadStrategy {
    public static void Main(string[] args) {
      var chromeOptions = new ChromeOptions();
      chromeOptions.PageLoadStrategy = PageLoadStrategy.Eager;
      IWebDriver driver = new ChromeDriver(chromeOptions);
      try {
        driver.Navigate().GoToUrl("https://example.com");
      } finally {
        driver.Quit();
      }
    }
  }
}
  {{< /tab >}}
  {{< tab header="Ruby" >}}
require 'selenium-webdriver'
caps = Selenium::WebDriver::Remote::Capabilities.chrome
caps.page_load_strategy='eager'

driver = Selenium::WebDriver.for :chrome, :desired_capabilities => caps
driver.get('https://www.google.com')
  {{< /tab >}}
  {{< tab header="JavaScript" >}}
const {Builder, Capabilities} = require('selenium-webdriver');
const caps = new Capabilities();
caps.setPageLoadStrategy("eager");
(async function example() {
    let driver = await new Builder().
                withCapabilities(caps).
                forBrowser('chrome').
                build();
    try {
        // Navigate to Url
        await driver.get('https://www.google.com');
    }
    finally {
        await driver.quit();
    }
})();
  {{< /tab >}}
  {{< tab header="Kotlin" >}}
import org.openqa.selenium.PageLoadStrategy
import org.openqa.selenium.chrome.ChromeDriver
import org.openqa.selenium.chrome.ChromeOptions

fun main() {
    val chromeOptions = ChromeOptions()
    chromeOptions.setPageLoadStrategy(PageLoadStrategy.EAGER)
    val driver = ChromeDriver(chromeOptions)
    try {
        driver.get("https://www.google.com")
    }
    finally {
        driver.quit()
    }
}
  {{< /tab >}}
{{< /tabpane >}}

## none

When set to **none** Selenium WebDriver only waits until the initial page is downloaded.

{{< tabpane langEqualsHeader=true >}}
  {{< tab header="Java" >}}
import org.openqa.selenium.PageLoadStrategy;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeOptions;
import org.openqa.selenium.chrome.ChromeDriver;

public class pageLoadStrategy {
    public static void main(String[] args) {
        ChromeOptions chromeOptions = new ChromeOptions();
        chromeOptions.setPageLoadStrategy(PageLoadStrategy.NONE);
        WebDriver driver = new ChromeDriver(chromeOptions);
        try {
            // Navigate to Url
            driver.get("https://google.com");
        } finally {
            driver.quit();
        }
    }
}
  {{< /tab >}}
  {{< tab header="Python" >}}
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
options = Options()
options.page_load_strategy = 'none'
driver = webdriver.Chrome(options=options)
# Navigate to url
driver.get("http://www.google.com")
driver.quit()
  {{< /tab >}}
  {{< tab header="CSharp" >}}
using OpenQA.Selenium;
using OpenQA.Selenium.Chrome;

namespace pageLoadStrategy {
  class pageLoadStrategy {
    public static void Main(string[] args) {
      var chromeOptions = new ChromeOptions();
      chromeOptions.PageLoadStrategy = PageLoadStrategy.None;
      IWebDriver driver = new ChromeDriver(chromeOptions);
      try {
        driver.Navigate().GoToUrl("https://example.com");
      } finally {
        driver.Quit();
      }
    }
  }
}
  {{< /tab >}}
  {{< tab header="Ruby" >}}
require 'selenium-webdriver'
caps = Selenium::WebDriver::Remote::Capabilities.chrome
caps.page_load_strategy='none'

driver = Selenium::WebDriver.for :chrome, :desired_capabilities => caps
driver.get('https://www.google.com')
  {{< /tab >}}
  {{< tab header="JavaScript" >}}
const {Builder, Capabilities} = require('selenium-webdriver');
const caps = new Capabilities();
caps.setPageLoadStrategy("none");
(async function example() {
    let driver = await new Builder().
                withCapabilities(caps).
                forBrowser('chrome').
                build();
    try {
        // Navigate to Url
        await driver.get('https://www.google.com');
    }
    finally {
        await driver.quit();
    }
})();
  {{< /tab >}}
  {{< tab header="Kotlin" >}}
import org.openqa.selenium.PageLoadStrategy
import org.openqa.selenium.chrome.ChromeDriver
import org.openqa.selenium.chrome.ChromeOptions

fun main() {
    val chromeOptions = ChromeOptions()
    chromeOptions.setPageLoadStrategy(PageLoadStrategy.NONE)
    val driver = ChromeDriver(chromeOptions)
    try {
        driver.get("https://www.google.com")
    }
    finally {
        driver.quit()
    }
}
  {{< /tab >}}
{{< /tabpane >}}


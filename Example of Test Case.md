Test case for a "Hello, World!" web program using Selenium WebDriver in both Python and Java.

### Test Case Scenario:
- Open the web page containing the "Hello, World!" message.
- Verify that the "Hello, World!" message is displayed on the page.

### Python Test Case (using Selenium WebDriver):

```python
import unittest
from selenium import webdriver
from selenium.webdriver.common.by import By

class TestHelloWorld(unittest.TestCase):

    def setUp(self):
        # Set up Chrome WebDriver
        self.driver = webdriver.Chrome()

    def test_hello_world_message(self):
        # Open the web page
        self.driver.get("https://example.com")

        # Find the "Hello, World!" message element
        hello_world_message = self.driver.find_element(By.XPATH, "//h1[contains(text(), 'Hello, World!')]")

        # Verify that the message is displayed
        self.assertTrue(hello_world_message.is_displayed(), "Hello, World! message is not displayed")

    def tearDown(self):
        # Close the WebDriver
        self.driver.quit()

if __name__ == "__main__":
    unittest.main()
```

### Java Test Case (using Selenium WebDriver):

```java
import org.junit.After;
import org.junit.Before;
import org.junit.Test;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

import static org.junit.Assert.assertTrue;

public class TestHelloWorld {

    private WebDriver driver;

    @Before
    public void setUp() {
        // Set up Chrome WebDriver
        System.setProperty("webdriver.chrome.driver", "/path/to/chromedriver");
        driver = new ChromeDriver();
    }

    @Test
    public void testHelloWorldMessage() {
        // Open the web page
        driver.get("https://example.com");

        // Find the "Hello, World!" message element
        boolean isHelloWorldDisplayed = driver.findElement(By.xpath("//h1[contains(text(), 'Hello, World!')]")).isDisplayed();

        // Verify that the message is displayed
        assertTrue("Hello, World! message is not displayed", isHelloWorldDisplayed);
    }

    @After
    public void tearDown() {
        // Close the WebDriver
        if (driver != null) {
            driver.quit();
        }
    }
}
```

### Note:
- Before running the test cases, make sure to replace `"/path/to/chromedriver"` with the actual path to your ChromeDriver executable.
- Both examples use Selenium WebDriver to interact with the web page and verify the presence of the "Hello, World!" message

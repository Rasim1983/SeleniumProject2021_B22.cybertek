June 26th, Saturday

Today's Schedule:
#1- Review
#2- Practices with POM Design Pattern
#3- Synchronization
#4- More review from interview perspective





ALL TOPICS COVERED SINCE SELENIUM (FROM THE INTERVIEW PERSPECTIVE)

- What is Selenium?
    - Selenium is an open source library (jar files) to automate browsers

- Why are we using Selenium? What are the advantages of using selenium?
    - Open source ---> Free
    - supports many programming langugages
    - supports multiple platforms: Windows, Mac, Linux
    - supports multiple browsers
    - There is a huge community behind selenium (using it) which means there are many solutions to any problems

----------------------------------

- What are some of the disadvantages of Selenium?
    - No costumer service
    - No built in reporting. We need to use additional libraries to generate reports.
    - Only web applications : Selenium is restricted with the browser. Therefore only web pages can be automated using selenium.
    - Requires advanced programming language to use Selenium
----------------------------------

- What is a WebElement?
    - Whatever we see on a web page is a WebElement, such as: buttons, links, images etc.

----------------------------------	

- What are the differences between getText and getAttribute method?

    - getText();
        - Return: String
        - Does it accept argument? --> No
        - Which text does it return? Where does it get the text from?
            - Only gets the text from between opening tag and closing tag.

    - getAttribute("attribute");
        - Return: String
        - Does it accept argument? --> Yes
        - What kind of argument does it accept? --> String
        - What does it do with that argument? --> finds matching attribute on a given web element, and returns the attribute's value as a String.
        - Where does it get the text from? --> from the opening tag


		<div id="kadhsf"> SOMETHING </div>

----------------------------------

- What are locators in Selenium?
    - Locators are methods that help us locate WebElements.
    - There are 8 locators
    - linktext, partialLinkText, id, className, name, tagName, cssSelector, xpath


----------------------------------

- How do you decide which locator to use?
- What is your locator strategy?
  #1- If there is "id" I make sure it is not dynamic and use it.
  #2- If not, I check if the "class" attribute is unique using cssSelector.
  #3- If it is a link WebElement, I use linkText
  #4- If none of the previous works/applies, I go for xpath


----------------------------------

- xpath
    - How many types of xpath are there?
    - 2

  #1- Absolute Xpath:
  	- Starts with "/"
  	- Starts from the very beginning of the HTML (root element = html)
  	- It goes down 1by1, therefore it is very long and not dependable
  	- It will easily break with any minimal change in the html code

  #2- Relative Xpath:
  	- Starts with "//"
  	- "//" means it starts from anywhere in the HTML page.
  	- "//" means jump to the given point
  	- Relative xpath is very dependable because we either directly start from the web element we want to locate, or we start from somewhere close (parent or child)
  	- For absolute xpath to break, a direct change must happen to the web element or attribute we are using in the locator

  syntax:
  #1-	//tagName[@attribute='value']

  #2-	//*[@attribute='value']

  #3-	//tagName[.='text']
  	//tagName[text()='text']


-How do you handle dynamic web elements?
#1- I would find a static parent/child and move from there to desired web element
#2- I would use one of the methods provided by xpath locator:
- starts-with
- ends-with
- contains

	//tagName[contains(@attribute,'value')]
	//tagName[starts-with(@attribute,'value')]
	//tagName[ends-with(@attribute,'value')]

-How do we go from parent to child using xpath?
- /
- This will go to direct child
- // --> will go any child regardless of hierarchy (grand childs as well)

-How do we go to parent from child?
- /..
- This will go to direct parent.


----------------------------------

- What is Maven?
    - Build automation tool (mainly) for java project

- Why do we use Maven?
    - Maven helps us create and manage projects easily
    - Maven projects will come with certain folder structure (such as main, test, pom.xml)

- What is build?
    - Repeating steps when we are creating the project, such as: creating the folders, adding, compiling, testing, deploying ( all of these steps are called build)

- What is pom.xml file? Why do we need this file?
    - pom : project object model
    - xml : extensible markup language

    - We add and manage dependencies and their versions from pom.xml file

- Where does maven store all of the dependencies?
    - .m2
    - It is a hidden file in our computer
    - Maven stores dependency related files/folders in .m2
    - If you add dependency or change a version of dependency, and it creates a problem, you might want to consider deleting everything in the .m2 file and "reload" your project.
    - Maven will auto re-download everything, usually fixes the issue.

    - You can and should try to use "invalidate caches and restart" before trying this option

----------------------------------

- What are the difference between findElement() vs findElements() methods?
- findElement()
    - Return type: WebElement
    - Returns a single web element
- What happens if it doesn't find a web element?
    - Throws NoSuchElementException

- findElements()
    - Return type: List<WebElements>
    - Capable of finding and returning multiple web elements in a List of web elements
- What happens if it doesn't find a web element?
    - It will return empty List.
    - It will not throw exception.

----------------------------------

Checkboxes and radio buttons:

	- How do we handle?
	- We locate checkboxes/radiobuttons using any locator and click().

	- How do we verify if checkbox is selected or not?

	- isSelected() method is used to verify.
		- returns "true" if checkbox is selected
		- returns "false" if checkbox is NOT selected


	- isEnabled() method is used to verify if web element can or cannot be clicked/interacted.
		- returns "true" if web element is enabled
		- returns "false" if web element is NOT enabled
		
	syntax: checkbox.click();
			checkbox.isSelected(); --> true/false


----------------------------------

TESTNG
- WHAT IS TESTNG?
- Test is a unit testing framework.
- Originally it was created by a developer for the developers.
- We use TestNG to use some of its annotations, such as (beforeMethod, afterMethod, beforeClass, afterClass etc)

https://testng.org/doc/

- Why do we use the annotations in the TestNG?
    - We change the behavior of java methods and make them TestNG methods.
    - This way we can create certain structure for repeating steps.


----------------------------------

DROPDOWNS:
- How many different types of dropdowns we have?
- 2

	- How do we know if it is a select dropdown or not?
		- We inspect.
		- If tag is <select> it is select dropdown. It means we can use SELECT class on it.

	- Non-Select (html) dropdowns
		- We just locate as regular web element and click.

	- Select dropdowns:
		- We use the SELECT class coming from Selenium library
		- Select class contains methods that are allowing to easy interact with dropdowns

	- How do we handle Select dropdowns?	
		#1- Create object of the select class
			Select selectDropdown = new Select(we pass the select web element);
			Select selectDropdown = new Select(driver.findElement(By.xpath("locator")));

	- How many different ways of selecting from dropdowns?
		- 3

		- selectDropdown.selectByIndex --> accepts the index number. (index start from 0)
		- selectDropdown.selectByValue --> accepts the value of the attribute "value"
		- selectDropdown.selectByVisibleText --> accepts the text of the web element

	- How do we get the currently selected option in a dropdown?
		- selectDropdown.getFirstSelectedOption()
			- Return type: WebElement
			- This method will return the currently selected <option> as a WebElement
			- If we want to get the text of it we need to use .getText()

	- How do we get all of the options from dropdown?
		- selectDropdown.getOptions();
			- Return type: List<WebElement>


----------------------------------

ALERTS/POP-UPS

How many types of alerts do we have?
- 2

	#1- Non-JS Alerts (HTML)
		- If we are able to locate by inspecting, it is HTML (non-js) alert.
		- How do we handle?
		- Locate using any locator and click

	#2- JS Alerts
		- How many types JS alerts are there?
		- 3

		a. warning/information
			- we can only accept()
		b. confirmation
			- we can accept and/or dismiss
		c. prompt
			- we can accept, dismiss and sendKeys.

- How do you handle alerts?
    - Using Alerts (from Selenium)

  syntax:
  Alert alert = driver.switchTo().alert();

  	alert.accept();
  	alert.dismiss();
  	alert.sendKeys("text here");


----------------------------------

- Iframes:
    - What is iframe?
    - Html inside of another html

    - How do you handle it?
    - We need to switch to <iframe> to be able to do any action on any web element inside of it.

    - How many ways we have to switch?
    - 3 ways to switch to an iframe.

  syntax: driver.switchTo().frame();

  1- index

  	driver.switchTo().frame(0);
  	driver.switchTo().frame(1);

  2- id, name (if there is)

  	driver.switchTo().frame("id");
  	driver.switchTo().frame("name");

  3- web element
  WebElement iframe = driver.findElement(By.LOCATOR);
  driver.switchTo().frame(iframe);

  	driver.switchTo().frame(driver.findElement(By.LOCATOR));


----------------------------------

WINDOWS/TABS

- What is the difference between a window and a tab for selenium?
    - They are same for selenium.

- What is a window handle?
    - It is a randomly generated alphanumeric string unique to each window.

- How do we handle windows?
    - We handle windows using windowHandles and methods returning us those.

- How do we get current window's handle?
    - driver.getWindowHandle();
        - Return type: String
        - Unique window handle of currently focused window/tab


- How do we get all windows' handle?
    - driver.getWindowHandles();
        - Return type: Set<String>

syntax: driver.switchTo().window(windowHandle);

----------------------------------

Actions:
- What Actions class is used for?
- Advanced mouse and keyboard operations
- doubleClick
- moveToElement
--> used for hovering as well
--> used for scrolling as well
- clickAndHold
- dragAndDrop
- release
- contextClick (right click)

	- How to use it?
	- Create an object of Actions class to reach methods

	Actions actions = new Actions(Driver.getDriver);

	actions.dragAndDrop(source, target).perform();


-----------------------------------------------------------------------------------------------

JavaScriptExecutor:
- It is a simple interface allows us to use(inject) JavaScript functions(methods) in our Java+Selenium code.
- Basically this interface has only two methods.
- These methods accept JavaScript functions as String and apply into our JAVA+SELENIUM code.


-> How do we implement JavaScriptExecutor?
- We downcast our WebDriver type to JavaScriptExecutor type.
- After this we are capable of using JavaScriptExecutor methods with our WebDriver instance methods.

	JavaScriptExecutor js = (JavaScriptExecutor) Driver.getDriver();
	js.executeScript("javaScriptCode");
	js.executeScript("javaScriptCode", arg1, arg2);

- This method can be overloaded for different use cases.

- How many ways do you know how to scroll?
  1- actions --> moveToElement
  2- Keys.PAGE_DOWN and/or Keys.PAGE_UP --> this simulates as if user pressing these buttons from keyboard.
  3- JavaScriptExecutor : js.executeScript("scrollBy");
  4- JavaScriptExecutor : js.executeScript("scrollIntoView");

----------------------------------------------------------------------------------------

---------------------------------------------------------------------------

What is POM Design Pattern:
- Creating .java class for each page of the web application.
- In these classes we store relevant information to that page, such as: WebElements, and re-usable methods

How do you implement it?
#1- Create a constructor and initialize the WebDriver instance with the object of that class.

	public LoginPage(){
		PageFactory.initElements(Driver.getDriver(), this);
	} 


-	public LoginPage() ----> creating a constructor of the class
-  PageFactory ----> This class is coming from Selenium library
    - This class contains methods help us create POM design pattern
- .initElements (arg1, arg2);
    - It accepts 2 arguments
    - 1st arg : WebDriver instance
    - 2nd arg : this --> points to the object of the current class

    - The goal is to be able to use the object of the class to reach the WebElements and also use Selenium methods from other classes.

- Why are we using POM Design pattern?
    - Reusibility
    - Easy to maintain
    - Readability
    - less code
    - cleaner code
    - easy to collaborate in between team members
    - we are centralizing the web elements (and methods) related to each page in its own .java class.

    - handles the StaleElementReferenceException by default

  ajsdf098a70sdfadsfkl;j ---> webelement1
  asdfasdfasdfasdfasdfff ---> webelement1

    - Everytime we try to use a web element in POM Design Pattern, something called 'freshness check' is happening.

-----------------------------------------------------------------------------------------------

TESTBASE
- What is TestBase?
- TestBase is a class we create as parent of all tests in our suite.
- In this class we store re-usable logic.
- We make TestBase abstract because we want to avoid object creation from this class.


-----------------------------------------------------------------------------------------------

properties related content

-----------------------------------------------------------------------------------------------

driver utility related content

-----------------------------------------------------------------------------------------------


	- src
		-main(it not using just delete)
		-test
			-java
				- com.cybertek
					- pages
					- tests
					- utilities
						- Driver
						- ConfigurationReader


	- pom.xml






























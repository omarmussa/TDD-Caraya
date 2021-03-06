# TDD-Caraya
LabVIEW Test Driven Development project template and support (depends on JKI Caraya unit test framework).

The TDD-Caraya project template for LabVIEW enables fast development of unit tests that exist on the same diagram as your actual source code.  This results in easily readable code that does not add execution overhead or source code complexity/configuration management, and has access to private data and methods that are available to the VI.  The goal of TDD-Caraya is to enable TDD/XP programming.

There are three features of the project template (and you are able to completely customize this template as needed).

#Test Template:
A template for creating new VIs where the test vector is in-line with the functional code under test.  By design new VIs generated from the VI template fail a default test implementation.

![Test Template](https://github.com/omarmussa/TDD-Caraya/blob/master/Images/TDD%20VI%20Template.png)

The recommended best practice for each new VI created from the template is to replace the “Caraya Assert” with an appropriate expected result(s) that will be valid once the VI is functional.  It is acceptable to just check for an error but you will likely want to make more specific test(s).  When you are done defining the test, it is a best practice to commit your work to SCC and then start working on functional implementation of your VI to satisfy the test requirements that you just created.  Ideally, when the test passes, your code is functional.

Here’s an example of a finished VI:
![Example Test](https://github.com/omarmussa/TDD-Caraya/blob/master/Images/Example%20Add%20Numbers.png)

The test assertion is inside of a conditional disable structure.  Notice in the example the inputs are also being conditionally configured and this configuration data can come from default values on the front panel, constants, configuration files, etc at the developers discretion.  Additionally, there is a check for if the test is running top level to avoid the test code from running if the VI is running as a subVI of another test.  Since the assertion test is scoped within the VI, the test can run regardless of whether the VI is privately scoped or not.  Additionally, it will get stripped from compilation so you won’t have to worry about it affecting run time performance.

#TDD Flag
The project has a VI that can set the TDD flag so that you can run.  In “TDD Mode”, running the VI will run the Caraya assertion.  Resetting the flag will run the VI normally (for development/simulation probe).  You can change this property manually in your project or by using the “Set TDD Flag.vi” included in the TDD Project Template.

![Set TDD Flag](https://github.com/omarmussa/TDD-Caraya/blob/master/Images/Set%20TDD%20Flag.png)

#Pre-Build Action
One other built in project feature is the ability to autorun your tests as a pre-build action.  The VI will automatically discover and run any Caraya tests in the project prior to running the build (for non-RT targets).  The VI is located in the "Build Support" folder and is called "Pre-Build Action.vi".

The entire TDD Project is a template that is distributed as a VIP package and can be installed into LabVIEW so that you can create a new project using the “Create Project” dialog.

![Create Project](https://github.com/omarmussa/TDD-Caraya/blob/master/Images/Create%20Project.png)

This should make it easier for everyone to start adopting TDD today.

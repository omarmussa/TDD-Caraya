# TDD-Caraya
LabVIEW Test Driven Development project template and support (depends on JKI Caraya unit test framework).  *** This Project is under construction - do not use yet ***

The TDD-Caraya project template for LabVIEW enables fast development of unit tests that exist on the same diagram as your actual source code.  This results in easily readable code that does not add execution overhead or source code complexity/configuration management, and has access to private data and methods that are available to the VI.


There are basically three features to this template (and you are able to completely customize this template as needed).

1 - By default it fails a default test implementation for your code.  This is the feature of the template that makes your coding process TDD.  The best practice is to replace the “Caraya Assert” with your expected result that should signify the VI is functional.  It is acceptable to just check for an error but you may want more specific test.  When you are done, it is a best practice to commit your work to SCC and then start working on implementation of your VI to satisfy the test requirements that you just created.

Here’s an example of a finished VI:


2 - The test assertion is inside of a conditional disable structure.  Notice in the example the inputs are also being conditionally configured and this configuration data can come from default values on the front panel, constants, configuration files, etc at the developers discretion.  Additionally, there is a check for if the test is running top level to avoid the test code from running if the VI is running as a subVI of another test.  Since the assertion test is scoped within the VI, the test can run regardless of whether the VI is privately scoped or not.  Additionally, it will get stripped from compilation so you won’t have to worry about it affecting run time performance.

The project has a VI that can set the TDD flag so that you can run.  In “TDD Mode”, running the VI will run the Caraya assertion.  Resetting the flag will run the VI normally (for development/simulation probe).  You can change this property manually in your project or by using the “Set TDD Flag.vi” included in the TDD Project Template.



3- One other built in project feature is the ability to autorun your tests as a pre-build script.  The VI provided needs to be customized to support running your build test suite but it is a starting point. 



The entire TDD Project is a template that is distributed as a VIP package and can be installed into LabVIEW so that you can create a new project using the “Create Project” dialog.  The built package is distributed via ... (TBD).

This should make it easier for everyone to start adopting TDD today.

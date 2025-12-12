# IBM Compiled Code Coverage  

**IBM Compiled Code Coverage is an extension for Visual Studio Code that provides access to compiled code coverage results produced by IBM debug engines.**

Engines currently supported:
  - IBM Z:  IBM z/OS Debugger


> Go here for the full [Documentation](https://www.ibm.com/docs/en/developer-for-zos/latest) online. 

Simplify your installation experience by using newly bundled extension packs that contain IBM Compiled Code Coverage as well as other extensions available for [IDzEE](https://marketplace.visualstudio.com/items?itemName=IBM.developer-for-zos-on-vscode-extension-pack) and [ADFz](https://marketplace.visualstudio.com/items?itemName=IBM.application-delivery-foundation-for-zos-vscode-extension-pack) customers.

## Table of contents

- [Prerequisites and Corequisites](#prerequisites-and-corequisites)
- [Running Code Coverage Service and Collecting Code Coverage on z/OS](#running-code-coverage-service-and-collecting-code-coverage-on-zos)
- [Viewing Results](#viewing-results)


## Prerequisites and Corequisites

Review the [IBM Compiled Code Coverage Agreement](https://github.com/IBM/zopendebug-about/raw/main/product-licenses/LICENSE.txt), terms and conditions for [separately licensed code](https://github.com/IBM/zopendebug-about/raw/main/product-licenses/NON_IBM_LICENSE.txt), and [Third Party Notices](https://github.com/IBM/zopendebug-about/raw/main/product-licenses/NOTICES.txt) before downloading.

- Client
  - **Prerequisite** [Visual Studio Code](https://code.visualstudio.com/download) version 1.48.2 or later
  - IBM Z
      - **Corequisite**  [IBM Z Open Debug](https://www.ibm.com/docs/en/developer-for-zos/latest?topic=code-debugging-applications): for automatic code coverage service configuration, and result opening.  
- Host 
  - IBM Z
    - **Prerequisite** One of the following for code coverage collection:
      - IBM z/OS Debugger [Remote Debug Service](https://www.ibm.com/docs/en/debug-for-zos/latest?topic=users-adding-support-remote-debug-service): for collecting code coverage for compiled applications running on z/OS and having IBM Compiled Code Coverage automatically add connections and open results
      - IBM z/OS Debugger [Headless Code Coverage](https://www.ibm.com/docs/en/debug-for-zos/latest?topic=gccza-generating-code-coverage-in-headless-mode-using-collector): for collecting code coverage results and running Code Coverage Service via z/OS Unix commands.
      - IBM z/OS Debugger [Headless Code Coverage Started Task](https://www.ibm.com/docs/en/debug-for-zos/latest?topic=asrdu-running-headless-code-coverage-collector-as-started-task): for collecting code coverage results and running Code Coverage Service using a started task
    - **Prerequisite** A valid host registration for [IBM Developer for z/OS Enterprise Edition (IDzEE)](https://www.ibm.com/products/developer-for-zos), [IBM Developer for z/OS Select (IDz Select)](https://www.ibm.com/products/developer-for-zos), [IBM Application Delivery Foundation for z/OS (ADFz)](https://www.ibm.com/products/app-delivery-foundation-for-zos), [IBM Test Accelerator for Z](hhttps://www.ibm.com/products/test-accelerator-z)
    - **NOTE**:   IBM z/OS Debugger PTF 17.0.3.2 level or higher is required.  For more information on service see [Fix list for IBM z/OS Debugger](https://www.ibm.com/support/pages/fix-list-ibm-zos-debugger).


## Running Code Coverage Service and Collecting Code Coverage on z/OS
In order to collect code coverage on z/OS you have one of three options:
1. Using Remote Debug Service:
    - Start Remote Debug Service with code coverage, and in particular Code Coverage Service options enabled.
    - In Z Open Debug, create a connection to the RDS instance.
    - Use a debug profile in Z Open Debug activated in code coverage mode, or alternately instrument your JCL with code coverage options with RDS in the TEST runtime option.  For example ```TEST(,,,RDS&userid:*)```
    - Launch your application in the normal way.
    - Your code coverage result will automatically be opened in VS Code when ready.
1. Using Headless Code Coverage on z/OS UNIX:
    - Start the headless collector via z/OS UNIX, and ensure that you specify appropriate Code Coverage Service options. Note the collector port, along with the code coverage service port.  The code coverage service port will be needed to create a connection to access your results.
    - Use a debug profile in Z Open Debug activated in code coverage mode, or alternately instrument your JCL with code coverage options with RDS in the TEST runtime option. Ensure that the profile has the right IP location and port option to connect to your headless code coverage instance. Alternately instrument your JCL with code coverage options with RDS in the TEST runtime option.  For example ```TEST(,,,TCPIP%localhost:*)``` 
    - Launch your application in the normal way.
1. Using Headless Code Coverage as a started task:
    - Obtain the code coverage collector and Code Coverage Service ports.  The code coverage service port will be needed to create a connection to access your results.
    - Use a debug profile in Z Open Debug activated in code coverage mode, or alternately instrument your JCL with code coverage options with RDS in the TEST runtime option. Ensure that the profile has the right IP location and port option to connect to your headless code coverage instance. Alternately instrument your JCL with code coverage options with RDS in the TEST runtime option.  For example ```TEST(,,,TCPIP%localhost:*)``` 
    - Launch your application in the normal way.

## Viewing Results

To view results:
1. You will need to add a connection to a Code Coverage Service instance by providing the URL for the CCS instance. Note: on IBM Z, when using Remote Debug Service and Z Open Debug, this is not required.
1. After providing credentials, a list of your results appear.
1. Use the context menu to select the View Report action and open the report.


## Tester plugin

The Tester plugin is a tool to help test QGIS core and plugins' functionality. It allows to run automatic and semi-automated tests. The first type of tests runs without the user intervention. The second also includes step-by-step instructions to perform manual or verification tasks.

The Tester plugin is available from the QGIS Official Plugins Repository at <https://plugins.qgis.org>. The plugin currently is in the experimental state, so to install it you should enable experimental plugins in the QGIS Plugin Manager. Note that Tester plugin itself does not contain any tests, the tests are added by installing additional plugins containing tests for specific QGIS functionality. For example, to test QGIS core functionality it is necessary to install Core Tests plugin described below.

### Testing with Tester plugin

We will assume that both Tester plugin and plugins with tests are already installed.

To start a test cycle, open Tester plugin from the menu **Plugins > Tester > Start testing**. The **Test selector** window will be shown with the available tests grouped by categories.

![Test Selector dialog!](/images/test-selector.png)

The list of available tests depends on the installed plugins with tests and can be different across installations and versions.

Inside each category there are two sub-categories: one for fully automated tests and another one with semi-automated tests. Select the tests you want to run with mouse or using one of the buttons at the top of the dialog and then press **Run Selected Test** button. All tests selected in the "Test Selector" dialog will be run sequentially. Once the **Run Selected Test** button pressed the **Test Selector** dialog will be closed and in the upper part of the QGIS map canvas, you will see the **Tester Plugin** dockable panel.

![Tester Plugin panel!](/images/tester-plugin-panel.png)

At the top of the panel a name of the currently running test is shown. Also there are two buttons:

* **Restart Test** to restart currently running test
* **Skip Test** to skip currently running test and start next test (if any)
* **Cancel Testing** to cancel current test cycle and see the test cycle summary

Below there is a the text area where a description of the current step of the running test is shown. At the right there are several buttons:

* **Next Step** button used to go to the next step of the current test. This button is only enabled when the current step is manual and it should be pressed only when all required actions from the test description are completed. In all other cases switching to the next test step is done automatically.
* **Test Passes** used to confirm successful execution of the test.
* **Test Fails** used to mark test as failed.

In most cases the **Test Passes** and **Test Fails** buttons are enabled only when the test reaches its end. However, some tests might contain intermediate manual steps where something has to be verified by the user. In this case, the **Test Passes** and **Test Fails** buttons will be renamed to **Step passes** and **Step fails** and will be enabled.

### Test cycle summary

Once all the selected tests have been run (or skipped), the **Tester Plugin** panel is closed and the **Test Results** dialog is shown.

![Test Results dialog!](/images/test-results.png)

At the top of the dialog there is a groupped list of the tests which were executed. Color of the test depends on its state (passed, failed, skipped, etc).

When test is selected the bottom area shows detailed information about the test execution, including stack trace and other relevant messages.

If test has associated issue, right-clicking on the test name in the list will open a context menu with a single menu entry **Open Issue Page**. Select it to open the corresponding issue page for the test.

## Core Tests plugin

This is a supplementary plugin containing some tests for the QGIS core functionality.

The Core Tests plugin is available from the QGIS Official Plugins Repository at <https://plugins.qgis.org>. The plugin currently is in the experimental state, so to install it you should enable experimental plugins in the QGIS Plugin Manager.

Note that Core Test plugin is only useful when installed together with the Tester plugin.

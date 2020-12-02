# QGIS Testing setup and Workflow

## Introduction

This document aims serves as a reference to anyone willing to participate in the QGIS Manual testing effort. It has information on how to setup a clean testing environment, how to use the testing management system (kiwi CMS), and how to create new test cases.

## What is manual testing

QGIS code is largely covered by automatic tests provided by unit tests. This is by far the preferable way to test and prevent software failure and regressions. Nevertheless, some tasks can't be tested without human interaction or visual feedback. That's where manual testing is helpful. Some examples that need or benefit from manual testing:

- Software installation
- Drag and drop operations (within QGIS and from outside)
- Specific workflows
- Monkey testings (Ad hoc functionality tests for new features)

## Setup an clean testing environment

Ideally, manual testing should be done in the most clean environment as possible. That is:

- Clean and updated operating system installation
- Bare minimum installed software
- Bare minimum user custom configuration changes
- Clean QGIS installation (without any previous install)
- No third party QGIS plugin (except if for testing a plugin)

This pretends to minimizes the risk of tests results being influenced by very specific configuration combinations.

### Using a Virtual Machine

The optimal way to achieve a clean environment is by using virtual machines with a clean operating system install and VM snapshots. The suggested workflow is:

1. Create or grab a clean VM of the operating system you pretend to run the tests.

   * For **Linux** you can find prepared VMs (Virtualbox and VMware)for many distributions in here:
     * https://www.osboxes.org/
   * For **windows 10**, you can get a development virtual machines (Virtualbox, VMware, Parallels and Hyper-V) here:
     * https://developer.microsoft.com/en-us/windows/downloads/virtual-machines/
   * For **Mac OS**, the first requirement is to have Apple hardware, then you need a Mac OS license. We didn't find any ready to go VMs, but the following link instructs how to create one yourself:
     * https://osxdaily.com/2017/04/11/run-macos-virtual-machine-easy-parallels/

      **Note:** Virtualbox does not perform well under Mac OS, you will better served either with VMWare Fusion or Parallels

2. Make sure to update the operating system applying all available updates at the moment. This may require several reboots
3. Install any additional software to help testing (e.g. better text editor, better browser, etc...)
4. Create and setup a shared folder to share files between your host machine and the VM. Use this folder to store sample data and the installers, this helps reducing the VMs size and allow you to re-use those files in other VMs.
5. Create a VM snapshot to store this clean and updated state (this way you can come back to it later to prepare a new test cycle or use it to test QGIS installation procedures)
6. Download and store the QGIS installers on the shared folder.
7. Run the QGIS installation following the instruction for the operating system. **!DON'T START UP QGIS!**
8. Create a VM snapshot of the fresh installed QGIS. This will allow you to came back to this state anytime during the test cycle.

Suggestion: Snapshots are a very helpful feature of virtual machines. Some test cases have very similar initial instructions (for example, the installation of the Tester plugin and the core-tests plugin). You can create a snapshot right after those steps and revert the machine whenever you need to start a new test.

### Using a clean user profile (poor man alternative)

The virtual machine setup requires a significant amount of time to prepare and occupies lots of disk space. Therefore, as a fairly less optimal alternative, for some test cases, testers can (at least) use a new user profile to run tests. This ensures that no plugins are installed, nor any previous QGIS configuration disturbs the results of the test. Unfortunately, it won't help with problems originated by previous QGIS installations or long untraceable configuration changes on the operating system.

To create a new profile, in the menu select **Settings > User profiles > New profile...**

## Testing Management System (Kiwi CMS)

To encourage systematic testing and track its progress for each release, we have setup a Kiwi CMS instance (called a tenant) in https://qgis.tenant.kiwitcms.org/. This open source software allows to describe test cases step by step, organize test plans per release, assign test executions, and log test execution results.

### Register in QGIS tenant

If you want to participate on QGIS testing effort, you should register on the QGIS tenant. The easiest way is to use your Github account to register and login. Go to the link above a select the option Continue with Github in the lower left corner of the page.

Once you are registered on kiwitcms, open a ticket on the https://github.com/qcooperative/qgis-testing repository requesting administrators access to the QGIS tenant.

### Test cases

A **test case** describes the steps or actions to reproduce a certain situation and its expected results. In QGIS testing it should provide instructions for testers to follow. For example, describe which data sample or project to load into QGIS, which steps to open, configure and execute a specific tool, and what are the expected outcomes or outputs.

You can find all existing test cases by going to the menu **Search > Search test cases**. Then, you can open a test case by clicking its name under the `Summary` column.

Currently, we have a limited set of test cases available, but **anyone with access to the QGIS tenant can create additional tests cases**. Because it's impossible to test all QGIS functionality in each release, we encourage the creation of new test cases, either to test possible regressions, generally reported before as bugs, or to promote testing around a new functionality.

Reinforcing what as been said before, these test cases should not be a replacement for in-code unit tests, but a complement for situations were unit tests were not possible to implement because of the need to too many user interaction.

Test cases should be added to one or more test plans, so that they can be executed and reported,


### Adding test cases to

### How to run a test


### How to report an issue


## Tester plugin

The Tester plugin is a tool to help test QGIS core and plugins' functionality. It allows to run automatic and semi-automated tests. The first type of tests runs without the user intervention. The second also includes step-by-step instructions to perform manual or verification tasks.

For more information about its usage see [this page](tester-plugin.md).

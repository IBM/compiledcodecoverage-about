# Change Log

All notable changes to the "IBM Compiled Code Coverage" extension will be documented in this file.

## 1.0.5
- Improvements to accessibility.
- Compiled Code Coverage extension now respects the IBM Z Open Debug extension's Zowe profile ```rejectUnauthorized``` setting when connecting to Code Coverage Service, ignoring certificate errors when set to ```false```.

### Fixes
- Security fixes.
- Fixed an issue where IBM TAZ EDT unit test coverage view only displayed one source file.
- Fixed an issue where IBM TAZ EDT unit test coverage was not displayed when a source file was set to listing mode and the CSECT name differed from the module name.

## 1.0.4
### Fixes
- Security fixes.

## 1.0.3
- Added Test Coverage support for IBM TAZ EDT extension, which will require Debugger for z/OS 17.0.4.1 PTF or later.

### Fixes
- Security fixes.

## 1.0.2
- Added user setting to reuse the Code Coverage results window.

### Fixes
- Security fixes.

## 1.0.1
- User can delete a single code coverage result from any connected result location.
- User can delete multiple results from the same connected result location, or across different connected result locations.
- User can rename a code coverage result from any connected result location.
- User authentication will fall back to use basic authentication when bearer authentication fails/not available.
- Improvements to accessibility.

### Fixes
- Updates to links in README.md for license information and Z Open Debug
- Security fixes.

## [Unreleased]

- Initial release 1.0
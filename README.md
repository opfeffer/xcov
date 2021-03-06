![/assets_readme/gather_coverage.png](/assets_readme/logo.png)
-------
[![Twitter: @FastlaneTools](https://img.shields.io/badge/contact-@carlostify-blue.svg?style=flat)](https://twitter.com/carlostify)
[![License](https://img.shields.io/badge/license-MIT-green.svg?style=flat)](https://github.com/nakiostudio/xcov/blob/master/LICENSE)
[![Gem](https://img.shields.io/gem/v/xcov.svg?style=flat)](http://rubygems.org/gems/xcov)

**xCov** is a friendly visualizer for Xcode's code coverage files.

## Installation
```
sudo gem install xcov
```

## Features
* Built on top of [Fastlane](https://fastlane.tools), you can easily plug it on to your CI environment.
* Generates nice HTML reports.

![/assets_readme/report.png](/assets_readme/report.png)

* Slack integration.

![/assets_readme/slack_integration.png](/assets_readme/slack_integration.png)

## Requirements
In order to make *xCov* run you must:
* Use Xcode 7.
* Have the latest version of Xcode command line tools.
* Set your project scheme as **shared**.
* Enable the **Gather coverage data** setting available on your scheme settings window.

![/assets_readme/gather_coverage.png](/assets_readme/gather_coverage.png)

## Usage
*xCov* analyzes the `.xccoverage` files created after running your tests therefore, before executing xCov, you need to run your tests with either `Xcode`, `xcodebuild` or [scan](https://github.com/fastlane/scan). Once completed, obtain your coverage report by providing a few parameters:
```
xcov -w LystSDK.xcworkspace -s LystSDK -o xcov_output
```

### Parameters allowed
* `workspace` `-w`: Path of your `xcworkspace` file.
* `project` `-p`: Path of your `xcodeproj` file (optional).
* `scheme` `-s`: Scheme of the project to analyze.
* `output_directory` `-o`: Path for the output folder where the report files will be saved.
* `derived_data_path` `-j`: Path of your project `Derived Data` folder (optional).
* `minimum_coverage_percentage` `-m`: Raise exception if overall coverage percentage is under this value (ie. 75)
* `slack_url` `-i`: Incoming WebHook for your Slack group to post results (optional).
* `slack_channel` `-e`: Slack channel where the results will be posted (optional).
* `skip_slack`: Add this flag to avoid publishing results on Slack (optional).

### [Fastlane](https://github.com/fastlane/fastlane/blob/master/docs/Actions.md)
*Fastlane 1.61.0* includes *xCov* as a custom action. You can easily create your coverage reports as follows:
```ruby
xcov(
  workspace: "YourWorkspace.xcworkspace",
  scheme: "YourScheme",
  output_directory: "xcov_output"
)  
```

# License
This project is licensed under the terms of the MIT license. See the LICENSE file.

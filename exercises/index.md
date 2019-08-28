# Exercises

## How to set up your development environment

iOS development for this course requires a Mac computer running macOS 10.14.4 or higher. If you don't have access to one, you should already have received access to a cloud provider where you can connect to a macOS VM via Remote Desktop.

### For both

- You're going to need a free Apple developer account, which you can create [here](https://developer.apple.com/account/).
- If you want to use the free [SourceTree](https://www.sourcetreeapp.com/) app, which I highly recommend, you'll also need a free Atlassian account, which you can get at [here](https://www.atlassian.com/).

### Using the cloud

- Connect using the instructions and login data you received via email.
- A wired connection (Ethernet, not Wi-Fi) might result in a better experience, due to reduced latency
- You don't need to install anything, everything's already been set up and installed
- **Make sure to log out when you're done by clicking the Apple symbol at the top of the menu bar and selecting `Log Out`. Closing the Remote Desktop window is not enough.**
- Due to cost constraints, there's a 3 hour daily limit on the VM usage. **If you forget to log out, the timer will keep running. Log out while you're not using the VM.**
- Running your apps on a physical device using the cloud is possible, but a bit more complicated than just plugging in the device. If you're interested in doing so, please [contact me](../README.md/#support-or-contact) for help.

### Using your own Mac

- Install the latest stable Xcode version. I recommend installing via [this fairly hidden download page](https://developer.apple.com/download/more/) on the Apple developer site, **not** via the App Store. The App Store version has the disadvantage that it will sometimes automatically update. Since Xcode ships with the latest Swift compiler, iOS SDK, etc., this can sometimes cause your code to break. Downloading and installing directly through the developer site doesn't have this problem. This way you can also install multiple Xcode versions side-by-side.
- Just so you know, downloading and installing Xcode can take a very long time. Do this early enough, so you have enough time to focus on the exercises.
- After installation run Xcode once, since it will install additional components.
- I strongly recommend installing [Homebrew](https://brew.sh/) on your system. It's a package manager that allows you to easily install additional software.
- Make sure [git](https://git-scm.com/) is installed and up-to-date. If you installed Homebrew, you can do so by simply running `brew install git` from your terminal.

## Fixed exercises

These exercises are relatively fixed in their scope and tasks. They're almost like an interactive tutorial, but without the solution ;-)

Since this course is very new, you'll probably run into problems in these exercises. Maybe something isn't specified that should be, or maybe something is missing, or some information is conflicting. Since this will definitely happen, if you're stuck, or feel something is more difficult than it should be, please [contact me](../README.md/#support-or-contact). I'm always happy to help.

- [Swift Exercise](swift-exercise) (Deadline Wednesday, 11 September 2019, 23:55. [Code review](#code-review) session during lecture on Friday, 13 September 2019)
- [Login Exercise](login-exercise) (Deadline Wednesday, 25 September 2019, 23:55, [Code review](#code-review) during lecture on Friday, 27 September 2019)
- [REST Exercise](rest-exercise) (Deadline Thursday, 10 October 2019, 23:55, [Code review](#code-review) session during lecture on Monday, 14 October 2019)
- More fixed exercises will be announced throughout the semester

## [Freeform Exercises](freeform)

You can find all the details on the freeform exercises [here](freeform).

## Submission instructions

- All exercises must be submitted before the deadline [via email](../README.md/#support-or-contact) as a zipped Xcode playground or Xcode project, including all source files.
- You may submit as many times as you like before the deadline. I will only look at your last submission.
- Make sure you understand all the concepts for the [code review session](#code-review) in the lecture after the submission deadline. You'll be graded according to your understanding of the code and the underlying concepts, not the code itself.

## General requirements

- All exercises must build in Xcode version 10.3.x without errors or warnings
- All exercises should run on the latest stable iOS version (currently 12.x).
- Exercises should never crash. Errors should be handled properly, unless explicitly allowed otherwise in the exercise instructions
- Except for the Swift exercise, all the fixed exercises must run without errors in the iOS Simulator. For the freeform exercises you may use iOS capabilities that require a physical device, but the app should still handle these cases gracefully on the simulator (i.e. display an error when such a feature is accessed, not just crash).

## How you are graded

- **Most importantly**: You are graded on your **understanding** of the code, not the code itself. Even the best code isn't worth much if you don't understand the underlying concepts.
- **You need to complete and pass all fixed exercises to receive a passing grade.**
- **You need to complete at least 3 freeform exercises to receive a passing grade.**
- For the fixed exercises, you'll be graded on:
	- Completeness (is everything there that the exercise asked for)
	- Understanding of the main concepts
	- Quality of your code (Don't have unused code laying around. Make sure your code is properly indented. Use proper style conventions for Swift code. Follow the [Swift API Design Guidelines](https://swift.org/documentation/api-design-guidelines/).)
- For the freeform exercises, the above points are still the most important ones. You'll additionally be graded on:
	- Creativity
	- Scope/Number of features. However, be careful, it's much better to have fewer features and have them work really well.
- What you won't be graded on:
	- Visual design. This is mainly a technical course, so visual design isn't super important. As long as UI elements are laid out properly and work on different device sizes, they don't have to look super fancy.
	
## Code review

During the lecture after the submission, we're going to do a short 1-on-1 code review session where you explain the code to me. You'll be graded according to your understanding of the code and the underlying concepts, not the code itself.

## Help and Support

As always, if you need any help or have any questions, feel free to [contact me](../README.md/#support-or-contact). I'm happy to help!

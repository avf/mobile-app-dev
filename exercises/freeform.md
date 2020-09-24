# Freeform Exercises

For the freeform exercises, you can implement your own ideas. Below are [some examples](#ideas-for-inspiration) you may get inspiration from. You shouldn't implement exactly these ideas, they're just to give you an idea of the content and scope these freeform exercises should have.

For each of the freeform exercises, you can either continue with one of the projects from the fixed exercises, or start a new one. You can also combine multiple freeform exercises in the same project, to create one app with multiple cool features.

You need to complete at least two freeform exercises of medium to large scope to receive a passing grade. You can also choose to work on multiple smaller features instead. I recommend that you mainly work on something that you find interesting.

### Important Deadlines

#### Proposals (see [below](#proposals))

- Please submit all [proposals](#proposals) until **Friday, 6 November 2020 23:55**
- Please submit your reviewed, updated and final proposals until **Friday, 20 November 2020 23:55**

#### Freeform exercises

There are two deadlines for freeform exercise submissions:

- Please submit your first batch of freeform exercises until **Friday, 18 December 2020 23:55**
- Please submit your second and final batch of freeform exercises until **Friday, 29 January 2021 23:55**

Since the number and scope of freeform exercises isn't fixed, what exactly you'll have to submit will be a bit different for each student. We'll individually discuss when to submit what during the proposal phase. When writing the proposals, please keep the deadlines in mind and try to get a rough plan of when you're going to submit which features.

## Proposals

For each freeform exercise, you first need to submit a proposal. The proposal should be a short document, for example in a Google Doc or simply in plain text via email.

The proposal should contain a textual description that describes in detail what your new app or feature will do.

Also, include very simple wireframes. They don't need to have any graphical fidelity at all, but it's important that the navigation and user interaction is clear. You can either use a digital tool to create the wireframes, or simply use pen and paper. If you use a digital tool, I recommend [Figma](https://www.figma.com/).

Here is a [sample proposal](sample-proposal) for the [MapKit](#mapkit) idea from below. Take a look to see what I expect from these proposals. It should also give you an idea on the scope of these freeform exercises. Please be aware that you shouldn't just copy the ideas from the sample proposal, but come up with your own.

After you submit your proposals, I'll take a look and will let you know what I think. Sometimes, I may tell you that a proposal needs to be more precise. Sometimes I'll tell you that it's too large or too small in scope. You'll then have time to submit a revision.

### The scope of your project is allowed to change

After your proposal has been accepted, you can start working on it.

Software is notoriously difficult to estimate. You're probably going to run into problems. Things will often take much longer than you expected. I'll try hard to help you catch these things in the proposal phase, but sometimes it won't work.

In these cases, I strongly recommend that you compromise on features, but not quality. It's much better not to implement a feature at all, than having loads of bugs and ugly code.

If you feel like you underestimated something, or you're stuck, [contact me](../README.md/#support-or-contact). I'll try and help you find a solution. 

## Ideas for Inspiration

I've added a difficulty estimation and a support level. Since I'm not equally familiar with all iOS frameworks, I may not be able to help you with everything. Topics with a *High* support level I'm very familiar with, but for topics with a *Low* support level, you may have to figure out more for yourself.

### Complex ViewController Navigation

Download some data from a public API. Create at least five `UIViewControllers` that interact with each other in a complex way. For example, you could use a combination of `UITabBarController`, `UINavigationController`, modal ViewControllers, popovers, embedded ViewControllers, alerts and action sheets to create a complex navigation between multiple screens.

Make sure to fill your ViewControllers with sensible data. For example, you could have a list of cities in a `UITableView`, which navigates to a detail view for a specific city when tapped, and so on. 

You can either use Storyboards or get bonus points for implementing the navigation completely in code.

- **Difficulty**: Easy - Medium
- **Support Level**: High

### Advanced Auto Layout

This works really well with the previous idea. Download some data from a public API. Create a few ViewControllers with a complex, non-trivial Auto Layout UI that displays this data in a sensible and interesting way. For example, you could display two columns of data side-by-side, or have a different UI depending on screen size and orientation. You can either use Storyboards and Interface Builder for this, or get bonus points if you use a third-party framework like [SnapKit](http://snapkit.io/) to lay out your UI completely in code.

- **Difficulty**: Easy - Medium
- **Support Level**: High

### SwiftUI

Instead of implementing the previous idea with UIKit/Auto Layout, you could also use SwiftUI.

- **Difficulty**: Medium
- **Support Level**: Low - Medium

### Animations and Gesture Recognizers

Use `UIKit` animations to create interesting, good looking animations. Add a few custom `UIViews` that are animated. Have your users interact with the views in some way, using `UIGestureRecognizer`.

- **Difficulty**: Easy - Medium
- **Support Level**: High

### MapKit

Download some data from a public API. For example, use the [Vienna Open Data API](https://www.data.gv.at/) to get a list of public locations in Vienna with additional data (like opening times, etc.). Display the locations as pins on a map using `MKMapView`. When tapping a location, show some kind of detail ViewController that displays more info on the location.

Or, use the `CoreLocation` framework to get the user's current location via GPS. Use the `CLGeocoder` framework and a reverse geocoder to get the user's address for the current location. You could then show information about for example restaurants that are nearby.

If you choose this topic, please make sure that it is different enough from the sample proposal.

- **Difficulty**: Medium
- **Support Level**: High

### ARKit

**Requires a physical iOS device. Not recommended when you're using the Cloud VM.**

Download some freely available 3D models and display them in augmented reality using `ARKit` and `SceneKit`. Have the user interact with them in some interesting way.

- **Difficulty**: Medium - High
- **Support Level**: High

### Camera

**Requires a physical iOS device. Not recommended when you're using the Cloud VM.**

Use the iOS camera to do something interesting. For example, you could use it to read in QRCodes, and display the data in an interesting way. Or, if you have access to an iPhone with FaceID, you could read in the facial features of the user and use them to do something interesting.

- **Difficulty**: Medium
- **Support Level**: High

### Publish your App on the App Store

**Requires a physical iOS device. Not recommended when you're using the Cloud VM. Requires a paid developer account which costs 99€/year.**

This is not a very technical challenge, but it does require a lot of work to publish an App on the Store. If you want to do this, you should use something like [fastlane](https://fastlane.tools/) to automate the generation of App screenshots and deployment. Also, you need an App that is sufficiently useful and complex to be accepted into the store, otherwise you won't get through Apple's review.

- **Difficulty**: Low - Medium
- **Support Level**: High

### Database syncing

Create an App that downloads and displays some data from a public API. Store the data in an offline database like `Core Data` or `Realm`. Allow the user to make changes to the data even if the device is offline and then upload/sync it once the device is back online.

- **Difficulty**: Medium - High
- **Support Level**: High (Realm), Medium (Core Data)

### Machine Learning

Use the `CoreML` framework to integrate a machine learning model into your app. You can either use a pre-existing model from the web, or use the [Create ML](https://developer.apple.com/machine-learning/create-ml/) App bundled with Xcode.

- **Difficulty**: Medium - High
- **Support Level**: Low

### Messaging App

Use the [Firebase Mobile SDK](https://firebase.google.com/) to create the serverless backend for a simple chat app. You could use a third-party library like [MessengerKit](https://github.com/steve228uk/MessengerKit) or [Chatto](https://github.com/badoo/Chatto) to implement the UI.

- **Difficulty**: Medium - High
- **Support Level**: High

### Create a third party library

Create a useful third party iOS or Swift library. Publish it using `CocoaPods`, `Carthage` and the `Swift Package Manager`.

- **Difficulty**: Medium
- **Support Level**: High (CocoaPods, Carthage), Low (SPM)

### Create a music player

**Requires a physical iOS device. Not recommended when you're using the Cloud VM.**

Use `MusicKit` to access the music on your device and Apple Music. Create a simple music player UI to play the music.

- **Difficulty**: Medium - High
- **Support Level**: Medium

### Implement In-App Purchases

**Requires a paid developer account which costs 99€/year.**

Implement and test [In-App Purchases](https://developer.apple.com/in-app-purchase/).

- **Difficulty**: Medium - High
- **Support Level**: Low

### Implement Ads

Implement and display paid ads using [Google AdMob](https://developers.google.com/admob/ios/quick-start).

- **Difficulty**: Medium - High
- **Support Level**: Low

### Your own idea

Ever thought of a cool feature for a mobile app? Want to try out any of the frameworks included in iOS, [listed here](https://developer.apple.com/documentation/)? Any other ideas? No problem! Just send in a proposal as [described above](#proposals).

### Ideas that I'm not super excited about

- **Games**: You can implement a game, but only if it uses `UIKit` and Auto Layout. See the idea with [animations and gesture recognizers](#animations-and-gesture-recognizers) above. This could work for simple puzzle games, but for anything with fancy graphics and fast user interaction it will probably be too slow. Since this isn't a class on game development, I don't want you to use any low-level graphics APIs or third party game engines like Unity, etc.
- **Cross-Platform Apps**: Due to resource constraints on my part, I'd prefer you not to work on cross-platform apps. For this class, please stick to iOS and Swift.

## Help and Support

As always, if you need any help or have any questions, feel free to [contact me](../README.md/#support-or-contact). I'm happy to help!

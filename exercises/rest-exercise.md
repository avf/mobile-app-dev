# REST Exercise

In this exercise we'll hook up our login screen from the previous exercise with a real API.

The main goal of this exercise is for you to learn how to query REST APIs using `URLSession`.

## Deadline

See the deadline on the [exercises page](./#fixed-exercises).

## Submission instructions

See the submission instructions on the [exercises page](./#submission-instructions).

## API Key, Username, Password

In this exercise, we're going to use the REST API of the Google Firebase service. Specifically, we're going to use [this endpoint](https://firebase.google.com/docs/reference/rest/auth#section-sign-in-email-password) to sign in with an email/password combo. You shouldn't necessarily have to dig through the docs above to be able to complete this exercise. Everything you need should be in the instructions below, but the above link might still help you understand the inner workings of the API.

When using the API, use the following credentials:

- API Key: `AIzaSyCTryhlVmmRHYE7iQT3k0eeNRHIKsTMpRw`
- Email: `m@m.at`
- Password: `madmad`

Note that I intentionally chose a short email/password combo to make testing easier for you so you don't have to type so much. Since this user account doesn't have access to any important data, security isn't really a concern.

## Instructions, Requirements and Hints

### Setting up the project

- Continue with the Xcode project from the previous exercise

### Setting up the login request

- Create a new Swift file. In this file, create a new class that will handle all the networking
- In your new networking class create a constant `URLSession` and initialize it with the default configuration
- Add a `login` method to your networking class. It should take two parameters: email, password. Later in this exercise, we'll add a third parameter, a `completionHandler` closure, but this is enough to get started.
- Create a `URL` with the following endpoint: `"https://identitytoolkit.googleapis.com/v1/accounts:signInWithPassword?key=API_KEY"`
- Create a `URLRequest` with the above URL.
- Set the `URLRequest's` `httpMethod` to `"POST"`.
- Set the `URLRequest's` http header for `Content-Type` to `application/json`.
- Set the request body. It should be a JSON string in the following format:

```json
{
	"email": "YOUR_EMAIL"
	"password": "YOUR_PASSWORD",
	"returnSecureToken": true
}
``` 

- To get an appropriately formatted JSON string, you need to construct a dictionary of type `[String: Any]`, which contains the above keys and data. Then, use `JSONSerialization.data(withJSONObject: dictionary, options: [])` to serialize the data. Since this method may `throw` an error, for now you can use `try!` to disable error propagation. Later in this exercise we'll properly handle the error.
- Now use the `URLSession` constant you created earlier to create a `URLSessionDataTask` with the `URLRequest` you created. Take a look at [this method](https://developer.apple.com/documentation/foundation/urlsession/1407613-datatask) if you're stuck.
- In the above method's `completionHandler`, print out the three parameters: the `Data`, `URLResponse` and `Error`. You'll have to convert the `Data` object into a `String` first. You can do so by calling `String(data: data, encoding: .utf8)`.
- Call the `resume()` method on your newly created `URLSessionDataTask` to start the request.
- Find a good place to create an instance of your networking class and call your new `login` method. For example, you could call the method from the action that is called when the user presses the login button in the `ViewController`. For testing, you may want to temporarily hardcode your email and password so you don't have to manually re-type it every time you restart the application. 
- Take a look at the console output. If you get a response in the following format, you were successful!

```json
{
  "kind": "identitytoolkit#VerifyPasswordResponse",
  "localId": "CxlvybnrRnSZyDDXN2VS7Fr6ddk1",
  "email": "YOUR_EMAIL",
  "displayName": "",
  "idToken": "VERY_LONG_ID_TOKEN",
  "registered": true,
  "refreshToken": "REFRESH_TOKEN",
  "expiresIn": "3600"
}
```

### Properly parsing the response

- Now that we know our request is working, we want to parse the response properly.
- Create a new Swift file called `User.swift`. In this file, create a new `User` struct.
- Add properties to your `User` type that correspond to the response from the API. Make sure to include `localId`, `email`, `displayName`, `idToken`, `registered`, and `refreshToken`. Make sure the variables are appropriately typed.
- Make your user type conform to the `Codable` protocol. If you've named your properties exactly as they're named in the API response, you shouldn't have to do anything other than adding the protocol to the type's definition. Read [this article](https://developer.apple.com/documentation/foundation/archives_and_serialization/encoding_and_decoding_custom_types) if you're stuck.
- In the `URLSessionDataTask's` `completionHandler`, use a `JSONDecoder` to `decode` the data, using your new `User` type. For now, it's okay to disable error propagation using `try!`.
- Print out your newly created `User` object to see if everything's working.
- If you're having trouble with this part of the exercise, you can refer to [this tutorial](https://learnappmaking.com/urlsession-swift-networking-how-to/).

### Handling errors

- We now can log in and properly parse a returned `User` object. However, so far we haven't handled any of the errors. We should fix that!
- Note, this is arguably the hardest part of this exercise, or at least the most tedious/time consuming.
- We'll ultimately want to provide information to the user what went wrong. To do so, we want to create a new `enum` type, called `NetworkingError`. This new type should conform to the Swift `Error` protocol.
- Make sure the following error cases are handled individually. Add enough enum `cases` so that they cover all the error cases in the following list.
	- An error when serializing the dictionary containing the email and password
	- User entered something that isn't an email address
	-	User entered the wrong email address
	- User entered the correct email address, but the wrong password
	- The network is offline
	- The http response contains data in an unexpected format
	- The http response has an non-successful response code (for example due to an internal server error)
	- Unexpected errors that we didn't think of yet
- For example, try what happens if you enter an invalid email address. The application will probably crash, since we're still using `try!` to parse the user response. This is because the `data` in the `completionHandler` will now contain JSON in the following format:

```
{
  "error": {
    "code": 400,
    "message": "INVALID_EMAIL",
    "errors": [
      {
        "message": "INVALID_EMAIL",
        "domain": "global",
        "reason": "invalid"
      }
    ]
  }
}
```

- To parse this error, create another `struct` type, (maybe name it `ResponseError`) that conforms to `Codable`. This is a bit more difficult to parse than our `User` from above, since it contains nested dictionaries and an array. You're going to have to use custom `CodingKeys` as described in [this article](https://developer.apple.com/documentation/foundation/archives_and_serialization/encoding_and_decoding_custom_types). You may even have to create another type that conforms to `Codable` to parse the nested errors. If you're having difficulties, look at [this StackOverflow post](https://stackoverflow.com/questions/47083639/swift-codable-decode-nested-dictionary) for hints.
- Use `print` to look at the `data`, `response` and `error` in the `completionHandler`. Try some of the other error cases from above to see what happens.
- A hint: if the `error` returned in the `completionHandler` closure is not `nil` (for example in the case of no internet connection), `error` will actually contain an `NSError` instance. You can use a conditional downcast `if let error = error as NSError?` to cast it to an `NSError`. You can then use `errror.localizedDescription` to obtain a nicely formatted `String` that you can later present to the user. You can then use enum [associated values](https://docs.swift.org/swift-book/LanguageGuide/Enumerations.html) to associate this data with your enum cases.
- Make sure that each of the above error cases is handled. For each case, create an appropriate instance of your `NetworkingError` enum. If each case is handled, you're done with this part of the exercise.

### Creating a completion handler and forwarding the user/error

- We can now successfully parse the `User` and handle error cases by creating appropriate `NetworkingError` enum cases. We now want to forward this data asynchronously to the caller of the `login` method.
- To do this, add a `completionHandler` closure to the `login` method parameters. The parameters of the `completionHandler` should be an optional `User?` object and an optional `NetworkingError?` object. Similar to how the `completionHandler` for the `URLSessionDataTask` is implemented. If you're having trouble with the syntax, try CMD-clicking the `dataTask(with request...` method you implemented earlier to jump to its definition. This should give you an idea how it's defined.
- You have to mark the `completionHandler` closure as `@escaping` in its definition. If you don't remember the difference between escaping and non-escaping closures, you can read up again about the difference [here](https://medium.com/@bestiosdevelope/what-do-mean-escaping-and-nonescaping-closures-in-swift-d404d721f39d).
- Now that we have defined the `completionHandler`, it's time to call it from our `login` implementation!
- Make sure to call the `completionHandler` with the `NetworkingError` you created as its parameter from all the error cases described above. The `completionHandler` should only ever be called once in the entire `login` method.
- Since most of the error cases will happen in the `URSessionDataTask` `completionHandler`, we're going to run into a problem. Remember that the `dataTask` is running asynchronously. This means the `dataTask's` completion handler is not called on the main thread, but on a background thread! However, we're not allowed to update the UI from any other thread than the main thread. Since the caller of our `login` method will most likely want to update the UI, we should make sure that our `completionHandler` is instead called from the main thread. You can use the following code snippet to do so:

```
	DispatchQueue.main.async {
			completionHandler(user, nil)
	}
```

- You should now update the place where you call the `login` function to include the `completionHandler`. There, you can check if the `User?` or `NetworkingError?` is present.
- In case of an error, display an appropriate error message, describing the error, using a `UIAlertController` like in the login exercise. You can use a `switch` statement on the `NetworkingError` enum for this to create the error messages.
- In case of success, simply display a success message. We'll further expand upon this in a future exercise.

## Help and Support

As always, if you need any help or have any questions, feel free to [contact me](../README.md/#support-or-contact). I'm happy to help!

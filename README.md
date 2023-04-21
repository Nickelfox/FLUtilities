# FLUtilities

# Usage

To run the example project, clone the repo, and run `pod install` from the Example directory first.

FLUtilities usage is based for dates, device specifications and model name, device token string, strings, UIAlertController, UIColor, UIView and a lot more.

Let's take example of Dates:

```swift
func add(months: Int) -> Date {
	var dateComponents = DateComponents()
	dateComponents.month = months
	let newDate = calendar.date(byAdding: dateComponents, to: self)
	return newDate ?? self
}
```
The above example is used to add to a month(s) to a given month.

```swift
func dayOfWeekFull() -> String? {
	let dateFormatter = DateFormatter()
	dateFormatter.dateFormat = "EEEE"
	return dateFormatter.string(from: self).capitalized
}
```
This method is to be used in case of getting a full name of a specific day, capitalized.

Just like that, you can use other methods to fetch number of months or days from a specific date, add or subtract to a day and month string, short or full.

Another example to be used for class name:

```swift
class func className() -> String {
	let className = (NSStringFromClass(self) as String).components(separatedBy: ".").last! as String
	return className
}
```
This method is used to convert an NSObject class name to string form.

Just like that, for strings:

```swift
public extension String {

	func capitalizingFirstLetter() -> String {
		let first = String(self.prefix(1)).capitalized
		let other = String(self.dropFirst())
		return first + other
	}
	
	mutating func capitalizeFirstLetter() {
		self = self.capitalizingFirstLetter()
	}
	
}
```

The above string based extension is used to capitalize first letter of any string, if used like below:

```swift
var name: String? = "nickelfox"
print(name.capitalizingFirstLetter())
```

Let's try working with UIAlertControllers:

```swift
class func showAlertForMessage(message: String) {
	let okActionInterface = ActionInterface(title: NSLocalizedString("Ok", comment: ""))
		
	UIAlertController.showAlert(
		title: "",
		message: message,
		actionInterfaceList: [okActionInterface])
	{ (interface) in
			
	}
}
	
class func showActionSheet(title: String?, message: String?, actionInterfaceList: [ActionInterface], handler: @escaping AlertHandler) {
	self.showAlertController(
		title: title,
		message: message,
		preferredStyle: .actionSheet,
		actionInterfaceList: actionInterfaceList,
		handler: handler
	)
}
	
class func showAlertController(title: String?, message: String?, preferredStyle: UIAlertController.Style, actionInterfaceList: [ActionInterface], handler: @escaping AlertHandler) {
	let alertController = UIAlertController.alertController(
		title: title,
		message: message,
		preferredStyle: preferredStyle,
		actionInterfaceList: actionInterfaceList,
		handler: handler
	)
	if let topController = UIApplication.topController {
		topController.present(alertController, animated: true, completion: { () -> Void in
		})
	}
}
```
The extension is used to show different types of alerts or action sheet like shared above.

An extension for colors is also present. Below is one example for it's usage :

```swift
var color = UIColor(red: <#T##CGFloat#>, green: <#T##CGFloat#>, blue: <#T##CGFloat#>, alpha: <#T##CGFloat#>)
```
After providing the respective floar values for above arguments, the desired result will be obtained.

## Requirements

## Installation

FLUtilities is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod "FLUtilities", :git => 'https://github.com/Nickelfox/FLUtilities.git'
```

Install using Swift Package Manager:

The [Swift Package Manager](https://swift.org/package-manager) is a tool for automating the distribution of Swift code and is integrated into the swift compiler.

Once you have your Swift package set up, adding FLUtilities as a dependency is as easy as adding it to the ```dependencies``` value of your ```Package.swift```.

```
dependencies: [
    .package(url: "https://github.com/Nickelfox/FLUtilities")
]
```

## Author

Ravindra Soni, soni@nickelfox.com

## License

FLUtilities is available under the MIT license. See the LICENSE file for more info.

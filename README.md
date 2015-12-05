## ColorSlider

`ColorSlider` is a Snapchat-style color picker written in [Swift](https://developer.apple.com/swift/). It supports changing color hue when dragging inside the bounds of the control and modifying color lightness when dragging outside its bounds, allowing you to select black and white.

## Installation

`ColorSlider` is available for installation using [CocoaPods](http://cocoapods.org/). You can install Cocoapods with the following command:

```bash
$ gem install cocoapods
```
Then, specify `ColorSlider` in your `Podfile`:

```ruby
platform :ios, '9.0'
use_frameworks!

pod 'ColorSlider', '~> 1.2.2'
```

Finally, run the following command:

```bash
$ pod install
```

You can also simply copy the `ColorSlider.swift` file into your Xcode project.

## Usage

The sample project `Sketchpad` provides an example of how to integrate `ColorSlider` with Interface Builder, but you can also follow the steps below. `ColorSlider` has several `IBInspectable` appearance properties that you can edit right from Interface Builder, if you choose to go that route.

Create and add an instance of `ColorSlider` to your view hierarchy.

``` Swift
self.colorSlider = ColorSlider()
self.colorSlider.frame = CGRectMake(0, 0, 10, 150)
self.view.addSubview(self.colorSlider)
```


`ColorSlider` is a subclass of `UIControl` and supports the following `UIControlEvents`:
- `.TouchDown`
- `.ValueChanged`
- `.TouchUpInside`
- `.TouchUpOutside`
- `.TouchCancel`

You can get the currently selected color with the `color` property.

``` Swift
self.colorSlider.addTarget(self, action: "changedColor:", forControlEvents: UIControlEvents.ValueChanged)

func changedColor(slider: ColorSlider) {
    var myColor = slider.color
    // ...
}
```


Customize appearance attributes:

``` Swift
self.colorSlider.cornerRadius = 2.0
self.colorSlider.borderWidth = 2.0
self.colorSlider.borderColor = UIColor.whiteColor()
self.colorSlider.shadowOpacity = 1.0
self.colorSlider.shadowColor = UIColor.blackColor()
self.colorSlider.shadowOffset = CGSizeMake(1.0, 1.0)
```


To make it easier to select colors, you can specify `UIEdgeInsets` as padding, in which touch input will still edit the color hue.

``` Swift
self.colorSlider.edgeInsets = UIEdgeInsetsMake(0.0, 44.0, 0.0, 44.0)
```

## Sketchpad

`ColorSlider` comes with a demo project called `Sketchpad` that's a simple drawing app for iPhone. To get it to run in Xcode, use Cocoapods and run `pod install`.

## How it Works

`ColorSlider` uses [HSL](http://en.wikipedia.org/wiki/HSL_and_HSV), defaults to saturation: 100% / lightness: 50%, and allows you to modify the hue by sliding up and down. When you slide your finger outside the bounds (+ padding) of the `ColorSlider`, you can modify the lightness of the color, allowing you to select black and white.

## License

ColorSlider is available under the MIT license, see the [LICENSE](https://github.com/gizmosachin/ColorSlider/blob/master/LICENSE) file for more information.


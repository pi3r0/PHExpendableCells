PHExpandableCells
===================

Library to display cells with min and max height like `UITableView`, it's made with an `UIView` and `UIScrollView`. It works with any kind of cell inside. Many parameters to customize the behaviour like max heigth, min height, if you want to expand all the cells. You do add this view programmatically or directly on your storyboard, using UIView and changind the class. 

`PHEScrollView` works vertically like a natural `UITableView`. 


## Getting Started

- Add `PHEScrollView` file to your project
- Change the type of your UIView with `PHEScrollView` like var ` var myExpendableTV : PHEScrollView` or on the storyboard changing the classe `UIView` with `PHEScrollView`
- Implement the `PHEScrollViewDatasource` datasource on your view controller and implement `numberOfRow(scrollView : PHEScrollView)` inside.
- Implement the `PHEScrollViewDelegate` datasource on your view controller and implement `maxheightForCell(scrollView : PHEScrollView) -> CGFloat`, `minheightForCell(scrollView : PHEScrollView) -> CGFloat` and `expandableScrollView(scrollView : PHEScrollView, cellForRowAtIndex index : NSInteger) -> UIView` inside.
- Implement the `myExpendableTV.reloadData()` to set all cells and build the ScrollView.
- Define your custom cell view and the min/max height and build.

## Customization 

All customize methods are optionals, if you want customization you have to add `PHEScrollViewDelegate` in your view controller.
The `PHEScrollView` have a default values if you want to set different case use the following methods

### expandAll

- Normally all cells can't be expand because the content offset is not too big, by default the library calculate the last cell which can be expanded. If you don't want that behaviour, `return true` and the library add necessary offset to expend all cells.

```swift
func expandAll(scrollView : PHEScrollView) -> Bool {
    return true;
  }
```

### hideVerticalScrollIndicator

- By default the Vertical Scroll Indicator is visible, if you want to hide this, just `return true`. 

```swift
 func hideVerticalScrollIndicator(scrollView: PHEScrollView) -> Bool {
        return true;
    }
```
### backgroundPlaceholderForCellAtIndexPath

- if you want use a placeholder image during the remote image loading, get the local image name. 

```swift
 func backgroundPlaceholderForCellAtIndexPath(indexPath: NSIndexPath) -> NSString {
            return "placeholderImage";
    }
```

## Event and Interaction 

The library add a tap gesture recognizer on every cells, if you want to catch the user interation, you have to to add `PHEScrollViewDelegate` in your view controller and this following method 

### didSelectRowAtIndex


- this event is dispatch when user taps a cell, after the new content Offset setup.
```swift
 func expandableScrollView(scrollView: PHEScrollView, didSelectRowAtIndex index: NSInteger) {
       
        NSLog("User did select this one at index %d", index);
    }
```


## How it Works

It's an `UIView` with inside a `UIScrollView`, it populates the `UIScrollView` with your custom view and add a `tapGestureRecognizer`. Based on the `UIScrollViewDelegate`, every time the user scroll, it's calculate the new frame for the current cell and the next one. 


You can see an full example with the project PHCExpendableCells.

Enjoy...

## License

PHFParallaxBackgroundCell is available under the [MIT license](LICENSE).
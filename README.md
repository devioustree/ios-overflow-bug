# Summary

When using the CSS attribute `-webkit-overflow-scrolling: touch`, Mobile Safari sometimes sends touch events to the wrong DOM elements while the user has initiated inertial scrolling.

# Steps to Reproduce

* Enable debugging for Mobile Safari
* Visit http://devioustree.co.uk/ios-overflow-bug/ in Mobile Safari
* "Throw" the page and, while the document is still scrolling because of inertial scroll, tap one of the blocks.

# Expected Results

This demo registers for the `touchstart` event and prints out the content of the blocks that are tapped.

There could be two entries in the log. One should be the contents of the block that was tapped to start the inertial scroll and the other should be the contents of the block that was tapped in step 3.

* Two
* Seven

# Actual Results

The content of the block that was tapped to start the inertial scroll will be used for both entries.

* Two
* Two

# Regression

Since `-webkit-overflow-scrolling: touch` was only added in iOS 5.0 it does not affect earlier iOS versions.

# Notes

The only workarounds are to either not use touch events (i.e. register for the `click` event) or not to use `-webkit-overflow-scrolling: touch`

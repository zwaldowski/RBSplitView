![Rainer Brockerhoff](http://brockerhoff.net/xrbt.png.pagespeed.ic.GKj9WAW0xz.png)

# RBSplitView version 1.2 — October 24, 2009

## Change Log

### New in 1.2:

- For now, there are two main build groups: (Leo) for 10.5 (Leopard) and (Sno) for 10.6 (Snow Leopard). This may change in the next release.
- As usual, small bug and documentation fixes.
- Support for 64 bits and Garbage Collection.
- New plugin for Leopard's Interface Builder 3.x. RBSplitView 1.2 is for Leopard and up, it must be build with Xcode 3.1 or better. Code may not be backwards-compatible; you'll probably want to use the previous version (1.1.4) for Tiger.
- Dragging a textured window by the background when having nested subviews, not all opaque, now works properly.
- Calling setAutoresizesSubviews: on a RBSplitView or RBSplitSubview now does nothing, to avoid messing up the algorithms.

### New
 in 1.1.4:
- Various small optimizations, bug and documentation fixes.
- The Creative Commons license version was upgraded from 2.0 to 2.5.
- The framework and library are now universal.
- The project is now set up for optimum use with Xcode 2.4. Global build options are now in a .xcconfig file, and all options have been optimized and tweaked. Warnings are now more restrictive and several variable names have been changed to avoid hiding global declarations. Both debug and release versions are now prebuilt, to make it easier to include RBSplitView as a subproject within your project.
- The sample app now shows the recommended way to restore divider settings; the logic to do so is now more robust.
- The sample app now shows how to expand/collapse with animation when double-clicking a divider.
- New -[RBSplitSubview canShrink] and -[RBSplitSubview canExpand] methods.
- If you move a divider and several immediately adjacent subviews in that direction are collapsed or already at their minimum, these will now be pushed aside.
- RBSplitViews should now behave correctly when inside an NSScrollView. There's a new -[RBSplitView isInScrollView] method to check for that.
- The IB palette now shows proper version information.
- Everything now behaves correctly if the RBSplitView and any scrollbar inside it overlap the window's grow box. To make that possible, the -[RBSplitSubview  changeDimensionBy:mayCollapse:] method (which was previously - and incorrectly - documented as having an extra setToMinimum: argument) now has an extra leads: argument.
- Dragging a divider by an auxiliary drag view now works even if that view is inside a nested RBSplitView.
- Dragging a metal window by the background now works correctly; or rather, it now doesn’t drag if you mouse-down on an opaque subview.

### New in 1.1.3:

- Small bug and documentation fixes.
- Fixed a crashing bug when dragging dividers under certain conditions.
- Fixed a bug which happened only when expanding the leading subview and the window simultaneously while the trailing subview had a minimum size which was larger than the distance to the right screen edge and if the name for the current phase of the moon in Egyptian had an odd number of hieroglyphs... well, something like that.
- A new method, -[RBSplitView drawDivider:inRect:betweenView:andView:] is now available for subclassers.
- A new delegate method, splitView:willDrawSubview:inRect: makes it easier to draw a frame inside subviews.

### New in 1.1.2:

- The splitView:changedFrameOf:from:to: delegate method wasn't being called for all subviews when opening a new window; this has been fixed.
- You no longer need to restore RBSplitView state explicitly if you set an autosaveName in Interface Builder, it will be restored automatically.
- Nested RBSplitViews are now restored correctly when calling restoreState:YES, if you have implemented splitView:wasResizedFrom:to: in the delegate.
- Small optimizations here and there, including in the license.

### New in 1.1.1:

- Expanded the documentation and documented some 1.1 methods that had been omitted.
- A new delegate method, splitView:shouldHandleEvent:inDivider:betweenView:andView:, allows the delegate to selectively handle mouse-down events in dividers.; another new delegate method, splitView:cursorRect:forDivider: allows the delegate to selectively change cursor rects for dividers. These should allow you to have more complex dividers.
- A new delegate method, splitView:shouldResizeWindowForDivider:betweenView:andView:willGrow:, allows the delegate to decide whether, while a divider is being dragged, it should resize the trailing subview or the containing window.
- The parameters passed to the splitView:changedFrameOf:from:to: delegate method are now more reliable, and the method is called only when the frame actually changes.
- The splitView:dividerForPoint: delegate method gained an extra parameter, the signature is now splitView:dividerForPoint:inSubview:. See the sample app for an example.
- A new -[RBSplitView isDragging] method allows you to check if a divider is being dragged, or if an animation is in progress. You could use this to postpone complex view updates.
- Fixed a bug where the actual divider count didn’t take hidden subviews into account.
- Fixed a bug in -[RBSplitView adjustSubviewsExcepting:] where the excepted subview was incorrectly collapsed.
- Adjusting subviews should now give more consistent results in unfavorable circumstances.
- Reduced flicker for complex subviews during divider dragging.
- The RBSplitView state was being saved continuously while dragging a divider or animating a subview, now it’s saved only after concluding the action. This should be faster for complex nested views.
- You now can select both 8x8 and 9x9 pixels as divider images in Interface Builder, and the previous 8x8 image has been sharpened to be more similar to the 9x9 image, which is the same used by NSSplitView. You must re-select the 8x8 divider in IB for all your RBSplitViews to get the new image.
- Restored a disclaimer in the licensing terms which was inadvertently removed in 1.1.

### New in 1.1:

- Revised and expanded the documentation.
- Project files have been reorganized into folders.
- Reorganized target dependencies to reduce bundle sizes and download size.
- A new pair of RBSplitView methods, arrayWithStates and restoreStatesFromArray:, allows you to take a snapshot of a view’s state (including nested subviews) and restore it later.
- You can now globally alter the cursors used by calling +[RBSplitView setCursor:toCursor:].
- A new delegate method, splitView:dividerForPoint:, makes it possible to implement alternate drag views (like the dragging tab in Tiger Mail). See the sample app for an example.
- A new delegate method, splitView:changedFrameOf:from:to:, makes it easier to keep auxiliary views aligned with certain RBSplitSubviews. See the sample app for an example.
- There are two new delegate methods, willAdjustSubviews: and didAdjustSubviews:, which unsurprisingly are called just before and after adjusting subviews.
- A new -[RBSplitView addSubview:atPosition:] method makes it easier to insert subviews.
- You can now hide and unhide RBSplitSubviews. Hiding a subview makes it vanish as far as redrawing is considered. This is different from collapsing in that one of the adjacent dividers also vanishes, and no delegate methods are called. Hiding is not available from the Interface Builder inspector though. See the sample app for an example.
- If a RBSplitSubview is collapsed while one of its subviews is the current first responder, it will now try to set the first responder to nil. This will avoid leaking focus rings outside the RBSplitView.
- A RBSplitView nested inside another as the single subview is now adjusted correctly.
- Nested RBSplitViews will now also inform the delegate of a size change; previously, only the outer RBSplitView would do that.
- A crashing bug in nib files saved in pre-10.2 format has been fixed.
- There are new methods to collapse/expand subviews with animation while keeping their contents static.
- All changes to RBSplitViews and RBSplitSubviews in Interface Builder are now undoable.
- Tabbing to the next key view in the Interface Builder inspectors now works correctly for all fields.
- There's a new option to set a transparent, 1x1 pixel divider image in Interface Builder.
- RBSplitSubview, RBSplitView and their outlets and actions are now shown correctly in Interface Builder’s class outline view.
- Fixed a bug where the dimension could be incorrectly displayed for horizontal RBSplitViews in Interface Builder.
- You can now set the identifier for non-nested RBSplitView in the Interface Builder palette; this may help with debugging.
- There are new “Current” buttons in the RBSplitSubview inspector panel, to set minimum or maximum dimensions to the current dimension.
- Prebinding is no longer turned off for the framework, so you can now use it with both prebound and non-prebound applications without getting a warning.
- The license is now changed from a modified BSD license to the equivalent Creative Commons Attribution License, Version 2.0. Makes little or no difference in practice but I get to display the cool CC logo ;-).

### New in 1.0.4:

- Version numbers in source files are again correct; I forgot to bump them for 1.0.3.
- You can now collapse and expand subviews with animation, although only a single subview may be animated at a time. There are several new RBSplitSubview and RBSplitView methods, mostly related to this, and a new RBSplitView delegate method.
- The SampleApp now demonstrates animation and some of the subviews were tweaked to test or demonstrate more features.
- Fixed a bug in the IBPalette where clicking “Adjust enclosed view” and some other actions could mangle nested enclosed views. This bug and several others fixed in previous versions may have mangled your nib file. Check out already saved nib files: switch to outline mode and see if there are any spurious subviews (like NSCornerViews) or incorrect sizes. You may have to completely redo the subviews in such a case; sorry for the mix-up.
- Fixed a bug in -[RBSplitView adjustSubviews] which could resize subviews inaccurately under rare circumstances.
- In the IBPalette, clicking “Adjust enclosed view” is now undoable.
- In the IBPalette, dragging a RBSplitView divider is now undoable, marks the document as changed, and subviews should now be properly resized when doing so.
- Both RBSplitViews and RBSplitSubviews now include more information in their - description methods, to make debugging easier.
- Documentation and source code comments have been revised and updated.

### New in 1.0.3:

- The IBPalette now appears to work correctly in the Tiger betas, some visual glitches excepted. I’m still working on this whenever possible.
- The -[RBSplitSubview setDimension:] method now works correctly.
- RBSplitSubview dimensions are now more carefully controlled when collapsing and expanding, even in nested RBSplitViews.
- Collapsing and expanding RBSplitSubviews with equal maximum and minimum dimensions now doesn’t mess up contained views.
- Encoding a RBSplitView with a collapsed subview now works correctly.

### New in 1.0.2:

- The RBSplitView inspector palette now has a drop-down menu to manipulate the divider image. You can clear it entirely, use the default thumb, or paste in any image from the clipboard.
- The RBSplitView inspector palette now has a “Use image dim.” checkbox to use the divider image dimensions for the divider thickness.
- The RBSplitSubview inspector palette now has a “Adjust enclosed view” button that will adjust the enclosed view (if there’s just one) to cover the RBSplitSubview, and also set the resizing springs accordingly. You’ll want to use this immediately after dropping a NSTextView in, for instance.
- The RBSplitSubview size inspector palette now has a “Collapse” check box that allows you to collapse or expand the subview.
- Clearing the divider image (or calling setDivider:nil) will make the RBSplitView stop responding to mouse events, that is, the splits will be able to be adjusted only programmatically. This may be convenient if you want the subviews to always maintain their relative size, for instance. You‘ll still be able to drag the divider in IB, however.
- Setting the divider thickness to zero now means that the divider image’s dimensions should be used. Setting any positive value will use that value, even if the divider image is larger than that, in which case the results may not be what you wanted.
- There is a new -[RBSplitView adjustSubviewsExcepting:] method, to allow keeping one subview static while resizing.
- There is a new -[RBSplitSubview isSplitViewHorizontal] convenience method.
- Fixed a bug where the IBPalette was mangling NSTabViews (and perhaps other complex views) contained inside RBSplitSubviews when reopening a nib file.
- The way RBSplitSubviews were collapsed has been changed completely; before, they were moved completely off the visible part of the RBSplitView; now, they’re actually collapsed to zero dimension, but the subview resizing mechanism is disabled while they’re smaller than the minimum dimension.
- The -[RBSplitSubview description] method now shows the view’s identifier if present, to make debugging easier.
- Several small potential bugs have been fixed.
- The limit case of having only a single RBSplitSubview now works, and the IB palette will allow you to generate such a RBSplitView. The single subview will always occupy the entire RBSplitView and can’t be collapsed. It also won’t obey the dimension limits.

If you already have a project built with older versions, you must open your nib files that contain RBSplitViews, set the divider thickness or click on “Use image dim.”, and resave them.

### New in 1.0.1:

- Several redrawing bugs were fixed, and in most cases adjustSubviews doesn’t need to be called explicitly anymore.
- The - collapse method no longer has a parameter, and collapsing/expanding subviews programmatically now always returns the subview to its former size. If the RBSplitView has changed size while the subview was collapsed, the subview will expand to occupy the same proportion it occupied before.
- The - dimension method now has a different behavior when called for collapsed subviews. Formerly it returned 0.0, now it returns the dimension the subview would normally have when expanded.
- Nested RBSplitViews now can be uncoupled from each other, suppressing the two-axis thumb and allowing different backgrounds and thumb images to be used. The IB palette has been redesigned accordingly.

If you already have a project built with version 1.0, it's advisable to open your nib files that contain RBSplitViews, toggle the “coupled” box twice, and resave them. Also be sure to check all calls to - collapse and remove the parameter.

### New in 1.0:

This was the first public release. If you had previously downloaded one of the beta releases, these were the main fixes:
- Several small bugs have been fixed, in both the source code and the documentation.
- Previously, only RBSplitSubviews could be programmatically added to RBSplitViews. Now, a containing RBSplitSubview is automatically created and the added view has its frame and resizing mask set to always occupy the entire “split”.
- Previously, a minimum size was forced if you created RBSplitViews programmatically. This is no longer done, but creating RBSplitViews with too-small frames will still give unreliable results.

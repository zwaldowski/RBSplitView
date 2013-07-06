![Rainer Brockerhoff](http://brockerhoff.net/xrbt.png.pagespeed.ic.GKj9WAW0xz.png)

# RBSplitView version 1.2 — October 24, 2009

## What is RBSplitView?

It's a replacement for NSSplitView. There are some serious limitations with NSSplitView if you need to limit subview's sizes, expand or collapse subviews programmatically or by double-clicking, or resize the split view frequently. IMHO the general design and the delegate calls of NSSplitView, a legacy from NeXTstep, are at the root of these problems; it has improved with Leopard, but it's still not ideal. So RBSplitView is *not* a drop-in replacement for NSSplitView, although some methods are similar.

RBSplitView has special content views — RBSplitSubviews — that handle details of subview limitations and properties. So there's less or no work to be done by the delegate. RBSplitView also has built-in support for nesting any number of levels, and automatically generates a two-axis thumb to resize in two dimensions.

The IB palette for RBSplitView isn't the best, as many details of writing palettes for container views aren't properly documented... still, it mostly works and gets a little better with each release. Be especially careful with Undo, Copy, and Paste. I recommend *always* working in outline view. This will change in Leopard, with the new Interface Builder, at the cost of backwards compatibility...

You can use RBSplitView’s object or source code in any form for no fee provided some conditions are met; see details at the end of this document.

This version of RBSplitView is for Snow Leopard (10.6) and up, to be compiled with Xcode 4 and up. It works with 32-bit or 64-bit Intel under Automatic Reference Counting (ARC).

Thanks to Dan Wood, Steve Gehrman, Brad Miller, Mike Ash, Chris Pavicich, Chris Silverberg, Peter N. Lewis, Mirko Viviani and several others for helping with debugging, making lots of excellent feature requests and/or submitting bug fixes! The growing list of adopters can be seen at http://www.brockerhoff.net/src/rbs.html. Be sure to e-mail me when you adopt RBSplitView, and I'll include you.

----

## How to use:

- If you have used an older version before, run IB, go to the Tool->Palette->Palette Preferences window, and Remove the previous RBSplitView palette. Then quit IB.
- Rebuild (if you have changed anything).
- The **recommended** way:
	- Include the entire RBSplitView project as a subproject in your own project
	- Add the RBSplitView’s project “source” folder to your user headers search path.
- If your compiler options are non-standard, or if you don't want to use the prebuilt library, you can also:
	- copy the RBSplitView/RBSplitSubview.h and .m files, as well as the RBSplitViewPrivateDefines.h file, into your project.
- Alternatively, you could also:
	- copy the prebuilt libRBSplitView.a static library into your project (be sure to use the Release version), as well as the RBSplitView/RBSplitSubview.h files, or
	- copy the prebuilt RBSplitView.framework framework into your project (only if you really like frameworks; I don‘t). The framework is meant to be included within applications or within the IB plugin, it’s not set up to work in the standard /Frameworks folders.
- Double-click on the RBSplitView.palette item in “Products” (this will let IB know about the palette). Alternatively, you can copy it to ~/Library/Palettes.
- **Read the documentation!** Then read it again! All three of them; reading the comments in the header files is also recommended.
- Check out the Sample App code and nib file.
- Ask me if you don't understand something :-). My AIM is rainerbrockerhoff@mac.com. My e-mail is rainer@brockerhoff.net. There's also a support forum on my website: http://www.brockerhoff.net/bb/viewforum.php?f=9.
- Please report all bugs promptly; see my contact info above. If I don’t know about it, I can't fix it. Don’t hesitate to send in suggestions.
- If you thought it necessary to subclass RBSplitView, or to change anything in the source, please tell me why. So far nobody I know has needed to subclass.

----

## Tips, tricks and FAQs:

- Look at the end of the “Programming Topics” file! All these items have been moved there. You should read that section even if you think you don‘t need it.

----

## Legal Mumbo-Jumbo:
RBSplitView is Copyright © 2004-2009 by Rainer Brockerhoff. Some rights reserved as described below. Check http://www.brockerhoff.net/ for similar items and other products, papers and whatnot by Rainer Brockerhoff.

You may choose whichever of the licensed below you deem more appropriate for your specific case.

This work is licensed under the Creative Commons Attribution License, version 2.5. To view a copy of the Creative Commons Attribution License, version 2.5, visit http://creativecommons.org/licenses/by/2.5/ or send a letter to Creative Commons, 543 Howard Street, 5th Floor, San Francisco, CA 94105-3013, USA.
This is a summary of the Legal Code (the full license) for your convenience, but is not itself a legal document. You are free:
- to copy, distribute, display, and execute the work, either in source or binary form
- to make derivative works
- to make commercial use of the work
Under the following conditions:
- Attribution. You must give the original author credit in some place where the end user can see it.
- For any reuse or distribution, you must make clear to others the license terms of this work.
- Any of these conditions can be waived if you get permission from the copyright holder.
- Your fair use and other rights are in no way affected by the above.

In addition, RBSplitView is also licensed under the MIT license, approved by the Open Source Initiative.
Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
RBSplitView is provided "AS IS", without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose and noninfringement. In no event shall the authors or copyright holders be liable for any claim, damages or other liability, whether in an action of contract, tort or otherwise, arising from, out of or in connection with the software or the use or other dealings in the software.
To comply with any of these licenses, I suggest that published products — be they commercial, “shareware” or freeware — should, somewhere in the “About Box” or its equivalent, say “RBSplitView by Rainer Brockerhoff”, with a link to http://www.brockerhoff.net/ if possible. A copy of the software itself would also be appreciated, and/or an e-mail telling me where you used it. If you make a significant modification to the source code, or find some bug, please e-mail me at <rainer@brockerhoff.net>.

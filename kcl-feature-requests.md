# KCL Feature Requests

I may be doing a bunch of this wrong, and in any of those cases would love to be corrected (kindly).

* I realize its a large change, but would love static typing in the language, or at least type hints in the VScode plugin
* The VScode plugin constantly crashes for me, ends up that I can't save a file change because the LSP crashes. I end up just disabling the LSP in order to save the file
* I wish there were custom types I could declare for function signatures so I could pass around functions that fit a certain signature. I'd like to know that a function can be passed around
	* Without control flow, the code ends up looking very functional to do anything reusable. Without custom types/method signatures, this makes it really difficult to reason about when looking at a piece of code that accepts 5 functions as arguments:
		```kcl
		fn generateEdgeCornerCurves(startPointOffsetFunc, rotationFunc, pointFunc, segment) {
			segmentStart = segment * 3
			startPoint0 = rotationFunc(  pointFunc(cornerCurvePoints), 0, segmentStart)
			startPoint = startPointOffsetFunc(startPoint0)
			sweepPath = startSketchOn(offsetPlane(XY, offset = bodyThickness))
				|> startProfileAt(startPoint, %)
				|> generateBezierCurve(pointFunc(cornerCurvePoints), rotationFunc, segmentStart, %)
			return edgeCurves(pointFunc(moreEdgePoints), startPoint[0], bodyThickness, -startPoint[1])
				|> sweep(path = sweepPath)
		}
		```
* Relatively minor, but I wish I could do multi-variable assignment in a single line.
	Today, I have to do something like the following
	```kcl
	fn myFunc(xy) {
		x = xy[0]
		y = xy[1]
		// do something
		return someResponse
	}
	```
	Instead, I'd much prefer something like
	```kcl
	// not valid, just for example
	fn myFunc(xy) {
		x, y = xy[0], xy[1]
		// do stuff
		return someResponse
	}
	```
* I really wish I could do matrix math on a list of lists.



## Great stuff

* I _love_ that I can return functions from a function:
	```kcl
	fn spOffsetFunc(x, y){
		return fn(xy) {
			return [x+xy[0], y+xy[1]]
		}
	}
	```



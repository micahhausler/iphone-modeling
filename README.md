# iPhone case modeling

I wanted an excuse to learn KCL better, I like the idea of reproducable 3D modeling, and have wanted to design an 3D-printable iPhone mount for my car. Before building the mount, I wanted to practice modeling the iPhone itself.

This repository builds a 3D model of an iPhone 16 Pro using [Zoo.dev](https://zoo.dev/)'s [Modeling app](https://zoo.dev/modeling-app) in [KCL](https://zoo.dev/docs/kcl).

[![iPhone 16 Pro Preview](./img/model.png)](./export/iPhone16Pro-bin.stl)

## Model Development

- [x] Interpoalte additional corner curve points for Bezier curves.
			(2 additional curve control points to create smooth bezier curves)
- [x] compose main body shape with corners and extrude
- [x] Interpoalte additional edge curve points for Bezier curves.
			(2 additional curve control points to create smooth bezier curves)
- [x] Sweep edge curves along corner along each corner's 6 bezier curve segments. (And duplicate/rotate for corners on top and bottom)
- [x] Extrude edge curve along sides/top/bottom (and back 4 edges)
- [x] Create center body/back rectangle (width - 2 * corner curve radius) x (length - 2 * corner curve radius) and extrude
- [x] Create camera bumpout
- [x] increase size of middle sketch to Camera Plateau `loft()` to get a smoother curve
- [x] Create power/volume/action buttons
- [x] `hole()` for USB-C port
- [ ] `hole()` speaker holes

**Code Cleanup**
- [x] clean up x/y/z translation of corners/edges
- [x] ~~Fillet edge and corner curves?~~ Simpler, but not as accurate on corner curves
- [x] Figure out how to remove sweep paths for corner/edge volumes after use. (After the sweep I ended up making the path into a solid and calling `rotate()` on it too. Its kind of a hack but the solid hides inside the phone body)
- [ ] Create module for common function
- [ ] Migrate python curve interpolation to KCL

## License

Apache 2.0

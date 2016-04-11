## TypeScript

### Why TypeScript

There are two main goals of TypeScript:

- Provide an optional type system for JavaScript.
- Provide planned features from future JavaScript editions to current JavaScript engines

sample.js (JavaScript)

```
let foo = 123;
```

sample.ts (TypeScript)

```
let foo: number = 123
```

Types increase your agility when doing refactoring. Its better for the __compiler to catch errors__ than to have things __fail at runtime__.

### Types are structural

```
interface Point2D {
  x: number;
  y: number;
}
interface Point3D {
  x: number;
  y: number;
  z: number;
}

var point2D: Point2D = { x: 0, y: 10, }
var point3D: Point3D = { x: 0, y: 10, z: 20 }
function iTakePoint2D(point: Point2D) { /* do something */ }

iTakePoint2D(point2D); // exact match okay
iTakePoint2D(point3D); // extra information okay
iTakePoint2D({ x: 0 }); // Error: missing information `y`
```

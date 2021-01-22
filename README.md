# Algolab cheatsheet

## Useful std::

## Boost Union Find

## CGal Geometry

## CGal Triangulation

### Fin the closest vertex 
```cpp
auto nv = t.nearest_vertex(p);
```

### Find the Triangle a point is in
```cpp
auto face = t.locate(p);  // @roman what happens on the border of two triangles
if (face == nullptr) {
  // p is not in convex hull.
}
```

## CGal LPs

### Rounding
```cpp
Solution sol = CGAL::solve_linear_program(lp, ET());
cout << (long)std::ceil(CGAL::to_double(sol.objective_value())) << endl;
```

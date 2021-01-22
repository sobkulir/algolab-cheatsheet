# Algolab cheatsheet
Lukas also sent me their old doc: https://docs.google.com/document/d/1yAtgKC3Jsnj1a_tlWmjD3qIjL2X12t3sMUMLgi-LHvw
## Useful std::

## Boost Union Find

```cpp
boost::disjoint_sets_with_storage<> uf(n);
std::size_t a, b;
std::size_t c1 = uf.find_set(a);
std::size_t c1 = uf.find_set(b);
uf.link(c1, c2);

```

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

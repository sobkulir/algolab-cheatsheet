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

## Boost Graphs 

```cpp
// Remove Edge
boost::remove_edge(boost::edge(i,j,g).first, g);
```

## CGal Geometry


### Binary Search SQRT-Root
```cpp
auto radius = c.squared_radius();
decltype(radius) l(0), r(radius+1);
while(r - l > 0.1) {
  auto mid = (r+l)/2;
  if(mid * mid >= radius) 
    r = mid;
  else 
  l = mid;
}

long out = floor_to_double(l);
while (K::FT(out) * K::FT(out) < radius) ++out;
```

### Geometry Operations

```cpp
typedef CGAL::Exact_predicates_inexact_constructions_kernel IK;
typedef CGAL::Exact_predicates_exact_constructions_kernel EK;

// Orientaion (no construction needed)
bool is_r_left = CGAL::left_turn(p, q, r);
auto ori = CGAL::orientation(p, q, r);
// ori can be:
// CGAL::COLLINEAR | CGAL::LEFT_TURN | CGAL::RIGHT_TURN


EK::Circle_2 c(ep, eq, er);
c.has_on_boundary(ep);

// Min circle
typedef CGAL::Min_circle_2_traits_2<EK> Traits;
typedef CGAL::Min_circle_2<Traits> Min_circle;
Min_circle mc(P.begin(), P.end(), true);
Traits::Circle c = mc.circle();
std::cout << c.center() << " " << c.squared_radius() << "\n";

// Intersections
if (CGAL::do_intersect(s[i],s[j])) {
 auto o = CGAL::intersection(s[i],s[j]);
 if (const P* op = boost::get<P>(&*o))
  std::cout << "point: " << *op << "\n";
 else if (const S* os = boost::get<S>(&*o))
  std::cout << "segment: " << os->source() << " "
            << os->target() << "\n";
 else // how could this be? -> error
  throw std::runtime_error("strange segment intersection");
 } else
  std::cout << "no intersection\n";


```

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

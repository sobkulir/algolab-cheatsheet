# Algolab cheatsheet

## Useful std::

## Boost Union Find

## CGal Geometry

## CGal Triangulation

## CGal LPs

### Rounding
```cpp
Solution sol = CGAL::solve_linear_program(lp, ET());
cout << (long)std::ceil(CGAL::to_double(sol.objective_value())) << endl;
```

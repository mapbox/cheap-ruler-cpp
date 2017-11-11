# cheap-ruler-cpp

Port to C++ of [Cheap Ruler](https://github.com/mapbox/cheap-ruler), a collection of very fast approximations to common geodesic measurements.

# Usage

Using namespace `cr`
```
namespace cr = mapbox::cheap_ruler;
```

All `point`, `line_string`, `polygon`, and `box` references are mapbox::geometry data structures.

## Create a ruler object

**CheapRuler(double latitude, Unit unit)**

Creates a ruler object that will approximate measurements around the given latitude with an optional distance unit.

```cpp
auto ruler = cr::CheapRuler(32.8351);
auto milesRuler = cr::CheapRuler(32.8351, cr::CheapRuler::Miles);
```

Possible units:

* `cheap_ruler::CheapRuler::Unit`
* `cheap_ruler::CheapRuler::Kilometers`
* `cheap_ruler::CheapRuler::Miles`
* `cheap_ruler::CheapRuler::NauticalMiles`
* `cheap_ruler::CheapRuler::Meters`
* `cheap_ruler::CheapRuler::Yards`
* `cheap_ruler::CheapRuler::Feet`
* `cheap_ruler::CheapRuler::Inches`

**CheapRuler::fromTile(uint32_t y, uint32_t z)**

Creates a ruler object from tile coordinates (`y` and `z` integers). Convenient in tile-reduce scripts.

```cpp
auto ruler = cr::CheapRuler::fromTile(11041, 15);
```

## Methods

**distance(point a, point b)**

Given two points of the form [x = longitude, y = latitude], returns the distance (`double`).

```cpp
auto distance = ruler.distance(point_a, point_b);
std::clog << distance; // 4.503
```

**bearing(point a, point b)**

Returns the bearing (`double`) between two points in angles.

```cpp
```

**destination(point origin, double distance, double bearing)**

Returns a new point (`point`) given distance and bearing from the starting point.

```cpp
```

**offset(point origin, double dx, double dy)**

Returns a new point (`point`) given easting and northing offsets from the starting point.

```cpp
```

**lineDistance(const line_string& points)**

Given a line (an array of points), returns the total line distance (`double`).

```cpp
```

**area(polygon poly)**

Given a polygon (an array of rings, where each ring is an array of points), returns the area (`double`).

```cpp
```

**along(const line_string& line, double distance)**

Returns the point (`point`) at a specified distance along the line.

```cpp
```

**pointOnLine(const line_string& line, point p)**

Returns a pair of the form `std::pair<point, unsigned>` where point is closest point on the line from the given point and index is the start index of the segment with the closest point.

```cpp
```

**lineSlice(point start, point stop, const line_string& line)**

Returns a part of the given line (`line_string`) between the start and the stop points (or their closest points on the line).

```cpp
```

**lineSliceAlong(double start, double stop, const line_string& line)**

Returns a part of the given line (`line_string`) between the start and the stop points indicated by distance along the line.

```cpp
```

**bufferPoint(point p, double buffer)**

Given a point, returns a bounding box object ([w, s, e, n]) created from the given point buffered by a given distance.

```cpp
```

**bufferBBox(box bbox, double buffer)**

Given a bounding box, returns the box buffered by a given distance.

```cpp
```

**insideBBox(point p, box bbox)**

Returns true if the given point is inside in the given bounding box, otherwise false.

```cpp
```




[![Build Status](https://travis-ci.org/mapbox/cheap-ruler-cpp.svg?branch=master)](https://travis-ci.org/mapbox/cheap-ruler-cpp)

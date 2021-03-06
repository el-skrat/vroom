# Changelog

## [Unreleased]

### Changed

- Update `clang-format` to 6.0 for automatic code formatting (#143)
- Speed up TSP solving by over 35% on all TSPLIB instances (#142)
- Speed up CVRP solving by over 65% on all CVRPLIB instances (#146)

## [v1.2.0]

### Added

- Support for multiple vehicles
- Support for multi-dimensional capacity constraints (#74)
- Support for skills to model jobs/vehicles compatibility (#90)
- Support for user-defined matrices (#47)
- New flag `-x` to set the trade-off between computing time and exploration depth (#131)
- Provide ETA at step level in the routes, using optional service time for each job (#101, #103)
- Experimental* support to use `vroom` directly from C++ as a library (#42)
- Automatic code formatting script based on `clang-format` (#66)
- PR template

*: read "functional with no C++ API stability guarantee"

### Changed

- Update `rapidjson` to a patched `v1.1.0` (#128)
- Improve dependency handling (#78)
- Improve compilation time and switch from relative to absolute paths for includes (#108)
- Various refactors (#64, #72, #88, #106)

### Removed

- Drop Boost.Log dependency (#130)

### Fixed

- Memory leak upon `vrp` destruction (#69)
- Prevent overflows with huge costs (#50)
- Infinite loop on TSP edge case (#122)
- Various build warnings and errors with both `gcc` and `clang` (#94, #114)

## [v1.1.0]

### Added

- Support `libosrm` as of v5.4 for faster `table` and `route` queries
  (#34)
- Add contributing guidelines (#56)
- Compile also with `-std=c++11`, useful in some environments (#55)

### Changed

- Internals refactor setting up a scalable data model for future
  features (#44)
- Renamed solution indicators key in json output `solution`->`summary`
- Global cleanup with regard to coding standard (#56)

### Removed

- Drop support for TSPLIB files (#48)
- Clean unused code and heuristics

## [v1.0.0]

### Added

- Support for OSRM v5.*
- Dedicated folder for API documentation

### Changed

- New input and output json API (#30)
- Switch to [lon, lat] for all coordinates (#33)

### Removed

- Drop support for OSRM v4.*
- Flags `-s` and `-e` (see new API)

### Fixed

- Compilation trouble with rapidjson and some types (#31)
- Correct usage display obtained with `-h` (#39)

## [v0.3.1]

### Changed

- Switch to BSD 2-clause license.
- Solving TSPLIB instances does not require the `-t` flag anymore.
- Several components of the local search code can now use
  multi-threading (#26).

### Fixed

- Improve 2-opt operator for symmetric cases (#27).

## [v0.3]

### Added

- Compute optimized "open" trips with user-defined start and/or end.
- Special extra handling for asymmetric problems in the local search
  phase.
- New local search operator to improve results in specific asymmetric
  context (e.g. many locations in a dense urban area with lots of
  one-way streets).
- OSRM v4.9.* compatibility.
- Use rapidjson for json i/o (#19)
- Append the `tour` key to the solution in any case.

### Changed

- U-turns enabled when retrieving detailed route geometry from OSRM
  (#10).
- Evolution of the local-search strategy providing lower dispersion in
  solution quality and improving on worst-case solutions (overall
  worst-case on TSPLIB went from +9.56% over the optimal in v0.2 to
  +6.57% in this release).
- Core refactor for undirected graph (#13), tsp structure and tsplib
  loader (#24), heuristics, local search and 2-opt
  implementation. Results in a less intensive memory usage and faster
  computing times (on TSPLIB files, the computing times dropped by
  more than a factor of 2 on average).
- Cleanup verbose output, using Boost.Log for better display (#18).
- Switch to boost::regex for input parsing.

### Fixed

- Wrong output tour size for problems with 2 locations (#16).
- Segfault with explicit matrix in TSPLIB format (#14).
- Invalid syntax for newline at the end of input file (#17).
- Trouble with the regexes used for TSPLIB parsing (#7).
- Incorrect DIMENSION key in TSPLIB format raising stoul exception.
- Segfault for DIMENSION: 1 problem in TSPLIB format (#25).

## [v0.2]

### Added

- New loader to handle TSPLIB format, providing support for
  user-defined matrices (#2).
- Dependency on boost.

### Changed

- Switch to boost.asio for http queries handling.
- Simplified matrix implementation.
- Use of -std=c++14 flag.

### Fixed

- Socket reading issues (#1).
- Potentially incorrect request for route summary (#5).

## [v0.1]

### Added

- Solving problems with one vehicle visiting several places a.k.a
  [travelling salesman problem](https://en.wikipedia.org/wiki/Travelling_salesman_problem).
- Support matrix computation using [OSRM](http://project-osrm.org/).
- Solution output to `json` with location ordering, cost of the
  solution and execution details.
- Optional ready-to-use detailed route.
- Optional use of euclidean distance for matrix computation.


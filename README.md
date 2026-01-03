
<!-- README.md is generated from README.Rmd. Please edit that file -->

# streamnetwork

<!-- badges: start -->

<!-- badges: end -->

`streamnetwork` will be an R package to create, manipulate, query and
plot stream networks.

## Design

- A streamnetwork is an object of S3 class `streamnetwork`.

- Functions have the prefix `sn_`.

- At a minimum it consists of a single tibble called `stream`

  Columns

  - stream_id (unique integer)
  - stream_name (unique character)
  - stream_length (double of the stream length in m)
  - parent_id (integer of stream into which it flows - NA for roots and
    disconnected streams)
  - parent_p (double of proportion between 0 and 1 of way up parent
    stream that confluence)

  Option Columns

  - geometry (sfc_LINESTRING)
  - child_id (integer of stream from which it start - defined for side
    channels)
  - child_p (double of proportion between 0 and 1 of way up parent
    stream)
  - start_year (integer) to allow for changes at freshet in any given
    year (child streams will also have to have their parent_p updated)
  - ds_elevation
  - gradient
  - sinuosity
  - other columns are preserved and can be used to filter etc

  Notes

  - The stream distance in m can be obtained by multiplying the xx_p by
    the stream_length.
  - Streams with sections that are temporarily or permanently dry or
    that flow through lakes should be included for calculation of stream
    measures but coded as such in the section table.
  - There must be no cycles!

Points Points on the stream network are stored as one or more tibbles
with

Columns - stream_id (must join to stream stream_id) - point_p (double of
proportion between 0 and 1)

Optional Columns - geometry (sfc_POINT) - distance_to_stream - other
columns are preserved - points can have same point_p

Notes - Must have same projection of streams tibble.

Segment Segments (often reaches) are touching sections of a stream

Columns - stream_id - us_p (upstream break)

Optional Columns - geometry (sfc_POINT) - distance_to_stream - other
columns are preserved

Section Sections are discrete potentially non-overlapping chunks of a
stream Columns - stream_id - ds_p (upstream break) - us_p (upstream
break)

Optional Columns - ds_geometry (sfc_POINT) - us_geometry (sfc_POINT) -
ds_distance_to_stream - us_distance_to_stream - other columns are
preserved

### Functions

- Compare two networks differences in
  - stream_ids
  - stream_names with stream_id
  - stream lengths
  - parent\_
- Create from bunch of multi line strings
- Create from FWA information
- Change projection
- Flip streams by listing and/or based on elevation
- Snap points to stream network can also include stream_id, and section
  table (in or out of sections)
- Convert segment to sections (and vice versa)
- Trim streams using points or polygon (and recalculate length and
  proportions and drop those outside)
- Interpolate between points to get values
- Convert to SSN (or just get distances as fish swims among points?)
- Map network
- Plot as schematic
- Create sections by choosing a point and going downstream
- Create sections by choosing a point and going upstream
- Filter on sections and/or segments

### Dependencies

- [`tibble`](https://github.com/tidyverse/tibble)

- [`sf`](https://github.com/r-spatial/sf)

- [`lwgeom`](https://github.com/r-spatial/lwgeom) \#### Possibilities

- [`dm`](https://github.com/cynkra/dm)

### Related Packages

#### tidyverse

- [`sfnetworks`](https://github.com/luukvdmeer/sfnetworks)
- [`tidygraph`](https://github.com/thomasp85/tidygraph)
- [`gggraph`]()
- [`igraph`]()
- SSN2

#### others

- [`fwatlasbc`](https://github.com/poissonconsulting/fwatlasbc)
- [`streamgis`](https://github.com/mattjbayly/streamgis)
- <https://github.com/mbtyers/riverdist>
- <https://github.com/pet221/SSNbler>

## Installation

You can install the development version of streamnetwork from
[GitHub](https://github.com/) with:

``` r
# install.packages("pak")
pak::pak("poissonconsulting/streamnetwork")
```

# Detection Format Specification

## Description

Detection is a format designed to encode the basic information of an earthquake
event Detection.  Detection uses the [JSON standard](http://www.json.org).

## Usage
Detection is intended for use in seismic data messaging between seismic
applications.

## Output
```json
    {
      "Type"        : "Detection",
      "ID"          : String,
      "Source"      :
      {
         "AgencyID" : String,
         "Author"   : String
      },
      "Hypocenter"  :
      {
          "Latitude"        : Number,
          "Longitude"       : Number,
          "Depth"           : Number,         
          "Time"            : ISO8601,
          "LatitudeError"   : Number,
          "LongitudeError"  : Number,
          "DepthError"      : Number,
          "TimeError"       : Number
      },      
      "DetectionType"   : String,
      "DetectionTime"   : ISO8601,
      "EventType"       : String,
      "Bayes"           : Number,
      "MinimumDistance" : Number,
      "RMS"             : Number,
      "Gap"             : Number,
      "Data"            : [PickJSON and/or CorrelationJSON Objects, ...]
    }
```

## Glossary
Required Values:
* Type - A string that identifies this message as a detection.
* ID - A string containing an unique identifier for this Detection.
* Source - An object containing the source of the Detection, see
[Source](Source.md).
* Hypocenter - An object containing the hypocenter of the Detection, see
[Hypocenter](Hypocenter.md).

Optional Values:
* DetectionType - A string that identifies whether the Detection is `New`,
`Update`, or `Final`.
* DetectionTime - A string containing the UTC time this detection was made,
i.e. how quickly after origin time was this detection created, in the ISO8601
format `YYYY-MM-DDTHH:MM:SS.SSSZ`.
* EventType - A string containing the type of Event that was detected;
`earthquake` or `blast`.
* Bayes - A decimal number that identifies bayesian statistic for this Detection.
* Sigma - A decimal number indicating the standard deviation of the hypocenter
time measurement.
* Data - An array of [Pick](Pick.md), and / or
[Correlation](Correlation.md) objects used to generate this Detection.
* MinimumDistance - The minimum distance to the closest station.

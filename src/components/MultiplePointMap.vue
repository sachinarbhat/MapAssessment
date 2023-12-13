<template>
    <div id="container"></div>
  </template>
    
    <script>
  import Highcharts from "highcharts";
  import HighchartsMap from "highcharts/modules/map";
  
  HighchartsMap(Highcharts);
  import "highcharts/modules/exporting";
  import "highcharts/modules/offline-exporting";
  import "highcharts/modules/accessibility";
  
  export default {
    mounted() {
      fetch("https://code.highcharts.com/mapdata/countries/us/us-all.topo.json")
        .then((response) => response.json())
        .then((topology) => {
          Highcharts.mapChart("container", {
            chart: {
              map: topology,
            },
            title: {
              text: "United States of America Map",
            },
            accessibility: {
              description:
                "Map where city locations have been defined using latitude/longitude.",
            },
            mapNavigation: {
              enabled: true,
            },
            tooltip: {
              headerFormat: "",
              pointFormat:
                "<b>City: {point.name}</b><br>Lat: {point.lat}, Lon: {point.lon} <br> Population: {point.Population}",
            },
            series: [
              {
                name: "United States of America",
                borderColor: "#A0A0A0",
                nullColor: "#ffc2b3",
                showInLegend: false,
              },
              {
                name: "Separators",
                type: "mapline",
                nullColor: "#727079",
                showInLegend: false,
                enableMouseTracking: false,
                accessibility: {
                  enabled: false,
                },
              },
              {
                type: "mappoint",
                name: "Cities",
                accessibility: {
                  point: {
                    valueDescriptionFormat:
                      "{xDescription}. Lat: {point.lat:.2f}, lon: {point.lon:.2f}.",
                  },
                },
                color: "#661400",
                data: [
                  {
                    name: "Nebraska",
                    lat: 41.5002,
                    lon: -99.68550000000001,
                    Population: "19.6 Lakhs",
                  },
                  {
                    name: "Massachusetts",
                    lat: 42.3739,
                    lon: -71.99930000000001,
                    Population: "69.8 Lakhs",
                  },
                  {
                    name: "Washington",
                    lat: 47.4865,
                    lon: -120.361,
                    Population: "7.3 Lakhs",
                  },
                  {
                    name: "California",
                    lat: 36.7496,
                    lon: -119.591,
                    Population: "3.92 Crores",
                  },
                  {
                    name: "New Mexico",
                    lat: 34.5002,
                    lon: -106.024,
                    Population: "21.2 Lakhs",
                  },
                  {
                    name: "Arkansas",
                    lat: 34.7563,
                    lon: -92.14279999999999,
                    Population: "30.3 Lakhs",
                  },
                  {
                    name: "Texas",
                    lat: 31.131,
                    lon: -98.7607,
                    Population: "2.95 Crores",
                  },
                  {
                    name: "Ohio",
                    lat: 40.0924,
                    lon: -82.67189999999999,
                    Population: "1.18 Crores",
                  },
                  {
                    name: "Alabama",
                    lat: 32.8551,
                    lon: -86.7184,
                    Population: "50.4 Lakhs",
                  },
                  {
                    name: "Virginia",
                    lat: 37.7403,
                    lon: -78.2431,
                    Population: "86.4 Lakhs",
                  },
                  {
                    name: "New Jersey",
                    lat: 40.0449,
                    lon: -74.4653,
                    Population: "92.7 Lakhs",
                  },
                ],
              },
            ],
          });
        });
    },
  };
  </script>
    
    <style>
  #container {
    width: 100%;
    height: 600px;
  }
  </style>
    
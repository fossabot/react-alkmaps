# react-alkmaps

![Under Development](https://allamericandreamhomes.com/wp-content/uploads/underconstruction.png)

>

[![Build](https://travis-ci.org/itsmeganesh-cse-iiit/react-alkmaps.svg?branch=master) ![NPM](https://img.shields.io/npm/v/react-alkmaps.svg)](https://www.npmjs.com/package/react-alkmaps) [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

## Support react-alkmaps

To support react-alkmaps visit [SUPPORT](https://www.patreon.com/ganeshkoilada) page.

## Features added

- [Adding Vector Layer](#)
- [Adding Vector Points to Vector Layer](#) - Vector point , external image and svg supprot

## Install

```bash
npm install --save react-alkmaps
```

## Usage

```jsx
import React, { Component } from "react";

import ReactAlkMaps, { VectorLayer, VectorPoint } from "react-alkmaps";

class Example extends Component {
  constructor(props) {
    super(props);

    this.state = {
      scriptLoaded: false,
      scriptError: false,
      config: {
        onLoad: this.onLoad,
        onError: this.onError,
        // url="https://maps.alk.com/api/1.2/alkmaps.js"
        //! Copy rights alkmaps api key Remove and place your own API Key
        // apikey: "",
        center: { lat: -74.655522, long: 40.367494 }
      },
      vectorPointData: {
        svgVector: {
          latlong: { lat: -73.965522, long: 40.367494 },
          type: "svg",
          data: {
            svg:
              "<svg xmlns='http://www.w3.org/2000/svg' ><circle id='svgCircle' stroke='black' fill='yellow' cx='16' cy='16' r='16' /><text id='svgText' x='16' y='20' font-size='10pt' font-family='arial' font-weight='bold' text-anchor='middle' fill='black' >svg</text></svg>"
          }
        },
        vector: {
          latlong: { lat: -74.655522, long: 40.367494 },
          data: {
            pointRadius: 10,
            fillColor: "red",
            label: "Vector Point",
            labelYOffset: 20,
            fontWeight: "bold",
            fontColor: "#0000AA"
          }
        },
        imageVector: {
          latlong: { lat: -73.655522, long: 40.367494 },
          data: {
            externalGraphic: "https://www.w3schools.com/w3css/img_avatar3.png",
            graphicHeight: 27,
            graphicWidth: 32,
            label: "External Image",
            labelYOffset: 20
          }
        }
      }
    };
  }

  onLoad = map => {
    this.setState({
      scriptLoaded: true
    });
  };
  onError = error => {
    this.setState({
      scriptError: true
    });
  };
  render() {
    const { vectorPointData, config } = this.state;
    return (
      <div>
        <ReactAlkMaps {...config}>
          <VectorLayer label="VectorLayer">
            <VectorPoint {...vectorPointData.svgVector} />
            <VectorPoint {...vectorPointData.vector} />
            <VectorPoint {...vectorPointData.imageVector} />
          </VectorLayer>
        </ReactAlkMaps>
      </div>
    );
  }
}
```

## Props

### <ReactAlkMaps/>

| Field   | Type            |  Default   |        Description        |
| ------- | --------------- | :--------: | :-----------------------: |
| onLoad  | func            |            | Invoked after script load |
| onError | func            |            | Invoked after script fail |
| url     | optional string | AlkMaps V2 |        AlkMaps URL        |
| apikey  | string          |            |      AlkMaps API key      |

### <VectorLayer/>

| Field | Type   |   Default    |    Description    |
| ----- | ------ | :----------: | :---------------: |
| label | string | Vector Layer | Vector Layer name |

### <VectorPoint/>

| Field   | Type                 |                                                                             Default                                                                              |            Description             |
| ------- | -------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------: | :--------------------------------: |
| latlong | object               |                                                                                                                                                                  |         Vector Layer name          |
| type    | `undefined` or `svg` |                                                                            undefined                                                                             |        Vector drawing type         |
| data    | svg                  |                                                                 undefined OR `{svg: svgContent}`                                                                 |     To draw using svg content      |
|         | image                |              {`externalGraphic`:imageURL,`graphicHeight`:20,`graphicWidth`:20,`label`:"label",`labelYOffset`:20} OR `As mentioned in alkmaps site`               | To draw vector with external image |
|         | vector               | {`pointRadius`: 10,`fillColor`: "red",`label`: "Vector Point",`labelYOffset`: 20,`fontWeight`: "bold",`fontColor`: "#0000AA"} OR `As mentioned in Alk maps site` |           To draw vector           |

## License

Copyright © 2020 [Ganesh Koilada](https://github.com/itsmeganesh-cse-iiit).
This project is [MIT licensed](#).

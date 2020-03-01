# react-alkmaps

![Under Development](https://www.pngkey.com/png/detail/365-3650941_no-packages-are-available-right-now-website-under.png)

>

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/facebook/react/blob/master/LICENSE) [![Build](https://travis-ci.org/itsmeganesh-cse-iiit/react-alkmaps.svg?branch=master) ![NPM](https://img.shields.io/npm/v/react-alkmaps.svg)](https://www.npmjs.com/package/react-alkmaps) [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-yellow.svg)](https://standardjs.com) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-blueviolet.svg)](#) [![npm downloads](https://img.shields.io/npm/dm/react-alkmaps.svg?style=flat-square)](https://www.npmjs.com/package/react-alkmaps)[![Gitter][gitter-image]][gitter-url]

## react-alkmaps

For full library documentation [visit this site](https://itsmeganeshcse.gitbook.io/react-alkmaps/)

## Features added

- [Adding Vector Layer](https://github.com/itsmeganesh-cse-iiit/react-alkmaps/blob/master/CHANGELOG.md)
- [Adding Vector Points to Vector Layer](https://github.com/itsmeganesh-cse-iiit/react-alkmaps/blob/master/CHANGELOG.md) - Vector point , external image and svg supprot

## Install

```bash
npm install --save react-alkmaps
```

## Usage

### State data

```jsx
this.state = {
  scriptLoaded: false,
  scriptError: false,
  config: {
    onLoad: this.onLoad,
    onError: this.onError,
    // url="https://maps.alk.com/api/1.2/alkmaps.js" // Optional prop
    // apikey: "",
    center: { lat: -74.655522, long: 40.367494 }
  },
  vectorPointData: {
    svgVector: {
      latlong: { lat: -73.965522, long: 40.367494 },
      type: "svg",
      data: {
        svg:
          "<svg xmlns='http://www.w3.org/2000/svg' >' +
          "<circle id='svgCircle' stroke='black' fill='yellow' cx='16' cy='16' r='16' />"+
          "<text id='svgText' x='16' y='20' font-size='10pt' font-family='arial'"+ "font-weight='bold' text-anchor='middle' fill='black' >svg</text></svg>"
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
```

```jsx
import React, { Component } from "react";

import ReactAlkMaps, { VectorLayer, VectorPoint } from "react-alkmaps";

class Example extends Component {
  constructor(props) {
    super(props);
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

<details>
  <summary><b>ReactAlkMaps component</b></summary>

| Field   | Type            |  Default   |        Description        |
| ------- | --------------- | :--------: | :-----------------------: |
| onLoad  | func            |            | Invoked after script load |
| onError | func            |            | Invoked after script fail |
| url     | optional string | AlkMaps V2 |        AlkMaps URL        |
| apikey  | string          |            |      AlkMaps API key      |

</details>

<details>
  <summary><b>VectorLayer component</b></summary>

| Field | Type   |   Default    |    Description    |
| ----- | ------ | :----------: | :---------------: |
| label | string | Vector Layer | Vector Layer name |

</details>

<details>
  <summary><b>VectorPoint component</b></summary>
  
| Field   | Type                 |                              Default                               |            Description             |
| ------- | -------------------- | :----------------------------------------------------------------: | :--------------------------------: |
| latlong | object               |                                                                    |         Vector Layer name          |
| type    | `undefined` or `svg` |                             undefined                              |        Vector drawing type         |
| data    | svg                  |                  undefined OR `{svg: svgContent}`                  |     To draw using svg content      |
|         | image                | {`externalGraphic:imageURL,...`} OR `As mentioned in alkmaps site` | To draw vector with external image |
|         | vector               |     {`pointRadius: 10,...`} OR `As mentioned in Alk maps site`     |           To draw vector           |

</details>

For complete documentation [visit this site](https://itsmeganeshcse.gitbook.io/react-alkmaps/)

## ChangeLog

[Click here](https://github.com/itsmeganesh-cse-iiit/react-alkmaps/blob/master/CHANGELOG.md) to view all changeLog Details

## Contributing

Contributions, issues and feature requests are welcome.
Feel free to check [issues page](https://github.com/itsmeganesh-cse-iiit/react-alkmaps/issues) if you want to contribute.

## Show your support

Give a :star: if this project helped you in any way!

[![patreon](https://img.icons8.com/cotton/30/000000/donate--v2.png)](https://www.patreon.com/ganeshkoilada) [![ko-fi](https://www.ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/ganeshkoilada)

## License

Copyright © 2020 [Ganesh Koilada](https://github.com/itsmeganesh-cse-iiit).
This project is [MIT licensed](#).

[gitter-image]: https://badges.gitter.im/Join%20Chat.svg
[gitter-url]: https://gitter.im/react-alkmaps/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge

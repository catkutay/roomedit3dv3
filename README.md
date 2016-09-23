# Roomedit3dv3

[![Node.js](https://img.shields.io/badge/Node.js-4.4.3-blue.svg)](https://nodejs.org/)
[![npm](https://img.shields.io/badge/npm-2.15.1-blue.svg)](https://www.npmjs.com/)
[![License](http://img.shields.io/:license-mit-blue.svg)](http://opensource.org/licenses/MIT)

[![oAuth2](https://img.shields.io/badge/oAuth2-v1-green.svg)](http://developer.autodesk.com/)
[![Data-Management](https://img.shields.io/badge/Data%20Management-v1-green.svg)](http://developer.autodesk.com/)
[![OSS](https://img.shields.io/badge/OSS-v2-green.svg)](http://developer.autodesk.com/)
[![Model-Derivative](https://img.shields.io/badge/Model%20Derivative-v2-green.svg)](http://developer.autodesk.com/)

## Description

Forge Viewer extension to move building elements and update the Revit BIM in real-time using [socket.io](http://socket.io).

This is a [node.js](https://nodejs.org) web server implementing a Forge Viewer extension.

It is based
on [Philippe Leefsma](http://twitter.com/F3lipek)'s
node.js-based boilerplate projects for the [Autodesk Forge Web Services APIs](http://forge.autodesk.com).

The following Forge APIs and components are used to manipuate a Revit BIM model:

- Authenticate and authorise the user &ndash; [Authentication (OAuth)](https://developer.autodesk.com/en/docs/oauth/v2)
- Access and download a RVT project file from A360 &ndash; [Data Management API](https://developer.autodesk.com/en/docs/data/v2)
- Translate and access its geometry and metadata &ndash; [Model Derivative API](https://developer.autodesk.com/en/docs/model-derivative/v2)
- Display to the user &ndash; [Viewer](https://developer.autodesk.com/en/docs/viewer/v2)

Just as Philippe original boilerplate code, this sample illustrates use of the following Forge npm packages:

- [forge.oauth2-js](https://github.com/Autodesk-Forge/forge.oauth2-js)
- [forge.oss-js](https://github.com/Autodesk-Forge/forge.oss-js)
- [forge.model.derivative-js](https://github.com/Autodesk-Forge/forge.model.derivative-js)
- [forge.data.management-js](https://github.com/Autodesk-Forge/forge.data.management-js)

The `roomedit3dv3` viewer extension enables interactive selection and movement of selected BIM elements in the model on screen.

The updated elements and their new locations are transferred back from the viewer client to the web server via a REST API call.

The server in turn uses [socket.io](http://socket.io) to broadcast the updates to the rest of the universe.

This broadcast is picked up by the [Roomedit3dApp](https://github.com/jeremytammik/Roomedit3dApp) C# .NET Revit add-in client.

This version supersedes its precursor [roomedit3d](https://github.com/jeremytammik/roomedit3d), which was hardwired for a specific model.

In `roomedit3dv3`, any model can be selected.

Todo: add a project identifier to the broadcasts to enable the C# add-in broadcoast receivers to igonre all messages not pertaining to the current Revit BIM.

The selected element is identified via its Revit UniqueId.

This sample demonstrates the following main interesting aspects:

- [Interactive model modification in the Forge Viewer](#2)
- [Communication back from viewer client to node.js web server via REST](#3)
- [Communication back from the web server to the C# desktop add-in and BIM via socket.io](#4)

Please refer to Philippe's original documentation for
the [prerequisites](https://github.com/Autodesk-Forge/forge-boilers.nodejs#prerequisites)
and [sample setup](https://github.com/Autodesk-Forge/forge-boilers.nodejs#boilers-setup).

Its describes the detailed steps required to set up your own Forge account,
install and modify the sample to use your credentials and deploy as a local server or on a platform such
as [Heroku](https://heroku.com).


## <a name="98"></a>Authors

- [Philippe Leefsma](http://adndevblog.typepad.com/cloud_and_mobile/philippe-leefsma.html), Autodesk Developer Network.
- Jeremy Tammik,
[The Building Coder](http://thebuildingcoder.typepad.com) and
[The 3D Web Coder](http://the3dwebcoder.typepad.com),
[ADN](http://www.autodesk.com/adn)
[Open](http://www.autodesk.com/adnopen),
[Forge Partner Development](http://forge.autodesk.com),
[Autodesk Inc.](http://www.autodesk.com)


## <a name="99"></a>License

This sample is licensed under the terms of the [MIT License](http://opensource.org/licenses/MIT).
Please see the [LICENSE](LICENSE) file for full details.

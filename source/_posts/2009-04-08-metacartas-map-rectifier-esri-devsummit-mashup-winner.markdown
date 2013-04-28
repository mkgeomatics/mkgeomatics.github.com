---
author: admin
comments: true
date: 2009-04-08 15:24:07
layout: post
slug: metacartas-map-rectifier-esri-devsummit-mashup-winner
title: MetaCarta's Map Rectifier + ESRI DevSummit Mashup Winner :)
wordpress_id: 274
categories:
- Web-GIS
tags:
- ESRI
- GIS
- MetaCarta
- OpenSource
---

I never knew about the [MetaCarta Labs' Map Rectifier](http://labs.metacarta.com/rectifier/) tool, but I'll expect to be using it more in the future. After uploading an image to the site, a user has full control over the creation of Ground Control Points. The advanced nature of this tool is shown though included RMS error reporting as well as the choice between multiple transformation algorithms. <!-- more --> In addition to uploading your own content, a user has the ability to add GCPs for other users' uploads as well.

[caption id="attachment_276" align="alignnone" width="300" caption="Above: The MetaCarta Interface"][![Above: The MetaCarta Interface](http://www.mkgeomatics.com/wordpress/wp-content/uploads/2009/04/metacarta-300x170.jpg)](http://www.mkgeomatics.com/wordpress/wp-content/uploads/2009/04/metacarta.jpg)[/caption]

What's really amazing is the ability to directly access rectified images via WMS overlay. Each image hosted on the site is given a unique URL, we can insert into our favorite web mapping clients.

To try it out, I used the [ExtMap - Mashup Framework](http://resources.esri.com/arcgisserver/apis/javascript/gmaps/index.cfm?fa=codeGalleryDetails&scriptID=16067) developed by ArcGIS user [alperdincer](http://resources.esri.com/arcgisserver/apis/javascript/gmaps/index.cfm?fa=codeGallery&authorID=alperdincer). This particular application framework was one of the winners at 2009 ESRI DevSummit, with good reason. I was able to quickly pass in the MetaCarta Labs URL, allowing the ExtMap application to consume and display the WMS layer with ease.

[caption id="attachment_278" align="alignnone" width="300" caption="Above: Adding a Service to ExtMap"][![Above: Adding a Service to ExtMap](http://www.mkgeomatics.com/wordpress/wp-content/uploads/2009/04/add_service-300x158.jpg)](http://www.mkgeomatics.com/wordpress/wp-content/uploads/2009/04/add_service.jpg)[/caption]

In addition to WMS layers, we can add in KML/GeoRSS as well as ArcGIS Server Dynamic/Tiled Map Layers.

[caption id="attachment_279" align="alignnone" width="300" caption="Above: ExtMap Interface"][![Above: ExtMap Interface](http://www.mkgeomatics.com/wordpress/wp-content/uploads/2009/04/extjs-300x187.jpg)](http://www.mkgeomatics.com/wordpress/wp-content/uploads/2009/04/extjs.jpg)[/caption]

Easy as pie? Piece of Cake? Yes. It's innovative projects like these that keep pushing me to learn more about web mapping technology. Big thanks go out to [crschmidt](http://) (who i assumed was involved w/ the project) at MetaCarta and [alperdincer](http://resources.esri.com/arcgisserver/apis/javascript/gmaps/index.cfm?fa=codeGallery&authorID=alperdincer) for putting together two great products.

On a final note, the MetaCarta Rectifier has the ability to export out images as geotiffs, allowing us to consume them in our desktop GIS applications. A quick check in ArcCatalog of the Chernobyl sample image I exported out revealed a WGS84 GCS. I can see some really nice workflows combining this tool with tiling programs such as [GDAL2Tiles](http://www.klokan.cz/projects/gdal2tiles/) for painless TMS creation.

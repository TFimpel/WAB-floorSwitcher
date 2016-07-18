# WAB-floorSwitcher
Custom ArcGIS WebApp Builder widget to show different floors of buildings.

## Summary
A configurable [ArcGIS WebApp Builder](https://developers.arcgis.com/web-appbuilder/) widget to be used for viewing interior building floor plans.
+ leverages webmap configuration and security
+ minimal requirements for data in terms of required fields etc.
+ intuitive user interface
+ three modes of switching between floors: per building, all buildings, SQL

![alt text](https://cloud.githubusercontent.com/assets/7443922/16904367/2df7d6a2-4c5a-11e6-81cc-a8ab9f33129c.png "Screen shots of widget in web browser on desktop PC and Google Nexus5")


## What you need to use this
+ ArcGIS Online Organizational or Developer account
+ ArcGIS WebApp Builder [Developer edition](https://developers.arcgis.com/web-appbuilder/)

## How to use this
1. Install and configure ArcGIS WebApp Builder [Developer edition](https://developers.arcgis.com/web-appbuilder/)
2. Add three layers to a webmap: one for buildings, one for walls, and one for rooms (more details below.)
3. Download and add this widget to your widgetpool
4. Configure the widget properties

## Configurable Properties
![alt text](https://cloud.githubusercontent.com/assets/7443922/16904354/e45f9354-4c59-11e6-8844-5c2edaadc87c.JPG "Screen shots of widget configuration menu.")
+ The widget is designed to work with three map layers. The three layers work together by means of attribute values for buildings, floors, and rooms
+ The idea is this: each building can have zero or more floors. Each floor can have zero or more rooms. Each floor belongs to a building, and each room belongs to a floor.
+ For example in the above screenshot the third layer in the webmap is a Feature Service with one attribute field BUILDING_NUMBER and one attribute field NAME. A feature might have the attribute values BUILDING_NUMBER='001' and NAME='Smith Hall'. The fourth layer in the webmap is a Feature Service with features representing rooms and attributes BUILDING = '001', FLOOR = '0G'. The fifth layer in the webmap is a Feature Service representing walls with attributes BUILDING = '001', FLOOR = '0G', OBJECTID = '1234'. This last layer contains exactly one feature per floor per building.  


## Limitations
This is a student project and at this point has several known limitations:
+ the attribute field describing the floor level should have text values that are between 2 and 3 characters in length (due to regular expression used in per building mode).
+ the attribute fields describing the building and floor should have the same names for the walls layer and the rooms layer (see "Note" on config screen, section "Rooms Layer") 
+ the widget doesn't provide an error message if the feature services are slow to load or completely unavailable. No user-friendly failure- or wait-message is triggered.

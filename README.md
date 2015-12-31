# AnchorFX

### Docking framework for JavaFX platform

AnchorFX is a gratis and open source library for JavaFX to create graphical interfaces with docking features 

#### Features

 * Stations and sub stations support
 * Dockable and floatable panels
 * Splitter and Tabs containers support
 * CSS styling


#### Usage

##### Create a DockStation

```java
DockStation station = AnchorageSystem.createStation();
```

Once created the station, we can create the panels and hook them to the station

##### Create a DockNode

```java
Pane myPanel...
DockNode dockNode = AnchorageSystem.createDock("My Title", myPanel);
dockNode.dock(station, DockNode.DOCK_POSITION.CENTER);
```
A DockNode is the window built around your panel. This window has a title and an icon and it can be defined as:

* Closeable
* Resizable
* Maximizable
* Floatable

If we want to create a knot that can not be closed, we will write

```java
dockNode.closeableProperty().set(false);
```

##### Add a DockNode to a Dockstation

To be visible, a node must be associated with a station. To do this procedure, we use the function dock (...) of DockNode

```java
dockNode.dock(station, DockNode.DOCK_POSITION.CENTER);
```

In this case, the node will be added to the station in a central position. When a station is empty, the location will always be central, otherwise, will be taken the position provided and will be changed the layout

You may also add a node by specifying the percentage of placement of the divider. This percentage is only effective if the position is provided different from the central

```java
dockNode.dock(station, DockNode.DOCK_POSITION.CENTER, 0.8);
```

#### Adding a node over another specific node

AnchorFX provides the possibility to add a node in a generic position respect to another node already present in the station.
This feature lets you design a custom layout when your application starts 

```java
dockNode.dock(otherNode, DockNode.DOCK_POSITION.CENTER);
```


##### Create a DockSubStation

A Dock SubStation is a station that also has the functionality of DockNode
The nodes that are associated with a DockSubStation can only be moved within the DockSubStation associated.


```java
 DockSubStation subStation = AnchorageSystem.createSubStation(station, "SubStation");
 dockSubNode.dock(subStation, DockNode.DOCK_POSITION.CENTER);
 
 subStation.dock(station, DockNode.DOCK_POSITION.LEFT,0.7);
```
 
 ##### Styling with AnchorFX.css
 
 The file AnchorFX.css located within resource, defines a simple default style
 
 ```css

.docknode-title-bar {
    -fx-background-color: rgb(100,100,100);
}

.docknode-title-text{
    -fx-text-fill: rgb(255,255,255);
}

.docknode-content-panel{
    -fx-background-color: rgb(100,100,100);
    -fx-padding: 0
}

.docknode-floating-stack-container-panel {
    -fx-background-color: rgb(100,100,100);
    -fx-padding: 4
}
 
.docknode-split-pane {  
    -fx-padding: 0;  
} 

.docknode-split-pane *.split-pane-divider {  
    -fx-padding: 2;  
    -fx-border-color:transparent;
    -fx-color: darkgray;
} 

.docknode-tab-panel{
    -fx-padding: 0;
}

.docknode-command-button{
    -fx-background-color:transparent;
    -fx-background-radius: 0,0,0;
}

.docknode-command-button:hover{
    -fx-background-color:darkgray;
}

.docknode-command-button:pressed{
    -fx-background-color:darkgray;
}

.docknode-command-button:focused{
    -fx-background-color:transparent;
}

.docknode-command-button-close{
    -fx-background-color:transparent;
    -fx-background-radius: 0,0,0;
}

.docknode-command-button-close:pressed{
    -fx-background-color:red;
}

.docknode-command-button-close:hover{
    -fx-background-color:red;
}

.docknode-command-button-close:focused{
    -fx-background-color:transparent;
} 

.station {
    -fx-background-color: rgb(0,0,0);
    -fx-padding: 0
}

.substation-title-bar {
    -fx-background-color: rgb(0,0,0);
}

.substation-title-text{
    -fx-text-fill: rgb(255,255,255);
}

.dockzone-circle-container-selectors {
    -fx-fill: rgba(0,0,0,0.7);
}

.dockzone-circle-selector {
    -fx-fill: rgba(0,0,0,0.8);
}

.dockzone-rectangle-preview {
    -fx-fill: rgba(63,138,163,0.8);
}
```
 
 
 
## Explore demos on test package

The examples will use the functionality described

 * AnchorFX_test.java
 * AnchorFX_substations.java
 * AnchorFX_settings.java

# Donut Window
A Qt Quick window shaped like a donut.

## The Application
![donut window](/donut.png)

This application demonstrates how to make an irregular shaped window with holes. To achieve this, it uses a [QQuickWidget](http://doc.qt.io/qt-5/qquickwidget.html) as the main window. This allows the window to have a transparent background and be defined by QML.

## QQuickWidget
This class derives from QWidget but has an offscreen QQuickView window that renders the QML scene. It can be used to embed Qt Quick scenes into a QWidget-based UI. It can also be used as a main window because any QWidget that has no parent is given it's own top level window. With the appropriate flags and attributes it can be made transparent.

```c++
// make the window and scene transparent
setWindowFlags(Qt::FramelessWindowHint | Qt::WindowStaysOnTopHint);
setAttribute(Qt::WA_TranslucentBackground);
setClearColor(Qt::transparent);
```

![qquickwidget](/diagram.png)

## The Mask
In order for mouse and focus events to pass through the transparent areas of the window, a mask is needed. The setMask() method of the QQuickWidget is used which accepts either a QRegion or QBitmap. For the donut window we use a monochrome image that matches the donut shape. This way only the donut area catches mouse events.

```c++
setMask(QBitmap::fromImage(QImage(":/donutmask.png")));
```

![mask image](/donutmask.png)

## Uses
* Bubble popups windows
* Desktop particle effects

## To Use
* Open DonutApp.pro in Qt Creator
* Run the project


# First Commit

First git file.Hello, world!
The next lvl play!
/n 顆顆
<<<<<<< HEAD
Add bb1 branch
=======
why doing it again?
>>>>>>> bbb1

final status

# GeoPython-AutoGIS 

Point - 對象表示空間中的單個點。點可以是二維（x，y）或三維（x，y，z）。

LineString -對象（即一條線）表示連接在一起以形成一條線的點的序列。因此，一行包含至少兩個坐標元組的列表

Polygon -對象表示一個填充區域，該區域由形成後環的至少三個坐標元組的列表和（可能）孔多邊形的列表組成。

MultiPoint -object表示點的集合，並且由一個坐標元組列表組成

MultiLineString -object表示線的集合，並且由線狀序列的列表組成

MultiPolygon -object表示多邊形的集合，該集合由從外環和（可能的）孔列表元組構造的多邊形序列列表組成

## Point
### Creating point is easy, you pass x and y coordinates into Point() -object (+ possibly also z -coordinate) :

Import necessary geometric objects from shapely module
In [1]: from shapely.geometry import Point, LineString, Polygon

Create Point geometric object(s) with coordinates
In [2]: point1 = Point(2.2, 4.2)

In [3]: point2 = Point(7.2, -25.1)

In [4]: point3 = Point(9.26, -2.456)

In [5]: point3D = Point(9.26, -2.456, 0.57)


What is the type of the point?
In [6]: point_type = type(point1)


Let’s see what the variables look like
In [7]: print(point1)
POINT (2.2 4.2)

In [8]: print(point3D)
POINT Z (9.26 -2.456 0.57)

In [9]: print(type(point1))
<class 'shapely.geometry.point.Point'>
## Point attributes and functions

Point -對象具有一些可以訪問的內置屬性以及一些有用的功能。最有用的功能之一是能夠提取點的坐標併計算點之間的歐幾里得距離。

### Extracting the coordinates of a Point can be done in a couple of different ways

Get the coordinates
In [10]: point_coords = point1.coords

What is the type of this?
In [11]: type(point_coords)
Out[11]: shapely.coords.CoordinateSequence

Ok, we can see that the output is a Shapely CoordinateSequence. Let’s see how we can get out the actual coordinates:

 Get x and y coordinates
In [12]: xy = point_coords.xy

 Get only x coordinates of Point1
In [13]: x = point1.x

 Whatabout y coordinate?
In [14]: y = point1.y

### What is inside?

In [15]: print(xy)
(array('d', [2.2]), array('d', [4.2]))

In [16]: print(x)
2.2

In [17]: print(y)
4.2

### It is also possible to calculate the distance between points which can be useful in many applications

### the returned distance is based on the projection of the points (degrees in WGS84, meters in UTM)

Calculate the distance between point1 and point2
In [18]: point_dist = point1.distance(point2)

In [19]: print("Distance between the points is {0:.2f} decimal degrees".format(point_dist))
Distance between the points is 29.72 decimal degrees

## LineString

### 創建LineString對象非常類似於Point的創建方式。現在代替使用單個坐標元組，我們可以使用形狀良好的Point -objects列表或傳遞坐標元組來構造線：

 Create a LineString from our Point objects
In [20]: line = LineString([point1, point2, point3])

 It is also possible to use coordinate tuples having the same outcome
In [21]: line2 = LineString([(2.2, 4.2), (7.2, -25.1), (9.26, -2.456)])

### Let’s see how our LineString looks like

In [22]: print(line)
LINESTRING (2.2 4.2, 7.2 -25.1, 9.26 -2.456)

In [23]: print(line2)
LINESTRING (2.2 4.2, 7.2 -25.1, 9.26 -2.456)

In [24]: type(line)
Out[24]: shapely.geometry.linestring.LineString

好的，現在我們可以看到可變線由多個坐標對組成，並且數據的類型為LineString。

## LineString attributes and functions

LineString -object具有許多有用的內置屬性和功能。例如，可以提取LineString（線）的坐標或長度，計算線的質心，沿著線以指定距離創建點，計算線到指定點的最接近距離，並簡化幾何形狀。請參閱Shapely文檔中的完整功能列表。在這裡，我們將介紹其中的一些

### 我們可以像使用Point一樣提取LineString的坐標

 Get x and y coordinates of the line
In [25]: lxy = line.xy

In [26]: print(lxy)
(array('d', [2.2, 7.2, 9.26]), array('d', [4.2, -25.1, -2.456]))

好的，我們可以看到坐標再次存儲為numpy數組，其中第一個數組分別包含所有x坐標，第二個數組分別包含y坐標。

### 通過引用這些數組，我們只能提取x或y坐標，如下所示
[27]中的x坐標：line_x  =  lxy [ 0 ]

通過引用
在[28]中的索引1中的數組，直接從LineObject中提取y坐標：
line_y  =  line 。xy [ 1 ]

在[29]中：print （line_x ）
array（'d'，[ 2.2，7.2，9.26 ]）

在[30]中：打印（line_y ）
array（'d'，[4.2，-25.1，-2.456]）

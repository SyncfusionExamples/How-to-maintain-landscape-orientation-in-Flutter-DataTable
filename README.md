# How to maintain landscape orientation regardless of mobile device orientation in Flutter DataTable (SfDataGrid)?

In this article, we will show you how to maintain landscape orientation regardless of mobile device orientation in [Flutter DataTable](https://www.syncfusion.com/flutter-widgets/flutter-datagrid).

Initialize the [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) widget with all the required properties. You can achieve this by rotating the SfDataGrid using the [RotatedBox](https://api.flutter.dev/flutter/widgets/RotatedBox-class.html) widget as parent, without changing the device's orientation. By using the [OrientationBuilder](https://api.flutter.dev/flutter/widgets/OrientationBuilder-class.html), we can retrieve the orientation of the mobile device. The OrientationBuilder widget rebuilds its child whenever the orientation changes, providing the current orientation as a parameter. By wrapping the OrientationBuilder as parent of the RotatedBox and passing the required [quarterTurns](https://api.flutter.dev/flutter/widgets/RotatedBox/quarterTurns.html) to the RotatedBox, you can maintain the SfDataGrid in landscape mode even if the mobile device is in portrait or landscape mode.

```dart
@override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Syncfusion Flutter DataGrid'),
      ),
      body: OrientationBuilder(builder: (context, orientation) {
        // Maintain the SfDataGrid in landscape mode even.
        // if the mobile device is in portrait or landscape mode.
        int quarterTurns = orientation == Orientation.portrait ? 1 : 0;
        return RotatedBox(
          quarterTurns: quarterTurns,
          child: SfDataGrid(
            source: employeeDataSource,
            columnWidthMode: ColumnWidthMode.fill,
            columns: <GridColumn>[
              GridColumn(
                  columnName: 'id',
                  label: Container(
                      padding: EdgeInsets.all(16.0),
                      alignment: Alignment.center,
                      child: Text(
                        'ID',
                      ))),
              GridColumn(
                  columnName: 'name',
                  label: Container(
                      padding: EdgeInsets.all(8.0),
                      alignment: Alignment.center,
                      child: Text('Name'))),
              GridColumn(
                  columnName: 'designation',
                  label: Container(
                      padding: EdgeInsets.all(8.0),
                      alignment: Alignment.center,
                      child: Text(
                        'Designation',
                        overflow: TextOverflow.ellipsis,
                      ))),
              GridColumn(
                  columnName: 'salary',
                  label: Container(
                      padding: EdgeInsets.all(8.0),
                      alignment: Alignment.center,
                      child: Text('Salary'))),
            ],
          ),
        );
      }),
    );
  }
```

You can download this example on [GitHub](https://github.com/SyncfusionExamples/How-to-maintain-landscape-orientation-in-Flutter-DataTable).
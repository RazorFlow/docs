<meta>
{
    "title": "Dual Y Axes Charts",
    "subtitle": "",
    "index": 8,
    "id": "dual_axis"
}
</meta>

You can create a dual axes chart by calling the {{ linkApi("js", "ChartComponent", "addYAxis") }} function on the chart component. Currently, only column, line and area charts can have dual axes. By default, the chart has a left axis, when the `addYAxis` is called it adds a right axis to the chart. The `addYAxis` function is similar to the {{ linkApi("js", "ChartComponent", "setYAxis") }} function with one exception. It function has an extra parameter `id` associated with it. it looks like this,

~~~
    chart.addYAxis("sales", "Sales", {
        numberPrefix: "$ "
    });
~~~
1. The first parameter is the id of the axis.
1. The second parameter is the name of the Y Axis.
2. The third optional parameter is an object containing **Standard number formatting properties**.

To tell a series to use the new axis instead of the `primary` axis set the unique id of new axis for the yAxis parameter in the config options in the `addSeries` function.

~~~
    $chart.addSeries ("vegetables", "Vegetables", [1313, 1976, 924], {
        numberPrefix: "$",
        seriesDisplayType: "column",
        yAxis: "sales"
    });
~~~

### Complete example

{{ embedExample ('js', 'chart_dual_axes') }}

<meta>
{
    "title": "Updating chart data",
    "subtitle": "",
    "index": 4,
    "id": "chart_update"
}
</meta>

## Updating data values

You can update a chart's data anytime, even after it's rendered using the {{ linkApi("js", "ChartComponent", "updateSeries") }} function. For example:

~~~
chart2.updateSeries ("series_1", [3, 5, 2]);
~~~

This function is useful in several situations, two of them are:

1. When an event is triggered in another component or element, and the data needs to be changed accordingly.
2. In a periodic timer which checks for new data every few seconds.

## Example

{{ embedExample ('js', 'chart_updatevals') }}

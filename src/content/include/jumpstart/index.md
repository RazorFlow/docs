<meta>
{
	"title": "Jump Start",
	"subtitle": ""
}
</meta>

Let's build your first dashboard with RazorFlow! In 15 minutes you will have
built a functional dashboard which is interactive and works great on desktops,
tablets and mobile browsers alike.

#### Before you get started

You will need:

1. A computer running Windows, Mac OS X, or Linux.
2. A modern web browser. RazorFlow supports the latest versions of Firefox, Internet Explorer and Google Chrome.
3. A text editor.

First, create a new empty dashboard:

1. Download RazorFlow, which is a ZIP file and extract it on your computer.
2. In the extracted directory, locate a folder called `empty_dashboard_template`.
3. Make a copy of this folder somewhere else and rename it to `RazorTunes`.

Open the files:

1. In the `RazorTunes` folder, open the `dashboard.js` file in your text editor.
2. Open the `index.html` file in your web browser. You should see a sign saying "Empty Dashboard Template".

#### Set the dashboard title

Open your text editor, change the text "Empty Dashboard Template" to "RazorTunes Executive Dashboard".

```
db.setTitle ("RazorTunes Executive Dashboard");
```

Reload the browser, you should see that your new title should be displayed in the browser.

#### Add a chart component

A key part of every dashboard is a Chart. We'll first add a single-series column chart, which is a commonly used chart. In your text editor, in the section with the text `// Add your components here`, use the following code to add a chart:

```
var artist_chart = new rf.ChartComponent();
artist_chart.setCaption("Top selling artists");
artist_chart.setSize(6, 6);
artist_chart.setLabels (["Beatles", "AC/DC", "Beethoveen"]);
artist_chart.addSeries ("revenue_2012", "2012", [1134, 951, 1019]);
artist_chart.addSeries ("revenue_2013", "2013", [1134, 951, 1019]);
db.addComponent (artist_chart);
```

Reload the page in your browser, you should now see a simple column chart. What just happened here? Let's break it down step by step.

1. You create a new variable called `artist_chart` which is an instance of `rf.ChartComponent`.
2. You used the `setCaption` function to set the caption of the component. This caption is displayed in the top of the component.
3. The `setSize` function set the size of the component as 6 units of width, and 6 units of height. A dashboard has 12 units of width, and your chart will occupy half of the dashboard's width at the top.
4. The `setLabels` function sets an array of labels which will be displayed on the X-axis.
5. There are 2 calls to `addSeries` function which is used to add a series of data. This is the actual data which is displayed on the chart.
6. The `db.addComponent` function adds the component to the dashboard.

#### Add a KPI Component

A KPI or a Key Performance Indicator is a vital part of every dashboard. It shows the current value of a particular metric. In your text editor, add the following code:

```
var scheduled_albums = new rf.KPIComponent();
scheduled_albums.setDimensions (3, 3);
scheduled_albums.setCaption ("Albums scheduled for release next month");
scheduled_albums.setValue(7);
db.addComponent(scheduled_albums);
```

Reload this in the browser, it should display a KPI value which is a caption and numerical value. The KPI component can be used for many other purposes as we'll show later.

Let's break this down:

1. You created a variable called `scheduled_albums` which is an instance of `rf.KPIComponent`
2. You set the dimensions to `3,3` which is 3 units of width and height each. This is a good size for a KPI which just has to show a single number.
3. You set the caption using `setCaption`
4. You set the value of the KPI to be displayed using the `setValue` function which is the central function of a KPI Component.
5. You use `db.addComponent` to add the KPI to the dashboard.


#### Add a table component


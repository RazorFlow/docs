<meta>
{
  "title": "CodeIgniter",
  "subtitle": "",
  "id": "php_mvc_frameworks_codeigniter",
  "index": 0
}
</meta>

## Integrating RazorFlow with CodeIgniter

* Copy the `razorflow_php` directory into `application/libraries`.
* Copy the `Rf.php` into `application/libraries/`.
* Create a directory called `rfDashboards` in the `applications/` directory. This contains all your dashbboard files.
* Note that, the dashboard's classname and filename must match.

You will have to load the RazorFlow wrapper for CodeIgniter.
To load the library use: `$this->load->library('rf')`

### Example Code to render Standalone Dashboard from your controller
In order to load a Standalone Dashboard do the following:

~~~
$this->load->library('rf');

$db = $this->rf->loadDashboard('<dashboardClassname>');
$db->renderStandalone();
~~~

### Example Code to render Tabbed Dashboard from your controller
In order to load a Tabbed Dashboard do the following:

~~~
$this->load->library('rf');

$db1 = $this->rf->loadDashboard('<dashboardClassname>');
$db2 = $this->rf->loadDashboard('<dashboardClassname>');

$tabbed = $this->rf->loadTabbedDashboard (array($db1, $db2));
$tabbed->setTabbedDashboardTitle ('My Tabbed Dashboard');
$tabbed->setActive ($db2);

$tabbed->renderTabbed ();
~~~

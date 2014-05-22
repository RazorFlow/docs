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
* Create a file called `Rf.php` in `application/libraries` with the following content:
  ~~~
  <?php

  if (!defined('BASEPATH')) {exit('No direct script access allowed');}

  require_once(APPPATH . 'libraries/razorflow_php/razorflow.php');

  class Rf {

    private $dashboards_path;
    private $filename;

    public function __construct() {
      /**
        * Edit this path to the location from where your dashboards will be loaded. 
        * For Eg., If you would like to store all your dashboard files in applcation/rfDashboards, you can specify it as:
        * $this->dashboards_path = APPPATH . 'rfDashboards/';
        */

      $this->dashboards_path = '';
    }

    public function requireFile($file) {
      $this->filename = $this->dashboards_path . $file . ".php";
      return $this;
    }

    public function loadDashboard ($className) {
      $this->requireDashboardFile();
      $db = new $className();

      return $db;
    }

    public function loadTabbedDashboard ($dashboards = array()) {
      $tabbed = new TabbedDashboard ();
      foreach($dashboards as $db) {
        $tabbed->addDashboardTab ($db);
      }

      return $tabbed;
    }

    private function requireDashboardFile() {
      require $this->filename;
    }

  }
  ~~~

You will have to load the RazorFlow wrapper for CodeIgniter.
To load the library use: `$this->load->library('rf')`

### Example Code to render Standalone Dashboard from your controller
In order to load a Standalone Dashboard do the following:

~~~
$this->load->library('rf');

$db = $this->rf->requireFile('<dashboard_filename>')->loadDashboard('<dashboard_classname>');
$db->renderStandalone();

/**
  * <dashboard_filename>: The filename without the extension
  * <dashboard_classname>: The classname of your dashboard
  */
~~~

### Example Code to render Embedded Dashboard
In order to load a Embedded Dashboard do the following:

~~~
$this->load->library('rf');

$db_embed = $this->rf->requireFile('<dashboard_filename>')->loadDashboard('<dashboard_classname>');
$data = array(
  "db" => $db_embed
);

$this->load->view('view_name', $data);

~~~

Inorder to render the Embedded Dashboard in your view file use:
~~~
<?php echo $db->renderEmbedded(); ?>
~~~
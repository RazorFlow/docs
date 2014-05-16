<meta>
{
  "title": "Adding authentication to your dashboard",
  "subtitle": "",
  "id": "js_pattern_authentication",
  "index": 0
}
</meta>

{{ notice ('warning', '', "This applies to the JavaScript version of the documentation. These instructions are relatively generic and apply to virtually all " )}}

The fundamental concepts behind adding authentication to your dashboard lies in 2 parts

1. Redirect a user to a login page. On successful login set a cookie to check that a user is valid.
2. Use that cookie to check against each HTTP request that the user has the right access to the data.

### Part 1: Initial dashboard load

When the dashboard loads for the first time, your server-side script should check whether the user has valid authentication, and ask the user to log in in case the user doesn't have access to it.

{{ image ("js/auth_basic_firstload.png") }}
www server is auth proxy between Drupal and client. www server has unlimited access to drupal as priveledged user.
1. registration
...* A register_graphQL_mutation is sent to www with user credentials over https. www creates drupal account on behalf of user 
over drupal API. The minimum volunteer role is given to user at that point. More roles can be added later by administrator.
2. login

...a login_graphQL_mutation is sent to www with user credentials over https. 

..* www obtaines auth token from drupal via code grant.

* The user is guest before he/she is logged in
* User creates account at /login client route. User name and password are sent over https to www server as login graphQL mutation.
* 

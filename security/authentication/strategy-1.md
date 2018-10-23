www server is auth proxy between Drupal and client. www server has unlimited access to drupal as priveledged user.
1. registration
  * A register_graphQL_mutation is sent to www with user credentials over https. 
  
  * www creates drupal account on behalf of user 
over drupal API. 

  * The minimum volunteer role is given to user at that point. More roles can be added later by administrator.
  
2. login
  * a login_graphQL_mutation is sent to www with user credentials over https. 
  
  * www obtaines auth token from drupal via password grant. This takes care of user authentication.
  
  * www obtaines user.id via drupal API using user credentials
  
  * www stores user.id in server session
  
  * www sets HTTPOnly cookie on the client with server session ID
  
  * for each subsequent request from that client, www will query drupal API for user scopes and pass them to graphQL resolvers
  via context. Alternatively, user scopes can be stored in user session for the duration of session or in server cache with a TTL limit.
  
  * each graphQL resolver will check its own scope with scopes granted to user to authorize its data. If user is not authorized, NULL is sent with normal 200 response.


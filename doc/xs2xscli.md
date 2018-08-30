### GETTING STARTED:                                
   login, l                                        Log user in
   logout                                          Log user out
   target, t                                       Set or view the targeted org or space
   api                                             Set or view target api url

 ### APPS:                                           
   apps, a                                         List all apps in the target space
   app                                             Display the status and information about an app
                                                   
   push, p                                         Push a new app or sync changes to an existing app
   scale                                           Change or view the instance count, disk space limit, and memory limit for an app
   delete, d                                       Delete an app
   rename                                          Rename an app
                                                   
   start, st                                       Start an app
   stop, sp                                        Stop an app
   restart, rs                                     Restart an app
   restage, rg                                     Restage an app
                                                   
   events                                          Show recent app events
   files, f                                        Print out a list of files in a directory or the contents of a specific file
   logs                                            Tail or show recent logs for an app
   set-logging-level, sll                          Set the logging level for an app
   unset-logging-level, ull                        Reset the logging level for the given component to its default
   list-logging-levels, lll                        List the manually configured logging levels for an app
   env, e                                          Show all env variables for an app
   set-env, se                                     Set an env variable for an app
   unset-env                                       Remove a variable from the environment of an app

###  SERVICES:                                       
   marketplace, m                                  List available offerings in the marketplace
   services, s                                     List all services in the target space
   create-service, cs                              Create a service instance
   delete-service, ds                              Delete a service instance
   bind-service, bs                                Bind a service instance to an app
   unbind-service, us                              Unbind a service instance from an app
   service-brokers                                 List service brokers
   create-service-broker                           Create a service broker
   update-service-broker                           Update a service broker
   delete-service-broker                           Delete a service broker
   rename-service-broker                           Rename a service broker
   create-user-provided-service, cups              Make a user-provided service instance available to apps
   update-user-provided-service, uups              Update user-provided service instance name value pairs
   register-service-url                            Register a service name with a URL
   unregister-service-url                          Unregister a service URL

###  ORGS:                                           
   orgs, o                                         List all orgs
   create-org, co                                  Create an org
   delete-org                                      Delete an org
   rename-org                                      Rename an org

###  SPACES:                                         
   spaces                                          List all spaces in an org
   create-space                                    Create a space
   delete-space                                    Delete a space
   rename-space                                    Rename a space
   update-space                                    Update settings of an existing space

###  DOMAINS:                                        
   domains                                         List all domains
   create-domain                                   Create a domain
   delete-domain                                   Delete a domain
   set-certificate                                 Sets the SSL certificate used for a domain.
   delete-certificate                              Deletes the SSL certificate used for a domain.

###  ROUTES:                                         
   routes, r                                       List all routes in current space
   create-route                                    Create a url route in a space for later use
   map-route                                       Assign or change the route for an app
   unmap-route                                     Remove a url route from an app
   delete-route                                    Delete a route

###  BUILDPACKS:                                     
   buildpacks                                      List all buildpacks
   create-buildpack                                Create a new buildpack
   update-buildpack                                Update a buildpack
   rename-buildpack                                Rename a buildpack
   delete-buildpack                                Delete a buildpack

###  RUNTIMES:                                       
   runtimes                                        List all runtimes
   runtime                                         Display information about a runtime component
   create-runtime                                  Create a new runtime component
   update-runtime                                  Update properties of a runtime
   delete-runtime                                  Delete a runtime component
   search-runtime                                  Searches for a runtime which best fits a query
   pinned-runtimes                                 List all pinned runtime components for an application
   pin-runtime                                     Pin a runtime component to an application
   unpin-runtime                                   Unpin a runtime component from an application

 ### USER ADMIN:                                     
   users                                           List all users
   purge-users                                     Removes all users from Controller which are not known to UAA [-f]
                                                   
   space-users                                     Show space users by role
   set-space-role                                  Assign a space role to a user
   unset-space-role                                Revoke a space role from a user
                                                   
   org-users                                       Show org users by role
   set-org-role                                    Assign a org role to a user
   unset-org-role                                  Revoke a org role from a user

###  ADMIN:                                          
   traces                                          List all available tracing components
   enable-trace                                    Enable tracing components
   disable-trace                                   Disable tracing components

###  CONFIG:                                         
   running-environment-variable-group, revg        Retrieve the contents of the running environment variable group
   set-running-environment-variable-group, srevg   Pass parameters as JSON to create a running environment variable group
   staging-environment-variable-group, sevg        Retrieve the contents of the staging environment variable group
   set-staging-environment-variable-group, ssevg   Pass parameters as JSON to create a staging environment variable group

 ### BLOB STORE:                                     
   blob-store-info                                 Show information about the blob store.
   blob-set-list                                   Lists all blob sets in the blob store.
   blob-list                                       Lists all blobs in the blob set.
   blob-set-download                               Downloads the content of a blob set as a zip file.
   blob-store-gc                                   Triggers a garbage collection of the blob store.

 ### OTHERS:                                         
   version                                         Show server version information.
   help, h                                         Show help
   system-info                                     Show information about the system infrastructure.
   oauth-token                                     Retrieve and display the OAuth token for the current session

  ### PLUGINS:                                        
   deploy                                          Deploy a new multi-target app or sync changes to an existing one
   undeploy                                        Undeploy a multi-target app
   mta-ops                                         List all active multi-target app operations
   download-mta-op-logs, dmol                      Download logs of multi-target app operation
   mtas                                            List all multi-target apps
   mta                                             Display information about a multi-target app
   target-platforms, tps                           List all target platforms for deployment of multi-target apps
   target-platform, tp                             Display information about a target platform for deployment of multi-target apps
   create-target-platform, ctp                     Create a target platform for deployment of multi-target apps
   update-target-platform, utp                     Update a target platform for deployment of multi-target apps
   delete-target-platform, dtp                     Delete a target platform for deployment of multi-target apps
   install, ins                                    Install software component version
   list-components, lc                             List all installed software component versions
   display-installation-logs, dil                  Display Product Installer log

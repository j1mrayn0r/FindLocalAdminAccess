# FindLocalAdminAccess
A custom Covenant task to find the machines on the local domain the current user has local admin access rights to. The task is basically port of Find-LocalAdminAccess function from PowerSploit. The task basically retrieves a list of computers on the local domain and tries to get a handle from the remote Service Control Manager. If successful, chances are very high that the user has local admin accss rigths on the remote machine. 

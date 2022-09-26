# uic-event-fixer

Two ways to keep your macroponent's events from getting wiped out when deploying custom components.

## A: Business Rule

This is the simplest solution and does not require exposing an API on your dev instance.  
After installing this application in your environment two business rules, an "On Delete" and "After Insert", which will save your configurations to a user preference with a prefix of "Events for Macroponent {sys_id of the macroponent}". 

The events should only fire when the SNC ui-component Command Line tools are making the changes so you can still edit the sys_ux_macroponent record manually if needed.  

## B:API

This is the most complex solution.  This adds a scripted REST api which you can call to update the retrieve and udpate the events before an after deploying your custom component.  It also gives you the most control over the behavior.

The downside of this is that it cannot use your credentials stored in the SNC cli's profile so you will have to retype your instance password each time you use it (or take responsibility to save it some other way on your local dev environment).

I also include a sample deploy.sh script that shows how to use it (it is attached to the "Macroponent" Scripted Rest API record).  **NOTE:** The deploy.sh script is Mac only, but should provide inspiration.

### How to use the API

1. Install the application in your instance.
2. Disable the business rules included in the update set ("Macroponent After Insert", "Macroponent Before Delete")
3. Go the "Macroponent" Scripted REST API that is installed with the application.
4. Check the "Active" checkbox for the service.
5. Download "deploy.sh" file and save it to the root of your custom component application.
6. Follow instructions in the comments of that file to reference your environment and complete deployments in one step.

Example usage:
./deploy.sh https://myinstance.service-now.com 5baf413d9e8aadd990626d67dade34d7 admin

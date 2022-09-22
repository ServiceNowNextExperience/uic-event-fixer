# uic-event-fixer

API to keep your macroponent's events from getting wiped out when deploying custom components.

This installs a scripted REST API that allows you to write scripts that can retrieve the attached events before a custom component deployment and then update them when deployment is completed.

NOTE: The deploy.sh script is currently Mac only.

## How to use

1. Install the application in your instance.
2. Go the Macroponent Scripted REST API that is installed with the application.
3. Download "deploy.sh" file and save it to the root of your custom component application.
4. Follow instructions in the comments of that file to reference your environment and complete deployments in one step.

Example usage:
./deploy.sh https://squashdemo.service-now.com 5baf413d9e8aadd990626d67dade34d7 jon.lind

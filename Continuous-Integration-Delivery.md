# CI / CD

The process for continuously integrating new code into a shared code base and deploying it on a regular basis.

Continuous delivery: Continuous Integration with manual deployment to production

Continuous deployment: Continuous Integration with automatic deployment to production

TeamCity is a powerful continuous integration and build automation tool

TeamCity is responsible for:

- Detecting source control changes
- Compiling the solution
- Running unit tests
- Inspecting code, gathering build metrics, etc.
- Packaging the application ready for deployment
- Using our TeamCity plugin, notify Octopus that a new release is available

Where TeamCity is a build automation server, Octopus is a deployment automation server

Octopus is responsible for

- Distributing the packaged applications to the remote web/application servers, all in a secure way
- Extracting and installing them
- Modifying configuration files with environment-specific variables
- Configure IIS, install and update Windows Services, etc.
- Invoking any custom deployment actions on the remote machines
- Gathering all the deployment logs into a central place

![https://blog.jetbrains.com/wp-content/uploads/2015/11/teamcity-octopus_post2.png](https://blog.jetbrains.com/wp-content/uploads/2015/11/teamcity-octopus_post2.png)

typical **Process:**

- Pull Master, Create Branch and write code locally
- Pull Master and merge with branch when done and run tests to makes sure nothing broke in merging process
- Push Branch and create pull request (tests and coverage checks run automatically on push)
    - push fails if they fail
- Teammate would pull down branch run tests and review the changes then approve them.
- The tester would then merge the branch to master and that would trigger TeamCity to create a build and run tests again
- Octopus would then handle releases and deployments to the different environments
    - env variables were maintained in octopus to avoid exposing them in git
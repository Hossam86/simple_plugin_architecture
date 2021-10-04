# Implementing a Plugin Architecture in a Python Application
A plugin is a software component that adds a specific feature to an existing computer program. When a program supports plug-ins, it enables customization (Wikipedia)

## we will walk through the implementation of a simple plugin system.
###  There are many benefits to building apps with a plugin framework:
1. 3rd party developers can create and extend upon your app
2. new features are easier to develop
3. your application becomes smaller and easier to understand

### Sample Application Flow
We have a program that starts, does a few things, and exits.

![Alt text](pics\program-workflow.png "a title")

## Plugin Architecture Workflow
We refactored our Business Logic into a Plugin Framework that can run registered plugins. The plugins will need to meet the specifications defined by our framework in order to run.

![Alt text](pics\program-workflow-plugin-system.png "a title")


Let's implement a example where we have a plugin framework to print to the console. Our project will have the following structure:

1. internal.py  -- internal business logic
2. external.py  -- contains user-created plugins
3. main.py      --  initialize and run application


## Discussion
The Application's plugin framework works for both internal and external plugins. We define internal plugins in the application code. External plugins are initialized and passed into the application at runtime.

Each plugin inherits from the base Python object and has a process() method. Nothing complex, want to keep this example as simple as possible.

We can run our plugins by calling the application's run() method. This method loops over all the plugins and calls each instance's process() function. As we see from the output above, the plugins are executed in the same order as the list.
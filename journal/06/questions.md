# Single Page Applications with Vue
01. What is the entrypoint of an application?

  The entry point is where the application's main logic or functionality is usually invoked.

02. What is the difference between a vue `component` and `page`?

  The difference between a vue component and page is that a components have their own structure, their own methods and their own APIs. Pages in the other hand are used to represent individual views.

03. What is ***Component-Based Architecture***?

  Component based architecture is encapsulating all the responsibilities within one space. CBA responsibility is split on a component by component basis. Its more freedom and control over the application and an even greater range of customization.

04. What are the three tags that make up a Vue component?

  The three tags that make up a vue component are template, script and style.

05. What are ***lifecycle hooks***? What are lifecycle hooks used for?

  Lifecycle hooks are a window into how the library you are using works behind the scenes. They allow you to know when your component is created, added to the dom, updated or even destroyed. 

06. Which component in Vue does the vue-router use to mount pages onto?

  The component in vue that the vue router uses to mount pages onto is the router view

07. What is the difference between the `AppState` and the state object within a component?

  The difference between the Appstate and the state object with a component is that the AppState provides more of a global store which can store data while in the other hand the state object is referring to the state data to a single component and is not shared.

08. What is the responsibility of `Services` in our Vue projects?

  The responsibility of service is basically still the same as in mvc. Data fetching, logic, and error handling.

09. What are ***props*** and how are they used? Provide an example

  Props are how we pass variables and other information around between different components. An example of how this looks

  props: {project: {type: Project, required: true} }

10. What is the Vue method used to create watchable objects such as `state` or `AppState`?

  The vue method that is used to create watchable objects such as state or AppState is called reactive



---
type: NoteCard
tags: []
---

# Web Dependency Injection
Dependency injection (DI) is a system that enables objects to get dependencies (other objects) from external sources instead of objects creating these dependencies, thus decoupling objects from their dependencies.

In modern web frameworks dependency injection can be achieved using different ways, such as:

*   Props: Passing objects and services to components
*   Global state: A state that is accessible across an app (e.g., React context API)
*   Provider: A way to make data available to multiple components

We will cover ways of DI in our labs and projects, especially, in the Sport and WebXR projects.

Below is an example that illustrate DI using the context API:

    const AppContext = {
      value: 'some value',
      setValue(newValue) {
        this.value = newValue;
      },
    };

    // A hook for using the context
    function useContext(context) {
      return context.value;
    }

    function Connected1() {
      return (
        <button
          onClick={() => {
            AppContext.setValue('Random ' + Math.random());
            render();
          }}>
          Update context value
        </button>
      );
    }

    function Connected2() {
      const ctxValue = useContext(AppContext);

      return <div>Context Value: {ctxValue}</div>;
    }

    // App component
    function App() {
      const ctxValue = useContext(AppContext);

      console.log('Render App context', ctxValue);

      return (
        <div>
          <Connected2 />

          <Connected1 />
        </div>
      );
    }
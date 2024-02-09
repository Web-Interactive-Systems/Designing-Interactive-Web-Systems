---
type: NoteCard
tags: []
---

# Web Routing
Web routing is a system that enables mapping different HTTP URLs to different screens.

Because modern web apps are more and more complex and highly interactive, they require

1.  organizing screens into independent and reusable pieces and
2.  mapping different HTTP URLs to different screens

This concept is known as routing. Routing is an important concept in modern web apps as it allows developers to create multi-page/component applications by handling the mapping between HTTP URLs and different components of an app. However, we do not want the user to wait for pages to reload every time they perform some actions. Interestingly, modern web frameworks update the UI directly depending on routing without reloading the entire page, which offers a better user experience. HTTP URL can be mapped to web pages or components (in SPA). Frameworks like React, Svelte, and Vue rely on some important concepts of routing that we will explore below:

## **Dynamic Components**

For basic routing, it is possible to dynamically switch between components. We can listen to the browser \`popstate\` (and/or \`hashchange\`) event and consequently render components.

    // app components
    const Home = () => <div>Home Page</div>;
    const NotFound = () => <div>404 - Page Not Found</div>;
     
    // Routes
    const routes = [
      { path: '/', component: Home },
      // ...
    ];

    // Render a component based on the current URL
    function renderComponent() {
      // current location path
      const currentPath = window.location.pathname;

      // Get the route of the current URL
      const route = routes.find((r) => r.path === currentPath);

      // Get the component of the route or NotFound
      const component = route ? route.component : NotFound;

      // Render the component inside router-outlet container
      render(component(), document.getElementById('router-outlet'));
    }

    window.addEventListener('popstate', renderComponent);

    // ...

## Route Configuration

The route configuration defines the URL pattern and the corresponding component that should be rendered when the URL matches the pattern. In React, this is usually done using a **router package** like [react-router-dom](https://reactrouter.com/en/main) or [raviger](https://kyeotic.github.io/raviger/) (React does offer an official router library). In Svelte for SPA application packages [svelte-routing](https://github.com/EmilTholin/svelte-routing) or [svelte-navigator ](https://github.com/mefechoel/svelte-navigator)can be used. Svelte meta framework Sveltekit has a built-in router. Vue offers its official routing library: [vue-router](https://router.vuejs.org/). Here are some examples of route configuration:

    // using raviger

    import { useRoutes, Link, useQueryParams } from 'raviger'

    const routes = {
      '/': () => <Home />,
      '/about': () => <About />,
      '/users/:userId': ({ userId }) => <User id={userId} />
    }

    export default function App() {
      let route = useRoutes(routes)
      return (
        <div>
          <div>
            <Link href="/">Home</Link>
            <Link href="/about">About</Link>
            <Link href="/users/1">Tom</Link>
            <Link href="/users/2">Jane</Link>
          </div>
          {route}
        </div>
      )
    }

<!---->

    // using svlete-navigator

    <script>
    	import { Router, Link, Route } from "svelte-navigator";
    	import Home from "./routes/Home.svelte";
    	import About from "./routes/About.svelte";
    	import Blog from "./routes/Blog.svelte";
    	import Search from "./routes/Search.svelte";
    </script>

    <Router>
    	<nav>
    		<Link to="/">Home</Link>
    		<Link to="about">About</Link>
    		<Link to="blog">Blog</Link>
    	</nav>
    	<div>
    		<Route path="/">
    			<Home />
    		</Route>
    		<Route path="about" component={About} />
    		<Route path="blog/*">
    			<Route path="/">
    				<Blog />
    			</Route>
    			<Route path=":id" component={BlogPost} />
    		</Route>
    		<Route path="search/:query" let:params>
    			<Search query={params.query} />
    		</Route>
    	</div>
    </Router>

<!---->

    // using vue-router

    <div id="app">
      <h1>Hello App!</h1>
      <p>
        <!-- use the router-link component for navigation. -->
        <!-- specify the link by passing the `to` prop. -->
        <!-- `<router-link>` will render an `<a>` tag with the correct `href` attribute -->
        <router-link to="/">Go to Home</router-link>
        <router-link to="/about">Go to About</router-link>
      </p>
      <!-- route outlet -->
      <!-- component matched by the route will render here -->
      <router-view></router-view>
    </div>

## **Route Parameters**

Route parameters allow dynamic URL segments to be handled in a route. This is usually done using the syntax below:

    // using raviger

    '/users/:userId': ({ userId }) => <User id={userId} />

    // using svelte-navigator

    <Route path=":id" component={BlogPost} />

    // using vue-router

    { path: '/users/:id', component: User }

Notice the use of the colon `:`. When a route is matched, the value of its params will be exposed to the component.

In \`raviger\` params can be handled within the route and passed to components as props.

In Vue params are available inside a template (\<template>) as: `this.$route.params`

Also, routers provide hooks to get parameters defined in routes inside components.

    // using raviger

    // here: userId will be parsed
    const { userId } = usePathParams('/users/:userId');

<!---->

    // using svlete-navigator

    <script>
    	import { useParams } from "svelte-navigator";

    	const params = useParams();

            // a reactive mechanism of svelte
    	$: console.log($params); // -> { id: "123", splat: "pauls-profile" }
    </script>

    <h3>Welcome user {$params.id}! bleep bloop...</h3>

## **Route Navigation**

Navigation refers to the process of changing the current URL and rendering the corresponding content. This is usually done using an HTML Link component, some hook, or a function provided by the router library.

    // using raviger

    <Link to="/home">Home</Link>

<!---->

    // using svelte-navigator

    <script>
    	import { navigate } from "svelte-navigator";

    	function onSubmit() {
    		login().then(() => {
    			navigate("/success", { replace: true });
    		});
    	}
    </script>


    <button on:click="{() => navigate(-1)}">Back</button>
    <button on:click="{() => navigate(1)}">Forward</button>
<script>
  import { Router, Route, Link } from "svelte-navigator";
  import LazyRoute from "./LazyRoute.svelte";

  const delayModuleLoad = (module) =>
    new Promise((res) => setTimeout(() => res(module), Math.random() * 2000));
  const Home = () => import("./Hero.svelte").then(delayModuleLoad);
  const About = () => import("./About.svelte").then(delayModuleLoad);
  const Blog = () => import("./services.svelte").then(delayModuleLoad);
  const Teams = () => import("./Team.svelte").then(delayModuleLoad);
</script>

<Router>
  <nav class="sticky top-0 px-4 py-4 bg-purple-900 text-white">
    <div
      class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto"
    >
    <a href="/" class="flex items-center">
        <img
          src="https://flowbite.com/docs/images/logo.svg"
          class="h-8 mr-3"
          alt="Flowbite Logo"
        />
        <span
          class="self-center text-2xl font-semibold whitespace-nowrap dark:text-white"
          >Flowbite</span
        >
      </a>
      <div class=" space-x-3 justify-end">
        <Link to="/">Home</Link>
      <Link to="about">About</Link>
      <Link to="blog">Services</Link>
      <Link to="team">Teams</Link>
      </div>
    <!-- <ul >
      <li class="mx-2 cursor-pointer">Home</li>
      <li class="mx-2 cursor-pointer">About</li>
      <li class="mx-2 cursor-pointer">contact</li>
    </ul> -->
    </div>
  </nav>
  <!-- <nav
    class="sticky top-0 border-gray-200 dark:bg-gray-900 bg-gray-400 rounded"
  >
    <div
      class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-4"
    >
      <a href="#" class="flex items-center">
        <img
          src="https://flowbite.com/docs/images/logo.svg"
          class="h-8 mr-3"
          alt="Flowbite Logo"
        />
        <span
          class="self-center text-2xl font-semibold whitespace-nowrap dark:text-white"
          >Flowbite</span
        >
      </a>
      <-- <div class="hidden w-full md:block md:w-auto" id="navbar-default"> -->
      <!-- <Link to="">Base</Link>
      <Link to="/">Home</Link>
      <Link to="about">About</Link>
      <Link to="blog">Services</Link>
      <Link to="team">Teams</Link> -->
      <!-- </div> ->
    </div>
  </nav> -->
  <main>
    <LazyRoute path="blog/*blogRoute" component={Blog} delayMs={500}>
      <h4>Loading...</h4>
    </LazyRoute>
    <LazyRoute path="/" component={Home} delayMs={500}>
      Loading Home...
    </LazyRoute>
    <LazyRoute path="about" component={About} delayMs={500}>
      Loading About...
    </LazyRoute>
    <LazyRoute path="team" component={Teams} delayMs={500}>
      Loading Teams...
    </LazyRoute>
    <!-- <Route>
      <h3>Default</h3>
      <p>No Route could be matched.</p>
    </Route> -->
  </main>
</Router>

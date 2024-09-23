<script>
  // You can import custom CSS files as shown here. In this case, we import a custom global style.
  import "$lib/static/css/glob.style.css"; 

  // Alternatively, if you are using Bootstrap, you could import the Bootstrap CSS file here:
  // import "bootstrap/dist/css/bootstrap.min.css";

  // You have two options for importing Bootstrap's JavaScript:

  // Option 1: Import the entire Bootstrap JavaScript bundle (includes all components).
  // This is useful if you are using multiple Bootstrap components and want everything loaded at once.
  // onMount(async () => {
  //   await import("bootstrap/dist/js/bootstrap.bundle.min.js");
  // });

  // Option 2: Import specific Bootstrap components as needed (e.g., Tooltip, Modal).
  // This approach is more efficient if you only use a few components, allowing for lazy loading of only the required JS.
  // Components can be imported individually when needed in your Svelte components.

  // `data` is passed to the component from SvelteKit's layout or route, holding route-specific data.
  export let data;
</script>

<slot></slot>

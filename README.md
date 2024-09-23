# SvelteKit Bootstrap 5.3 Demo

This project demonstrates how to integrate Bootstrap 5.3 JavaScript components (such as tooltips and modals) into a SvelteKit project. The demo includes multiple product cards with tooltips and a "See more" button that opens a modal with dynamic content.

## Prerequisites

Before running the project, ensure you have the following installed:

- Node.js (v16.x or higher)
- npm (v8.x or higher)

## Getting Started

1. Clone the repository and navigate to the project folder.
2. Install the required dependencies:

```bash
npm install
```

3. Start the application:

```bash
npm run build && npm start
```

This will build the project and start the server.

## Project Structure

The `package.json` contains several useful scripts to manage and build the project:

- **`dev`**: Builds the project and starts the server.
- **`build`**: Compiles the custom styles using SCSS and builds the SvelteKit project.
- **`compiling-style`**: Uses Sass to compile custom SCSS styles into CSS.
- **`preview`**: Previews the built app with Vite.

Ensure that when you start the application, it is running on the specified port (default is usually 3000).

## Bootstrap Integration

This project uses Bootstrap 5.3 for both its CSS and JS functionalities. The integration of Bootstrap components like `Tooltip` and `Modal` is handled using dynamic imports within the `onMount` lifecycle hook of Svelte.
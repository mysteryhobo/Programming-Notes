# Build Process

Takes your working directory and converts it into something that can actually run in production or some other environment (test or UAT)

- Webpack relies on a dependency graph underneath. Webpack traverses through the source to construct the graph, and it uses this information and configuration to generate bundles.

Transpiles any code that needs it. (See Babel)

Copies everything to a build or dist folder

Code Splitting: allows you to split your code into various bundles which can then be loaded on-demand or in parallel. It can be used to achieve smaller bundles and control resource load prioritization which, if used correctly, can have a major impact on load time.

- Hot Module Replacement (HMR): Updating code in the browser without needing a full page refresh.

Minify / Compress code

Asset Hashing (Cache busting file names)
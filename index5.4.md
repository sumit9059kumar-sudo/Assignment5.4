File 1: index.html
HTML
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Assignment 5.4 - CSS Variables & Design Tokens</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>

  <!-- Header Component using CSS Variables -->
  <header class="header">
    <h1 class="heading-large">Design Tokens Showcase</h1>
    <p class="subtitle">A mini design system powered by CSS Custom Properties (:root)</p>
  </header>

  <main class="container">

    <!-- Section 1: Cards Showcase -->
    <section>
      <h2 class="heading-medium">Featured Cards</h2>

      <div class="card-grid">
        <!-- Card 1 -->
        <article class="card">
          <h3 class="heading-small">Primary Action Card</h3>
          <p class="card-body">
            This card uses design tokens for spacing, background colors, borders, and typography sizes.
          </p>
          <button class="btn btn-primary">Primary Button</button>
        </article>

        <!-- Card 2 -->
        <article class="card">
          <h3 class="heading-small">Secondary Action Card</h3>
          <p class="card-body">
            Updating a single variable in <code>:root</code> instantly re-themes this component and the rest of the application.
          </p>
          <button class="btn btn-secondary">Secondary Button</button>
        </article>
      </div>
    </section>

    <!-- Section 2: Buttons Showcase -->
    <section>
      <h2 class="heading-medium">Button Variations</h2>
      <div class="button-group">
        <button class="btn btn-primary">Primary Action</button>
        <button class="btn btn-secondary">Secondary Action</button>
      </div>
    </section>

  </main>

  <footer>
    <p>&copy; 2026 Web Development Assignment — CSS Variables & Design Tokens</p>
  </footer>

</body>
</html>
File 2: styles.css
CSS
/* ==========================================================================
   1. DESIGN TOKENS (:root)
   ========================================================================== */
:root {
  /* Color Tokens */
  --color-primary: #2563eb;        /* Royal Blue */
  --color-secondary: #0d9488;      /* Teal */
  --color-bg: #f8fafc;             /* Light slate gray */
  --color-surface: #ffffff;        /* Pure white for card backgrounds */
  --color-text-main: #0f172a;      /* Dark slate for main body text */
  --color-text-muted: #64748b;     /* Muted gray text */
  --color-border: #e2e8f0;         /* Light border color */

  /* Spacing Tokens */
  --spacing-sm: 8px;               /* Small spacing */
  --spacing-md: 16px;              /* Medium spacing */
  --spacing-lg: 32px;              /* Large spacing */

  /* Font-Size Tokens */
  --font-size-sm: 0.875rem;        /* Small text (~14px) */
  --font-size-md: 1rem;            /* Base body text (~16px) */
  --font-size-lg: 1.25rem;         /* Subheadings (~20px) */
  --font-size-xl: 1.75rem;         /* Section titles (~28px) */
  --font-size-xxl: 2.5rem;         /* Main headings (~40px) */

  /* Additional Structural Tokens */
  --border-radius: 8px;
  --transition-speed: 0.2s ease-in-out;
}

/* ==========================================================================
   2. GLOBAL / RESET STYLES
   ========================================================================== */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  background-color: var(--color-bg);
  color: var(--color-text-main);
  font-size: var(--font-size-md);
  line-height: 1.6;
  padding: var(--spacing-lg);
}

.container {
  max-width: 960px;
  margin: 0 auto;
}

/* ==========================================================================
   3. TYPOGRAPHY (Headings using Tokens)
   ========================================================================== */
.heading-large {
  font-size: var(--font-size-xxl);
  color: var(--color-primary);
  margin-bottom: var(--spacing-sm);
  font-weight: 800;
}

.heading-medium {
  font-size: var(--font-size-xl);
  color: var(--color-text-main);
  margin-top: var(--spacing-lg);
  margin-bottom: var(--spacing-md);
  border-bottom: 2px solid var(--color-border);
  padding-bottom: var(--spacing-sm);
}

.heading-small {
  font-size: var(--font-size-lg);
  color: var(--color-text-main);
  margin-bottom: var(--spacing-sm);
}

.subtitle {
  font-size: var(--font-size-lg);
  color: var(--color-text-muted);
}

/* ==========================================================================
   4. HEADER & FOOTER
   ========================================================================== */
.header {
  text-align: center;
  margin-bottom: var(--spacing-lg);
  padding: var(--spacing-lg);
  background-color: var(--color-surface);
  border: 1px solid var(--color-border);
  border-radius: var(--border-radius);
}

footer {
  text-align: center;
  margin-top: var(--spacing-lg);
  padding-top: var(--spacing-md);
  color: var(--color-text-muted);
  font-size: var(--font-size-sm);
  border-top: 1px solid var(--color-border);
}

/* ==========================================================================
   5. CARD COMPONENTS
   ========================================================================== */
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: var(--spacing-md);
}

.card {
  background-color: var(--color-surface);
  border: 1px solid var(--color-border);
  border-radius: var(--border-radius);
  padding: var(--spacing-lg);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.card-body {
  font-size: var(--font-size-md);
  color: var(--color-text-muted);
  margin-bottom: var(--spacing-md);
}

code {
  background-color: var(--color-bg);
  padding: 2px 6px;
  border-radius: 4px;
  font-size: var(--font-size-sm);
  color: var(--color-primary);
}

/* ==========================================================================
   6. BUTTON COMPONENTS
   ========================================================================== */
.button-group {
  display: flex;
  gap: var(--spacing-md);
  margin-top: var(--spacing-md);
}

.btn {
  display: inline-block;
  padding: var(--spacing-sm) var(--spacing-md);
  font-size: var(--font-size-md);
  font-weight: 600;
  border-radius: var(--border-radius);
  border: none;
  cursor: pointer;
  transition: opacity var(--transition-speed);
}

.btn:hover {
  opacity: 0.9;
}

.btn-primary {
  background-color: var(--color-primary);
  color: var(--color-surface);
}

.btn-secondary {
  background-color: var(--color-secondary);
  color: var(--color-surface);
}
Step 6 Verification Instructions: How to Verify Global Variable Updates
To verify step 6 ("Change a variable and verify that multiple elements update"):

Open styles.css and locate the :root block at the top.

Change --color-primary from #2563eb (Blue) to #d97706 (Amber/Gold):

CSS
:root {
  --color-primary: #d97706; /* Updated primary color */
}
Save and refresh index.html in your browser.

Result:

The main header (.heading-large) changes to Amber.

The primary buttons (.btn-primary) change to Amber.

Code snippet accents (code) change to Amber simultaneously across the page without needing to edit individual element styles.
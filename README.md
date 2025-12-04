# threlte-a11y

Screen reader accessibility components for [Threlte](https://threlte.xyz/), the Svelte framework for Three.js.

This library provides a set of accessible components that map 3D objects to HTML elements, making your 3D scenes accessible to screen readers and keyboard navigation.

## Installation

```bash
npm install threlte-a11y
```

## Usage

Wrap your 3D objects with the appropriate `A11y` component. These components handle focus, hover, and click events, and sync them with an invisible HTML overlay.

### A11yButton

Use `A11yButton` for interactive elements that trigger an action.

```svelte
<script>
  import { A11yButton } from 'threlte-a11y';
  import { BoxGeometry, MeshStandardMaterial } from 'three';
</script>

<A11yButton
  description="Click me to perform an action"
  actionCall={() => console.log('Clicked!')}
  activationMsg="Action performed"
>
  <T.Mesh
    geometry={new BoxGeometry(1, 1, 1)}
    material={new MeshStandardMaterial({ color: 'red' })}
  />
</A11yButton>
```

**Props:**

- `description` (string, required): The accessible name of the button.
- `actionCall` (function): Callback function triggered on click or activation.
- `activationMsg` (string): Message announced by the screen reader upon activation.
- `disabled` (boolean): Whether the button is disabled.
- `tabIndex` (number): Tab index for keyboard navigation (default: 0).
- `showAltText` (boolean): Whether to show a visual tooltip on hover.

### A11yLink

Use `A11yLink` for navigation.

```svelte
<script>
  import { A11yLink } from 'threlte-a11y';
</script>

<A11yLink
  description="Go to Threlte documentation"
  href="https://threlte.xyz"
>
  <!-- Your 3D Object Here -->
</A11yLink>
```

**Props:**

- `description` (string, required): The accessible name of the link.
- `href` (string, required): The URL to navigate to.
- `showAltText` (boolean): Whether to show a visual tooltip on hover.

### A11yToggle

Use `A11yToggle` for toggleable states (like a checkbox or switch).

```svelte
<script>
  import { A11yToggle } from 'threlte-a11y';
  let isToggled = false;
</script>

<A11yToggle
  description="Toggle light"
  startPressed={isToggled}
  activationMsg="Light turned on"
  deactivationMsg="Light turned off"
  actionCall={() => isToggled = !isToggled}
>
  <!-- Your 3D Object Here -->
</A11yToggle>
```

**Props:**

- `description` (string, required): The accessible name of the toggle.
- `startPressed` (boolean): Initial state of the toggle.
- `activationMsg` (string): Message announced when toggled on.
- `deactivationMsg` (string): Message announced when toggled off.
- `actionCall` (function): Callback function triggered on toggle.

### A11yImage

Use `A11yImage` for static images or non-interactive content that needs description.

```svelte
<script>
  import { A11yImage } from 'threlte-a11y';
</script>

<A11yImage
  description="A beautiful landscape"
>
  <!-- Your 3D Object Here -->
</A11yImage>
```

### A11yContent

Use `A11yContent` for generic content sections.

```svelte
<script>
  import { A11yContent } from 'threlte-a11y';
</script>

<A11yContent
  description="Main content area"
>
  <!-- Your 3D Objects Here -->
</A11yContent>
```

## License

MIT

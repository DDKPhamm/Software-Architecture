# ADR-004: React with Material-UI for Frontend

## Context and Problem Statement

The CMS needs a frontend framework that supports WCAG 2.1 Level AA accessibility compliance (legal requirement), provides reusable components across multiple user interfaces (consumer portal, agent console, support dashboard), and integrates with the Django REST API.

## Considered Options

* React with Material-UI
* Vue.js with Vuetify
* Angular with Angular Material
* Svelte with Svelte Material UI
* Plain HTML/CSS with Bootstrap

## Decision Outcome

Chosen option: "React with Material-UI", because Material-UI provides WCAG 2.1 AA accessibility out of the box, React's component architecture enables reuse across user roles, and React Native offers a path to future mobile development.

### Consequences

* Good, because Material-UI components have built-in accessibility (ARIA labels, keyboard navigation, focus management)
* Good, because component-based architecture allows sharing UI elements across consumer, agent, and support interfaces
* Good, because large ecosystem and community support for problem-solving
* Good, because React Native uses same concepts for potential mobile app
* Bad, because larger JavaScript bundle size compared to lightweight alternatives
* Bad, because team needs to learn React hooks, state management, and MUI patterns

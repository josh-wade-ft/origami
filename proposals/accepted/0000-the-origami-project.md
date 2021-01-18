# Origami as a project

Let's start treating Origami as a single project, steered by design and the Origami team.

Rather than a series of specifications and a decentralized—yet deeply coupled  repos, let's instead have a single repository that the whole project lives in. 

The Origami Project is the project that this team is responsible for.

Things that live outside the Origami repository are not part of the Origami project.

the problem with Origami is that is meant to be there to solve a design problem, but the way it is implemented right now it is only there to solve a technical problem

right now we have a component system, not a design system. i want to change that.

the reason we don't have anything like Lonely Planet's Rizzo or gov uk's design system page is that we have focused all our attention on this strange decentralised system of components where anyone can make an Origami component by creating a repo in the Financial-Times github and just saying it's an Origami component

we can't talk about it as a single thing, because it isn't a single thing.

## motivation

- When making changes to a lower level component, it can be difficult ot understand how those changes in isolation affect the components that depend on it. It would be able to automatically create screenshots and append them to the PR when a component that has dependents has changed
- Often, changes to components need to happen across every component and that means a PR for every component
- When we make changes to build tools, they often require releases across several repos and when we discover a problem late in that chain it means starting the chain again
- Origami is, as it stands, a component system rather than a design system. Having everything in one place will make it easier to understand as a whole.
- 


## explanation

- We decide what is and isn't part of Origami. Polyfill service, image service? are these part of Origami?
- We move everything that we think of as part of Origami into a single multi-package repository using npm workspaces [`lerna`](https://lerna.js.org/)
- components go in the `components/*` directory, services go in the `services/* ` directory, tools go in the `tools/*` directory, actions go in `.github/actions/*`
- when pull requests are merged, the components that changed since the last version will be released
- we'll need to switch to using conventional commits so the workflow can figure out what needs to be released based on what changed
- initially we should deploy releases to our internal npm repository, until it's working well
- if someone wants to add a component, or make changes to it, both Design and Origami Team get the chance to approve it, or request changes.

## work required

- We have a conversation about what is and isn't part of Origami
- A repository is created
- We use `lerna import` to import our components, services, tools and actions to the correct folders
- We replace calls to origami-repo-data with published json files 
- 

## alternatives

### do nothing

we carry on as we are. i think we're wasting a lot of precious time.

## supporting examples


- https://github.com/gatsbyjs/gatsby uses lerna in independent mode with conventional commits

## notes

### How about components that used to be Origami components but don't go into the new multi-package repo?

If the team that maintains the component would like to maintain it within the Origami project, then it will 

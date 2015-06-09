<!--
{
"name": "advanced-outlearn",
"version" : "0.1",
"title" : "Outlearn Kung Fu",
"description" : "Master the advanced techniques of Outlearn publishing",
"homepage" : "https://github.com/outlearn-content/outlearn-publishing",
"freshnessDate" : 2015-06-08,
"license" : "CC BY 4.0"
}
-->

<!-- @section -->

# Individual Users and Organizations

Whenever you publish something on Outlearn, it will have an owner. The owner can be an individual user or an Outlearn Organization. If you are an individual developer blogger or independent consultant, you are usually best served by publishing your Modules and paths under your own name. Go ahead and build your own brand and get a massive Outlearn following!

Open source projects and companies will find the power of Outlearn Organizations more suited for their needs. When content is owned by an Organization, severals users can have permission to publish under the name of the Organization and to update existing content.

Any Outlearn user can create a new Organization under [My Organizations](https://pilot.outlearn.com/my-organizations) and clicking Add Organization. Once you are a member of an Organization, you can Add a Member under the Members tab. If the person does not have an Outlearn account, you can type in their email to send an invitation. Creating awesome content is often a team sport and we'd hate to have anyone feel left out.


<!-- @section -->

# Publishing as an Organization

If you are a member of an Organization, you can publish content as that Organization. The logistics work almost the same as when you [publish content as an individual user](https://pilot.outlearn.com/learn/outlearn/outlearn-publishing/1). The only difference is that after you click Add a GitHub Repository, you can choose any Organization that you belong to as the Outlearn Owner for the content. When you publish as an Organization, the learners will only see the information of the Organization and not your user account. No matter which team member publishes the content, it all looks nice and uniform to the world.


<!-- @section -->

# GitHub Organizations vs Outlearn Organizations

> **Note:** Outlearn Organizations are similar to GitHub organizations but they are totally independent of each other. The example below explains how it works.

Let's say that you are a member of a GitHub organization called Delightsome that contains the source code and documentation for Delightsome Database. When you go to Import Content in Outlearn and click Add a GitHub Repository, you will be able to import content from repos owned by Delightsome. When you import any repository, you can assign ownership to yourself or to any Outlearn Organization that you are a member of. Outlearn does not require that the GitHub organization and the Outlearn Organization be the same.

You can import content **from** any personal repository where you are the owner or a collaborator and from any repository owned by an organization where you are a member with access to that repo. You can import content **to** your own Outlearn account or to any Outlearn Organization that you are a member of.

To go back to the Delightsome example, if you are also a member of an Outlearn Organization called Delightsome, then you are able to import content:

* from Delightsome GitHub repositories to Delightsome Outlearn Organization
* from personal GitHub repositories to Delightsome Outlearn Organization
* from other GitHub organizations that you are a member of to Delightsome Outlearn Organization
* from Delightsome GitHub repositories to your personal Outlearn account
* from Delightsome GitHub repositories to any other Outlearn Organization that you are a member of

If this sounds complicated, just remember that we give you the flexibility to do the maximum amount of things and trust that you know what content should go where.


<!-- @section -->

# Building a Path from Modules with Different Owners and/or Repositories

Outlearn Paths let you pull in any publicly available Outlearn Modules as well as private Modules that your learners have access to. All the Modules are specified in the `outlearn.json` manifest in the `pages` array. If a Module is declared in the same `outlearn.json` as the path, you can just use the name of the Module. See Module `awesome-first-module` below for an example. If the Module is declared in a separate repository with its own `outlearn.json`, need to import that repo first and then reference the Module by its Outlearn owner _and_ the Module name. In the example below, `grand-second-module` is owned by `delightsome` on Outlearn.

```json
"paths" : [
  {
    "name" : "your-new-path-name",
    "title" : "The Name You Just Chose",
    "description" : "More explanation about your the glorious purpose of your Path",
    "privacy" : "public",
    "pages" : [
      {"page" : "./pages/welcome.md"},
      {"module" : "awesome-first-module"},
      {"module" : "delightsome/grand-second-module"},
      {"page" : "./pages/closing.md"}
    ]
  }
],

"modules" : [
  {
    "olm" : "./modules/awesome-first-module.md"
  }
],
```

> **Note:** Outlearn Modules are referenced by their owner, not by their source repo. If you will import the path to Outlearn Organization Delightsome and it includes a Module owned by Delightsome coming from a different repo, you still need to specify the owner.

The easiest way to keep your Modules and Paths up-to-date is to set them to Autoimport. However, when you update a Module and want to see the changes in a path that is declared in a separate repo, you need to manually refresh the Path because Outlearn does not currently track whether any of the Modules of a Path that are declared in another repo have changed.

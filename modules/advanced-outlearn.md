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

Open source projects and companies will find the power of Outlearn Organizations more suited for their needs. By inviting users to an Organization multiple authors can publish and manage content owned by the Organization.

Any Outlearn user can create a new Organization under [My Organizations](https://pilot.outlearn.com/my-organizations) and clicking Add Organization. Once you are a member of an Organization, you can Add a Member under the Members tab. If the person does not have an Outlearn account, you can type in their email to send an invitation. Creating awesome content is often a team sport and we'd hate to have anyone feel left out.


<!-- @section -->

# Publishing as an Organization

If you are a member of an Organization, you can publish content as that Organization. The logistics work almost the same as when you [publish content as an individual user](https://pilot.outlearn.com/learn/outlearn/outlearn-publishing/1). The only difference is that after you click Add a GitHub Repository, you can choose any Organization that you belong to as the Outlearn Owner for the content. When you publish as an Organization, the learners will only see the information of the Organization and not your user account. No matter which team member publishes the content, it all looks nice and uniform to the world.




<!-- @section -->

# GitHub Organizations vs Outlearn Organizations

> **Note:** Outlearn Organizations are similar to GitHub organizations but they are totally independent of each other. The example below explains how it works.

You can import **from** any repository you have access to on GitHub. You can import **to** your own Outlearn account or any of your Outlearn organizations.

Let's say that you are a member of a GitHub organization called Delightsome that contains the source code and documentation for Delightsome Database. When you go to Import Content in Outlearn and click Add a GitHub Repository, you will be able to import content from repos owned by Delightsome.

When you import any repo, you can assign ownership to yourself or to any Outlearn Organization that you are a member of. Outlearn does not require that the GitHub organization and the Outlearn Organization be the same. In order to be able to import Delightsome content from GitHub into the Delightsome Outlearn Organization, you need to be a member of Delightsome both on GitHub and Outlearn.

Often, your team will share access both to a Github repository with the source of the content, and to the Organization on Outlearn. Note that if you configure a GitHub content import source yourself with auto-import settings, any GitHub user who pushes to the `master` branch will trigger a re-import to Outlearn, whether or not that user is a member of the Outlearn Organization.


<!-- @section -->

# Building a Path from Modules with Different Owners and/or Repositories

Outlearn Paths let you pull in any publicly available Outlearn Modules as well as private Modules that your learners have access to. All the Modules for a Path are specified in the `outlearn.json` manifest in the `pages` array. If a Module is declared in the same `outlearn.json` as the Path, you can just use the name of the Module. See Module `awesome-first-module` below for an example.

A remote Outlearn Module must be available at the time of import. For example, if you reference `delightsome/grand-second-module`, be sure that it exists on Outlearn before importing a path that references it. Remote Modules are referenced by their Outlearn owner _and_ the Module name.

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

> **Note:** If you import a Path to Outlearn Organization Delightsome and it includes a Module owned by Delightsome coming from a different repo, you still need to specify the owner.

The easiest way to keep your Modules and Paths up-to-date is to set them to Autoimport. However, when you update a Module and want to see the changes in a path that is declared in a separate repo, you need to manually re-import the Path because Outlearn does not currently track whether any of the Modules of a Path that are declared in another repo have changed.

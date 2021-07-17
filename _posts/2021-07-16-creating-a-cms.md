---
layout: post
title:  "Creating a CMS for Modern Times"
categories: cms echoplex
---

After spending most of my career working with a CMS in some capacity, I decided to consolidate my experience and lessons learned into a future CMS MVP: echoplex.

The scope of what a CMS is, what content is and who this is for could encompass a large post in itself. I have worked on a variety of CMS platforms for a variety of clients. From public utilities such as ConEd, Duke Energy and Evergy (neé KCP&L) to large multi-nationals like PepsiCo, ExxonMobil and L'Oréal to news sites like US Soccer. All have had very distinct needs with the basic need of delivering meaningful content to the consumer with engaging marketing content.

From a purely technical perspective, developing a marketing website is straightforward. However, anyone working with a multinational corporation will quickly discover. Software companies as varied as Netflix, Microsoft and Slack discovered rather late that having an effective means of distributing content without modifying code is surprisingly difficult. Simply what works from an engineering perspective limits the ability for copy editors, designers, data analysts and marketers to do their job effectively. Systems which empower the latter to make changes runs the risk of transferring too much power, and consequently code modification, into the hands of non-engineers. Hampering any effort are engineers themselves which design frameworks that allow rapid development but do not lend them a clean separation between code and content.

To illustrate the complexity with a simple example: A water bottle company wishes to run a promotion . They want the banner of the site to showcase "Pure mineral water pure as the Rockies," yet this would not work for their British audience. The problem is not a reference to the Rockies, "mineral water" is a legal term in England. Furthermore, the British division has an approval workflow different from the other divisions. Do you bifurcate the code base or give the CMS platform the ability to manage multiple regions? What if the British division engages in a different advertising agency that wants to put up a microsite with their digital team? Or if you create a separate code base and application, does that violate the license for the proprietary CRM that's run on-premise for both markets?

These decisions are complex and unique to every project. It is completely out of bounds to even begin to discuss the fiscal implications or client management. If  the code is bifurcated between America and Britain to accommodate what are fundamentally two separate applications, that may solve a lot of issues. Then adding a feature as simple as a product carousel on the North American site would result in the features not appearing immediately on the British code base until it may be thoroughly tested. Many stakeholders in non-technical verticals may not understand the ramifications of their decisions and those ramifications are often hard to explain. Even the stalwart tech company Microsoft maintained three separate code bases in the launch of Windows 95 and experienced the technical debt arising from it.

What am I trying to achieve? A template for a flexible CMS using the latest technologies that should last in the lifecycle of a large, corporate website. Usually this is a design cycle of 3-5 years. I will also attempt to annotate and justify any choice made with data and graphs. If something is not annotated assume I'm drawing on experience. The following pillars I'll focus on in creating the application:

* 12Factor application, which will largely set the tone for the entire project.
* WASM+WASI compatability. The framework should be able to be expanded and customized as long as it is able to compile down to WASM. This allows .NET via Blazor, Rust, Typescript and many other modern languages.
* Severless with compatability aimed at Deno Deploy/Cloudflare Workers. Ability to build serverless functions or lambdas with major cloud providers and Kubernetes via the build toolchain. Write once, be able to deploy to the provider of your choice.
* Ease of local development. This means any local environment builds quickly, does not need Internet connectivity and mimics upper environments. A large portion of this project was my dissatisfaction with Kubernetes and vendor lock-in from cloud providers. No uploading code to just test an inner-loop.
* MVP for the initial release. Get something working and mark where improvements can be made.

The initial framework will likely be so broad it could well serve as the underpinning of any modern web application. Indeed, most client engagements use the marketing site as a springboard for a custom application on the web or on native devices.

Github repository: https://github.com/geoffreysmith/echoplex
Kanban board: https://github.com/geoffreysmith/echoplex/projects/
---
title: Blog
layout: default
nav_order: 2
---

#### 2023-11-10


## How not to do monorepo
-------------------------

Among the tech scenes, monorepo is not a foreign concept. It is used in major tech companies such as Google, Facebook, Uber, etc. For folks who are not familiar with it, ChatGPT listed the following points as the benefits of a monorepo, which all I agree.

1. **Code Sharing and Reusability:**
   - All code is in one place, making it easier for teams to share and reuse code across projects.
   - Shared libraries, utilities, and components can be easily maintained and updated.

2. **Atomic Changes Across Projects:**
   - Changes that span multiple projects can be made atomically, ensuring consistency across the codebase.
   - Atomic commits help avoid issues that may arise when different projects are on different versions of shared code.

3. **Consistent Development Environment:**
   - Developers working on different projects can have a consistent development environment since they are all working from the same codebase.

4. **Simplified Dependency Management:**
   - Dependencies can be managed more easily as they are centralized in the monorepo. It's easier to track and update dependencies across the entire codebase.

5. **Unified Build and CI/CD Pipeline:**
   - A single build and continuous integration/continuous deployment (CI/CD) pipeline can be used for all projects, streamlining the development process.
   - This can lead to faster and more reliable build processes.

6. **Easier Refactoring:**
   - Refactoring code that spans multiple projects is more straightforward when all the code is in one repository.
   - Developers can make changes across the monorepo and ensure that everything continues to work cohesively.

7. **Centralized Versioning:**
   - Versioning is centralized, making it easier to manage and track changes across the entire codebase.
   - Ensures that all projects are on the same version of shared code.

8. **Simplified Code Reviews:**
   - Code reviews can be more comprehensive, as developers have visibility into changes across the entire codebase.
   - It's easier to catch potential issues that may arise from changes in shared code.

9. **Cross-Project Consistency:**
   - Consistency in coding standards, practices, and documentation can be more easily enforced across all projects.

10. **Enhanced Collaboration:**
    - Improved collaboration among teams working on different projects, as they have a shared understanding of the entire codebase.

However, going from multi-repo to a monorepo isn't always easy. Let's see what might be in the way.

Let's say your organization isn't fully ready for the concept and want to try it out before fully jumping onto the bandwagon, which is totally reasonable. What would be a good approach vs not?


Although monorepos could carry many benefits, for folks who have never developed in a monorepo, it is totally reasonable to have doubts on it. Therefore, we need strong set of pain points today to motivate the developers to be onboard with the idea. 

In Twitter's case, it was the "publshing hell", i.e. if service A -> B -> C ( -> means depends on), and each of them have some IDL defined. If C's IDL changes, then C needs to publish the change for B to consume from a separate repo, and then B needs to be published in order for A to consume, so on and so forth. Eventually it got to 5 to 6 levels deep for twitter at the time. Thus a change could take months to propagate, test and eventually get online.

Another reason could be relatively simple, e.g. "our team's CI time is horrible", then bazel (in a monorepo setting) can most efficiently build and test the projects. In the current market, for sizable monorepos, there is no real competitor to bazel.

In either case, it is generally recommended to have a strong single (or two) reason to motivate the migration, to provide something people can strongly hope for.

On the contrary, if a team seems happy with where they are as a small repo, it's probably hard to get buy-in from them, because if they are in the game for a while, chances are they will run into issues here and there, and probably would want a monorepo. Some of the aspects could include
1. the team / project is very new, so there hasn't been any team that need to depend on them, thus for them to manage the SDLC for other developers.
2. "our team only needs to publish code updates, but adoption rate isn't our responsibility, because other teams can choose what they want."
3. the team / project only aims for short term benefits or scopes, in which case there is no incentive at all. The project could be dead in a few weeks / months, why spend the time migrating to monorepo.

Why are teams happy with where they are
1. Affordable QA cost. In some peculiar market, the cost of hiring a software engineer is about hiring 3 QA engineers, and 


Code is our asset. While code is indeed a asset of a company, it is not the most important asset. The most important asset is people, because people how to use or not to use / where to use the code, the context around the code, etc.


larger background: what drives people to be more near sighted.
* unpredictable policies
* more and more tightened market and area to grow




Heavy rely on QA because QA cost is significantly lower than software engineering cost.

Organizational power grab

"selfish" developers


the worse than before multi monorepos, the forgotten monorepos









#### 2022-11-25 

## A Slice Of My 7 Years And Change @ Twitter
---------------------------------------------

After a fun ride of 7 years and 4 months, Nov 17th, 2022 was my last working day at Twitter by not choosing being “hardcore” ([context](https://gizmodo.com/elon-musk-email-be-part-of-hardcore-twitter-or-leave-1849789128)), so now is probably a good time to share part of what I have learned at Twitter (all “Twitter” references below are about the company, not the product).

### Communicate Fearlessly To Build Trust

People have always said Twitter is an amazing place to work at, and its culture is definitely part of that.

What is culture? It can simply be how a group of people speak, ask questions, listen (if at all), give support, etc. Hence Twitter's culture affects how I behave, and at the same time, my behavior also contributes to such culture which affects other people.

One of the core values is “communicate fearlessly to build trust” where “fearless” does not mean rude, but direct and timely. However if the receiver cannot process this correctly, things can go wrong very quickly. Personally I have observed disheartening cases like this where coworkers’ relationship soured for something totally repairable. Therefore it cannot be an empty statement, but a skill to learn.

During my time at Twitter, I had always assumed people had the best intentions, and I had never felt disrespected even when my colleagues disagreed with me or felt embarrassed or ashamed admitting my own mistakes, including almost bringing down twitter.com a couple of times, because this is the basis to improve myself and our team. It is also a sign that other people have great trust in me when they are willing to provide the feedback.

Twitter also puts these values into action. For example, TWIG was a training program for seasoned engineers and managers to learn about what kind of people exist on this planet and what the best way is to communicate with them. “Recognize that passion and personality matter.”

One key takeaway for me is that trust is the foundation for any communication. It does not matter whether what you said was right or wrong, if the receiver has no trust in the giver, there is likely no positive outcome. This is why I think it is extremely important to understand why things are the way they are or people behave the way they do before making any suggestions or judgments. Therefore it is essential to explicitly state the intention and to set up a common goal before any difficult conversation.

### Growing With Others

It is easy to see the benefit of working with more experienced people, but I want to highlight that the reverse is also true.

I have always enjoyed mentoring and working with junior engineers (by tenure or experience). It may be a natural instinct that engineers don’t like others to touch their code, but sometimes our instincts serve us the opposite way.

There are a few aspects to this:

1. “If I am the only person who knows how this piece of code works, job secured!”. While it might be true, it also means one may be stuck with it, thus having no growth for their career. Hence the counter-intuitive conclusion is that one should always strive to be replaceable.
2. It is a great way to get feedback on your own code. Code quality is not only about elegance, but also readability and maintainability.
3. The industry is moving forward rapidly, and it is very common for me not to be able to keep up with the latest trends or technologies, so I expect them to teach me as well, as one might say “my teachers are getting younger and younger”.

### Closing

I would like to quote someone I don’t recall but cannot strongly agree enough with - “Twitter teaches you how to treat people right”, and that’s a lifelong treasure to keep that no one can take away from me.

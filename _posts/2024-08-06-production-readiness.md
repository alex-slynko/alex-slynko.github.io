---
title: "Production Readiness"
date: 2024-08-06
---

Production readiness is a set of criteria that make it easier to operate a system in production. It is not required and there is no well-defined checklist. Most of the systems I met in my career got to production without this concept in mind and we slowly improving over time.
One of the best lists I found was in Pivotal. They had a big list with well-defined criteria and the note that the system should not meet all of them before going to production but the team should be able to answer on all the point and have a concious decision to go to production.
There are other lists like the launch checklist in Google SRE book or some offerings by random website.
In general there are some common groups of criteria that are important to consider:

1. You need to run and update the system. So there should be some deployment process, some way to check dependencies and upgrade them, some way to try the change outside of production.
1. You need to see that the system is running (or not). So some kind of monitoring is required. It can be even Twitter-based monitoring where you get the feedback from the users that the system is down.
1. The next one is the resilience of the system. This includes the ability to recover from failures, to handle the load, to scale it, to have a backup and restore process and so on.
1. Security. I would love to say that is the most important but most of the time it is cut down for the sake of the other points. Security includes not only securing the system and data, but also ability to rotate the keys. One more relatively new point is working with the data privacy. It is not only about laws but also protecting the data from government and other entities.

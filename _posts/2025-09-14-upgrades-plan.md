---
title: "Upgrade everything all the time"
date: 2025-09-14
categories: [Production Readiness, Upgrades]
---

The one thing that prevents us from upgrading is the fear of breaking something. The more complex the system, the more we are afraid to change something. And the more we postpone the upgrades, the more complex the system becomes, and the more we are afraid to change something.

The solution is to make the upgrades a regular activity. The more often we do it, the easier it becomes. The more people are involved, the more knowledge is shared and the easier it is.

The goal is to make the upgrades a continuous non-event. The same way as with the software development - the more often you do it, the easier it is. And the more people are involved, the more knowledge is shared and the easier it is.

I love upgrading software. I upgrade software on my machine weekly. And there is a plan that we made back at CFCR days to upgrade Kubernetes version every 3 months and we kept doing it. It worked well for us. We had a plan, we had a process, we had the knowledge and the tools. And we were able to upgrade and share knowledge with the team.

Here is the plan that we used:

1. **Create stories/issues to track the process**: Create a story for each step, this will help to track the progress and make sure that nothing is missed.
2. **Check the release notes**: Check the release notes for the new version, look for any breaking changes, deprecations, and new alpha and graduated features that might be interesting for the team. Write the results in the story.
3. **Create a small presentation**: Create a small presentation for the team, this will help to share the knowledge and make sure that everyone is on the same page. This would let everyone know what to expect and what to look for.
4. **Find the way to develop with the new version**: It can be either with codespaces or some simple script to update the version. The goal is to make it possible for every team member to try the new version and fix issues if necessary.
5. **Make sure tests are running in CI for new version**: Make sure that all tests are passing, this will help to catch any issues early and make sure that the system is working as expected. Your CI should support multiple versions and it should be easy to add new versions.
6. **Create a way to deploy the new version**: Create a way to deploy the new version. It does not matter if it is a script, a terraform code, or a helm chart. The goal is to make it easy to deploy the new version. This works better if you have a non-production environment or even better ephemeral environments to run tests.
7. **Make the new version to be default in non-production environments**: Make the new version available in non-production environments, this will help to catch any issues early and make sure that the system is working as expected. Keep it running for some time.
8. **Prepare the rollback plan**: Prepare the rollback plan, this will help to make sure that you can quickly revert back to the previous version if something goes wrong. Test the rollback plan in non-production environments.
9. **Schedule the upgrade for production**: Schedule the upgrade for production, this will help to make sure that everyone is on the same page and that the upgrade is done in a controlled manner. Make sure to have a rollback plan.
10. **Run the upgrade**: Run the upgrade, make sure to monitor the system and make sure that everything is working as expected. If something goes wrong, use the rollback plan.
11. **Post-upgrade review**: After the upgrade, review the process, what went well, what could be improved, and what was learned. Update the documentation and the process if necessary.
12. **Celebrate the success**: The process is boring. Celebrate the success, this will help to keep the team motivated and make sure that everyone is on the same page.
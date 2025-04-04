# My Home Assistant Blueprints

Based on work by [crnh](https://github.com/crnh/home-assistant-blueprints) and Enhanced for my use case and tested on iPhone

## Notify everybody at home

Easily create scripts that allow you to notify everybody who is currently at home. Requires that you use the person component with presence detection, and have at least some notify services that target a specific person. Tested with the mobile app on Android only.

This blueprint creates a script which can be used like most `notify` services. When you call the script, it checks if the person is at home; if so, the notification is sent.

Setup and configuration for [notify everybody at home](notify_everybody_at_home.md).


## Notify everyone
Simular to the above but also adds a list of people to always notify regardless of their at home state.  Breaks out the data section ito the specific components that are used frequently.

Setup and configuration for [notify everyone](notify_everyone.md)

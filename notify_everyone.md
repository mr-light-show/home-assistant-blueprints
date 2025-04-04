# My Home Assistant Blueprints

This blueprint creates a script which can be used like most `notify` services. When you call the script, it checks if the person is at home; if so, the notification is sent.

## Notify everyone
Simular to the above but alsa adds a list of people to always notify regardless of their at home state.  Breaks out the data section ito the specific components that are used frequently.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://github.com/mr-light-show/home-assistant-blueprints/blob/main/notify_everyone.yaml)

### Configuration

In order to create the script, you need to supply a mapping of person names to their corresponding `notify` services. Say you've got two persons, Lisa and John, resulting in two `person` entities: `person.lisa` and `person.john`. For Lisa, you want to send a notification to `notify.lisa`, and for John, you want to send a notification to `notify.mobile_app_john`. The mapping will then look like this:

```yaml
lisa: notify.lisa
john: notify.mobile_app_john
```

### Usage

The blueprint will create a script, e.g. `script.notify_everybody_at_home`, which you can supply with a number of parameters. These are documented in the script and shown in the service developer tools.

[![Open your Home Assistant instance and show your service developer tools with a specific service selected.](https://my.home-assistant.io/badges/developer_call_service.svg)](https://my.home-assistant.io/redirect/developer_call_service/?service=script.notify_everybody_at_home)

The following parameters can be specified:

- `people_to_always_notify`: List of people to always notify, regardless of their at home state. This is useful for sending notifications to people who are not at home but still need to receive the notification.
- `people`: List of people you want to notify, useful if you want to send the notification only to a specific set of people. If not specified, all people configured in the blueprint are notified.
- `message`: Notification text. 
- `group`: Group name to send the notification to. Notifications with the same group are kept together.  The group is also used as the tag for removing notifications. a message of `clear_notification` will clear notifications in the group.
- `title`: Notification title.
- `subtitle`: Notification subtitle.
- `sound`: "caf" Sound to play when the notification is received. defaults to `Ladder.caf`
- `url`: URL to open when the notification is tapped. relative urls like `/lovelace` will open the dashboard in the app. (for iOS it will also switch to the correct home)

### Limitations

The script is written to call the Home Assistant mobile app notification services. It likely will not work with other notification platforms.

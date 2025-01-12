# Notifications
Notifications can be enabled on a per user basis, and the Portal supports several query and delivery methods.

## Types of Notifications
There are two types of Portal notifications
- **Temporary**: user will only be notified one time.
- **Persistent**: only cleared through explicit user action.

## Notification delivery
Methods by which the Portal will deliver notification data to the end user.

### Basic delivery (default)
When a notification is recieved, the Portal will play a notification sound and alternate the page title between the new notification cound and the actual page title to get the user's attention.

### Toast notifications (recommended)
When enabled by the user, the Portal will display received notifications using the operating system's build in notification mechanism.

## Notification query
Methods the Portal will use to check for new notification. If new notifications are found, a delivery method is employed to deliver the message to the end user.

### Polling Notifications (default)
Once every minute, the Portal will contact the server for new notification data.

### Push Notifications (recommended)
When given permission by the client and enabled, the Portal will wait to be contacted by the server for notification data. 

> [!NOTE]
> Once push notification delivery is enabled, it cannot be disabled from within the Portal. The user must revoke the push notification permission in the browser themselves. This is a browser limitation.

# AdoptOpenJDK/openjdk-email

**MX server management for adoptopenjdk.net**

## Email aliases

The [adoptopenjdk.net](./adoptopenjdk.net) directory contains an 
[aliases.json](./adoptopenjdk.net/aliases.json) file that provides email mappings 
for the adoptopenjdk.net domain. It maps `"from"` usernames @adoptopenjdk.net 
to `"to"` email addresses.

A _credentials.json_ file needs to exist in the same [adoptopenjdk.net](./adoptopenjdk.net) 
directory containing an `"api-key"` property for the [mailgun](http://www.mailgun.com/) 
account managing the adoptopenjdk.net MX servers.  The _credentials.json_ file can 
be found in the secrets repo.

## Updating

The [update](./update) directory contains a simple node program.  To execute:

```
cd update
npm install
node update.js adoptopenjdk.net
```
 
This will read the aliases, fetch the list of mail routes from Mailgun and update 
the routes to make sure they match the required aliases. The Mailgun API key for 
the given domain is required to make this work.

As a reminder, this key must be placed in a file named `adoptopenjdk.net/credentials.json` 
in the form: `{ "api-key": "key-abc..." }`.

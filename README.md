# filter.nostr.wine Relay Readme

## Quickstart

If you already know what this relay does and you're ready to connect here are the steps:

1. Go to https://nostr.wine and sign up for the paid relay by entering your pubkey and paying the invoice. You ***MUST*** be a paid nostr.wine member to access filter.nostr.wine. 
2. Once admitted, add wss://nostr.wine to your relays. This relay is seperate and does not share events with the filter relay.
3. Next, add wss://filter.nostr.wine/REPLACE_WITH_YOUR_NPUB?broadcast=true to your relays (broadcast paremeter is optional and defaults to false)
4. You're done! Play around with adding/removing various public relays to find your ideal global feed.

***IMPORTANT: you must replace REPLACE_WITH_YOUR_NPUB with your nostr npub (not hex) for the relay to accept you.***

## What is it and why should I use it?

The purpose of this relay is to help bridge the gap between paid and public relays. Nostr users have started to experiment with adding more paid relays and removing some (or all) of their public relays. The problem with this approach is you start to lose content from users you are interested in as well as replies and profile metadata from anyone who does not share at least one of your remaining paid/public relays. In addition, some users you share relays with will not have all their posts or profile data load correctly because it may not all be present on the new paid relays. 

Reduced reach is another problem. If you are no longer connected to some of the biggest public relays, users who no longer share relays in common with you will not be able to read your posts. 

## How does it work?

filter.nostr.wine sits in front of our private aggregator relay that constanly pulls new content from many of the largest public relays. When you connect to our relay, we gather all of your follows as well as any account they follow and filter your global event requests to include only content from your web of contacts. When your client requests a note, a profile, available direct messages, or a channel, we pull all of the available related content from our aggregator (unfiltered). This allows you to load profiles and notes of users who do not share relays with you, receive DMs from those same users, as well as read all replies on a given note.

If you choose to include the ?broadcast=true parameter at the end the relay URL after your npub, you will also be broadcasting to several large public relays when you send any events while connected to filter.nostr.wine. The list of public relays updates frequently based on connectivity. We plan to eventually publish live status updates on a website so you can see what is currently online and writing. For now, I will include and update the relays we read from and broadcast to below. 

### Public Relays Read Filter List

These are the relays that we are currently aggregating events from in real time.

- wss://relay.damus.io
- wss://eden.nostr.land
- wss://brb.io
- wss://nos.lol
- wss://relay.current.fyi
- wss://nostr.bitcoiner.social
- wss://relay.orangepill.dev
- wss://nostr.oxtr.dev
- wss://relay.nostr.bg

Last updated: February 9, 2023

We do not plan on adding paid relays (besides eden and orangepill as they were included by default on some clients) to this list. We like to think of those as their own little place that you can choose to be apart of or not individually. 

### Public Relays Broadcast List

These are the relays we are currently broadcasting events to in real time (if you include ?broadcast=true at the end of the filter.nostr.wine relay after your npub).

- wss://relay.damus.io
- wss://nos.lol
- wss://nostr.bitcoiner.social
- wss://nostr.oxtr.dev
- wss://relay.nostr.bg
- wss://relay.current.fyi
- wss://nostr.fmt.wiz.biz
- wss://nostr.mom
- wss://nostr.zebedee.cloud

Last updated: February 15, 2023

##

nostr.wine and filter.nostr.wine were created by [@Katie](https://snort.social/p/npub1qlkwmzmrhzpuak7c2g9akvcrh7wzkd7zc7fpefw9najwpau662nqealf5y) and [@Mazin](https://snort.social/p/npub18kzz4lkdtc5n729kvfunxuz287uvu9f64ywhjz43ra482t2y5sks0mx5sz)

Our aggregator relay behind filter.nostr.wine is running [Strfry](https://github.com/hoytech/strfry) created by [@Doug Hoyte](https://snort.social/p/npub1yxprsscnjw2e6myxz73mmzvnqw5kvzd5ffjya9ecjypc5l0gvgksh8qud4)

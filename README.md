# filter.nostr.wine Relay Readme
Last Updated: June 24, 2024


## Subscription Required

The filter.nostr.wine relay now requires a monthly subscription of 10,000 sats per month (with substantial discounts for larger purchases). New users who sign up to nostr.wine have 1 month of access included in their purchase. Existing nostr.wine users can add time to their filter.nostr.wine account by visiting https://nostr.wine/add-time.

## Quickstart

If you already know what this relay does and you're ready to connect here are the steps:

1. Go to https://nostr.wine and sign up for the paid relay by entering your pubkey and paying the invoice. You ***MUST*** be a paid nostr.wine member to access filter.nostr.wine. 
2. Once admitted, add wss://nostr.wine to your relays. This relay is seperate and does not share events with the filter relay.
3. Next, add wss://filter.nostr.wine to your relays. Your nostr client MUST support [NIP-42](https://github.com/nostr-protocol/nips/blob/master/42.md) for our relay to authenticate you as a paid user.
4. You can optionally add the ?global=all parameter. See [New Global Views](#new-global-views) for further details.
4. You're done! Play around with adding/removing various public relays to find your ideal global feed.

## Why should I use this?

- Improve performance and reliability (no duplicate notes, one high performance relay connection instead of 10+)
- Reduce battery and data usage on mobile devices
- Improve content discovery (see notes outside of your follows but still within your trusted network)
- Reduce spam (by default "global" on filter.nostr.wine is limited to the accounts you follow + the accounts your followers follow)
- Full text search of all aggregated notes (https://search.nostr.wine or NIP-50)

## Why was this made?

The purpose of this relay is to help bridge the gap between paid and public relays. Nostr users have started to experiment with adding more paid relays and removing some (or all) of their public relays. The problem with this approach is you start to lose content from users you are interested in as well as replies and profile metadata from anyone who does not share at least one of your remaining paid/public relays. In addition, some users you share relays with will not have all their posts or profile data load correctly because it may not all be present on the new paid relays. 

Reduced reach is another problem. If you are no longer connected to some of the biggest public relays, users who no longer share relays in common with you will not be able to read your posts. 

## How does it work?

filter.nostr.wine sits in front of our private aggregator relay that continuously pulls new content from many of the largest public relays. When you connect to our relay, we gather all of your follows as well as any account they follow and filter your global event requests to include only content from your web of contacts. When your client requests a note, a profile, available direct messages, or a channel, we pull all of the available related content from our aggregator (unfiltered). This allows you to load profiles and notes of users who do not share relays with you, receive DMs from those same users, as well as read all replies on a given note.

By default you will also be broadcasting to several large public relays when you send any events while connected to filter.nostr.wine. The list of public relays updates frequently based on connectivity. We publish a list of relays we read from and broadcast to at the bottom of this readme. If you wish to disable broadcasting, you can add the parameter broadcast=false to the relay url. Example: wss://filter.nostr.wine?broadcast=false

## New Global Views

As of April 4, 2023 we now support a new parameter global=all (if missing it defaults to follows+follows) at the end of your relay URL. This will remove the follows+follows filter from your global view and show you all of the events we have aggregated using only a very basic spam filter. This view is considered experimental and without any guarantees at this time. Example: wss://filter.nostr.wine?global=all

## NIP-50

We support NIP-50 (search) on filter.nostr.wine. Keyword search is available if your client supports NIP-50. No user configuration or changes are required.

### Public Relays Read Filter List

These are the relays that we are currently aggregating events from in real time:

- wss://relay.damus.io
- wss://nos.lol
- wss://relay.snort.social
- wss://nostr-pub.wellorder.net
- wss://relay.nostr.bg
- wss://nostr.mom
- wss://offchain.pub
- wss://nostr.bitcoiner.social
- wss://nostr21.com
- wss://nostr.oxtr.dev
- wss://nostr.bongbong.com
- wss://relay.primal.net
- wss://nostr.zbd.gg
- wss://nostr-relay.nokotaro.com
- wss://relayable.org
- wss://public.relaying.io
- wss://nostr.fmt.wiz.biz
- wss://socolo.nl
- wss://relay.mutinywallet.com
- wss://nostr.einundzwanzig.space
- wss://relay.nostr.net

Last updated: June 24, 2024

We do not plan on adding paid relays. We like to think of those as their own little place that you can choose to be apart of or not individually. 

### Public Relays Broadcast List

Filter supports [NIP-65](https://github.com/nostr-protocol/nips/blob/master/65.md). Your events are automatically broadcasted to your first 4 "write" relays and the first 4 "read" relays from the first 5 tagged users. 

In addition, these are the public relays Filter is currently broadcasting events to in real time:

- wss://relay.damus.io
- wss://nos.lol
- wss://relay.nostr.bg
- wss://offchain.pub
- wss://nostr.bitcoiner.social
- wss://public.relaying.io
- wss://nostr.fmt.wiz.biz
- wss://socolo.nl
- wss://relay.mutinywallet.com
- wss://nostr.einundzwanzig.space
- wss://relay.nostr.net

Last updated: June 24, 2024

##

nostr.wine and filter.nostr.wine were created by [@Katie](https://njump.nostr.wine/katieannbaker.com) and [@Mazin](https://njump.nostr.wine/mazinkhoury.com)

Our aggregator relay behind filter.nostr.wine is running [Strfry](https://github.com/hoytech/strfry) created by [@Doug Hoyte](https://njump.nostr.wine/doug@hoytech.com)

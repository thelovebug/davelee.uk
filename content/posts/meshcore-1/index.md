+++
author = "Dave Lee"
categories = ["Radio"]
date = 2025-10-16T19:00:00Z
description = ""
featuredImage = "banner.jpg"
slug = "meshcore-initial-thoughts"
summary = "My initial thoughts around the new mesh, and why I'm suddenly so interested in it"
tags = ["meshcore", "meshtastic", "radio"]
title = 'MeshCore initial thoughts'
+++

## The Mesh

Using radio to communicate between two points isn't new.  Look around you.  Most devices that you can see use radio in some way: mobile phones, home internet, home security systems, your car's remote fob, security staff, emergency services, public transport, satellite navigation; to name just a few.  The advent of the Internet of Things (IOT) has made low-powered radio devices - usually using WiFi, Bluetooth, or LoRa - almost ubiquitous.  These could be anything from relaying sensor data - environmental, security, etc - to commercial applications.

They can also be used for fun.

LoRa - the underlying technology for most of these applications - has been around since 2015.  Its ability to send low-power radio signals over long distances has made it a fantastic base for what has colloquially been referred to as The Mesh.

## Meshtastic

Meshtastic was created in 2020 as a way of maintaining communication between communities where internet access may have been problematic.  This is a great use of this technology.  The TL;DR is that you have a Meshtastic node, you place it in an open space where it can potentially be heard by other nodes.  You connect your phone - via an app - to your node over Bluetooth, and you can send and receive messages through your node.  Messages received by your node will then be repeated so that other nodes can hear them.  That way, messages can be sent between two nodes that otherwise cannot talk directly to each other, by using other nodes in between them.

I tried Meshtastic, as did a number of my friends throughout the UK and beyond, but it was a hard fad that people quicly got bored with because there wasn't much take up.

The problem with things like this is that you need other people to talk to.  There are only so many times you can type "Testing" into the void before you give up and move on to something else.  There was also a moment when the operating parameters changed within the mesh - this resulted in some nodes still using the original mode (LongFast) and those in the know using the new mode (MediumFast) - this split the mesh into two, making it even less likely that nodes could talk to each other as LongFast nodes could not speak to MediumFast nodes.

## MeshCore

MeshCore is a reimagining of the Meshtastic intent.  It uses the same devices, the same frequencies, and the same basic concepts.  I'm still learning so I don't know what the technical nuances are between Meshtastic and MeshCore, but I do know that MeshCore has the concept of "repeaters" and "companions".  There are also "room servers" but I've not investigated those yet.

I tried MeshCore for a while but didn't get any messages from my Companion node.  I then joined a Telegram group dedicated to MeshCore in Yorkshire, and I learned a few things.  I then set up a Repeater node and stuck it on my shed roof but didn't get any messages from my Companion node.

A quick aside to explain what the two node type are:

### Companion nodes

Companion nodes are designed to be used by the end user, and connected to a device that the end user can use to interact with the node.  This can be a mobile app, a web browser (using Bluetooth or USB), and possibly some other ways that I haven't explored yet.

As an example, I have a Companion node - a Heltec v3 - which is inside my house.  I connect to that using the MeshCore app on my phone.  All interactions I make on the app are done through this node.  One node, one user, one app.

### Repeater nodes

Repeater nodes - as the name suggests - take messages from Companion nodes and other Repeater nodes, and rebroadcasts them so that other Companions and Repeaters can hear them... and so on and so forth.  I believe the hop limit is currently set to 64, meaning that a message sent by my Companion node can be bounced from Repeater to Repeater up to 64 times before it will go no further.  I think my record to _receiving_ a message is 22 hops, thus far.  There are talks of reducing the hop limit - possibly to 32 - so I don't think that will have that much impact.

As an example, I have a Repeater node - a Lilygo T-Beam 1.6.1 - with a 18650 battery, half way up the supporting pole of my HF antenna.  I will be replacing it with a Seeed Studio XIAO node with battery and solar panel, that I can put at the top of a long pole and forget about it.

My Companion node communicates directly with my Repeater node (but only because it's the closest) which then repeats out to any other nodes that it can see.

## The MeshCore story continues

Then, as happened with Meshtastic, the powers that be within MeshCore said "we're changing modes" from the EU/UK Default to Narrow.  This obviously had the same impact as with Meshtastic of effectively creating two MeshCore meshes talking different languages...but this time there was a _lot_ more noise about it.  Local MeshCore communities coordinated and planned for the change, often liaising with neighbouring regions to ensure that they all did it at around the same time.

So I changed to Narrow once I found out that Doncaster was going to make the change.  And this had zero impact for me... I still had no messages coming through.  Then I remembered one of the key mantras in radio "height is might" so I risked life and limb to attach my repeater node using velcro cable ties to the top of the 12 foot mast on which my HF antenna sits.  Well, I say "top of" but I think I only managed about 10 feet up, and that's only because I coaxed it up there with a long stick.

I got some messages!  I was receiving messages from the mesh!  That was such a buzz!  And I was responding to those messages!  And no-one was hearing me!  Bum!

I think there may have been one instance where someone heard me and responded, but then nothing.

I was patient.  I kept sending test messages in the vain hope that someone heard me again... but no.

## And then it happened

I don't remember the exact date but it was only a week or two ago, suddenly the floodgates opened.  I was receiving message after message.  Multiple in a single minute.  I found myself actually involved in conversations with people around the mesh, as if on Telegram or Signal.  I'd send a message, someone would respond to that message, I'd respond back, etc!  I couldn't explain what had happened for me to suddenly be "on the mesh"!

Of course, as the days progressed, I was learning more and more about MeshCore, the mesh, some of the technology behind it, etc, and I was (obsessively, some might say) checking the repeater paths of messages that I was receiving.  Repeater paths are a somewhat-reliable way of being able to identify how a message got from the originator to my Companion node.  One hop away from me was always the same - my own Repeater node - this makes sense and was completely expected.  The hop before that was always the same also.  This told me that my Repeater had a good path to this other one, which was based in Sheffield about 7mi from my home.  Since then every message that I've checked has had the same final two hops: Sheffield repeater to my repeater to my companion.  I don't know who operates that repeater in Sheffield, but they are solely responsible for me getting onto the Mesh.  I did fire a message into the Yorkshire channel on the mesh to say thank you to the repeater owner, but I have no idea if they saw it or not.

## The future of the mesh (for me)

As I mentioned, I'm going to construct a solar-powered repeater to replace the existing one, and I'm going to put that at the top of a long pole attached to my shed.  In an ideal world I should put it on my roof, however maintaining and updating the node would be next-to-impossible.

As I'm going to have a spare board kicking about at some point, I'm going to set one up for my youngest (who's interested in radio) but I might remove the "Public" channel from his - I'm not particularly comfortable with him seeing people talking about, uh, let's say "intra-familial relations" - yes, that actually happened; an unfortunate side-effect of an unmoderated communications platform.

---

_Post image by taken from []()_

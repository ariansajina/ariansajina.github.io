---
layout: post
title: "Use Signal"
date: 2026-02-25
tags: [opinion]
---

I want you to use Signal. More often than I'd like to, I find myself annoying my friends and loved ones to switch, and having the same conversation over and over again. The conversation goes something like this...

I know what you might say:
What do I care?
For what I use it, it’s fine.
I have nothing to hide.
Don’t worry, I’m not that important.
I just use what everyone else is using.
I had a dealer who used it.

No one cares about the dog memes your siblings send you, the latest gossip from your friend circle, the drinks you’re getting after work this Thursday, or even the most intimate text you send to your partner. What everyone should care about however, is what kind of society we want to live in. It’s not about you, it’s about power.

Facebook messenger is the [dogshit](https://www.securemessagingapps.com/index.html) of messaging apps. It is the equivalent of sending a letter, and writing the content of the letter on the outside of the envelope; the only upside is that it’s faster. The messages are not [end-to-end](https://en.wikipedia.org/wiki/End-to-end_encryption) encrypted by default and Facebook can read and process them. If I told you I live in a country where my government reads everyone’s letters, you’d look at me bewildered and call it authoritarian. Yet in many European countries who boast of democracy (for example Scandinavia), Facebook messenger is the de facto communication platform. Yes, give yourself that bewildered look.

WhatsApp encrypts messages end-to-end. So now, we not only put the letter inside the envelope, but also encrypt the content such that it is incomprehensible to anyone except the person for whom the message is intended (unless you solve a really hard maths problem, but we assume that’s impossible; this is the basic principle of modern cryptography). Major improvement. Still, WhatsApp is highly problematic. Before I can tell you why, we need to know what metadata is.

Metadata is data about data. For a message, data is the content of the message, while metadata is information about the sender, receiver(s), size, date and time, device, location. If I don’t know what you are saying, but know when, where, to whom and how much, I still know an awful lot. WhatsApp does not encrypt metadata. This means that in our letter analogy, they keep the envelopes.

When this data is available on scale, one can learn a lot about society. How many friends does an average person have and how long does an average friendship last? How many communities is the average person a member of? How easy is it to predict someone's location? Does it become easier if I already know the location of one of their friends? How about two? This kind of analysis can give us [cool insights into human behavior](https://www.youtube.com/watch?v=gW4sy0X6pGk), but it's also scary. How strong is a given community? Where strong means how many links can be removed before the community breaks down? In other words, which three people do I need to remove in order to kill this social movement?

This is social [network analysis](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0095978), [community detection](https://towardsdatascience.com/social-network-analysis-community-detection-2b19e836c76c/) and similar well established academic fields which make their methods publicly available. The tools are available to everyone, the data is available to…?

WhatsApp has over [three billion](https://www.statista.com/statistics/260819/number-of-monthly-active-whatsapp-users/) monthly active users. Read: they can attempt to answer all of the above questions for almost half of all living humans. WhatsApp is owned by Meta, which also owns Facebook and Instagram. Read: Meta can (and [does](https://www.facebook.com/privacy/policy?section_id=5-HowDoTheMeta)) combine the data of all three apps into a massive centralized data platform. This is immense unaccountable power.

I think giving such power to a few shareholders is a heavy price to pay for texting and calling. Especially when you have free access to virtually the same service, which by design does not produce such power. Enter [Signal](https://signal.org/#signal).

Signal is a free privacy focused instant messaging service. Signal encrypts both data and metadata, and does not collect user data. Now, the letter is encrypted, the envelope is encrypted, and the envelope self-destructs after you open it. Signal has proven itself both technically (uses recommended cryptographic primitives, code is open source, security has been independently reviewed) and legally (subpoena in [2016](https://signal.org/bigbrother/eastern-virginia-grand-jury/) and [2021](https://signal.org/bigbrother/central-california-grand-jury/), Signal complied and provided all the data it had on the user: two timestamps for when the account was created and when it was last active).

The only real hurdle to switching to Signal is adoption (_none of my friends use it_). If we start having it as an option, and then nudge our contacts to move over time, we can get there. Imagine going to a protest about a cause close to your heart, fists in the air, throats sore from shouting the slogans. Now keep that image in mind and go download the Signal app. You’re essentially doing the same. (Not entirely, because embodied collectivity builds political subjectivity, but you know... allow me a feelgood metaphor.)

Happy messaging.

---

_I initially circulated a version of this text to my friends some years ago. Some convertees, eventually growing tired themselves of having the same conversation again, grabbed it and circulated it further. With that impulse, I felt emboldened to make the text available here._

_Since then, my little article has unfortunately both aged very well (collective privacy is as important as ever and yelling at people to use Signal is still oxygen well spent), and went completely out of touch (to labour the whole point of Meta having all that metadata only to raise concern that they might leverage some decades-old algorithms, and not what Cambridge Analytica on steroids might emerge from giving AI agents access to that data, might make you think I've spent the last five years living in the hills with my cousin and his hogs). So I'd float a few updates._

_Signal has grown and running it isn't cheap. It's about [$50 million a year](https://signal.org/blog/signal-is-expensive/) and their ambition is to make it sustained by small donations. So if you use it, consider [donating](https://signal.org/donate/)._

_[bitchat](https://bitchat.free/) was published in the meantime and I would recommend everyone to have it on their phone. It's a messaging app that serves a very different, but complementary purpose. It uses bluetooth mesh networks to create ad-hoc communication networks using only the devices present in physical proximity._

_Imagine there's an outage in your city, you pick up the phone to check on your friend, but Signal doesn't work: no internet connection. You open bitchat and see your neighbour next door asking if it's the whole building. Soon, enough people on your block have logged in to allow messages to hop from building to building and it's not long before you establish that it's at least the whole neighbourhood, and Giorgio from the ground floor has some candles to spare. More ominously, imagine you're at a protest and cops are jamming the signal; bitchat will work. More gaily, imagine you're in the hills without reception, clearing a field for a music festival, and you need to tell HQ to bring down an extra pickaxe; bitchat has you covered. Basically it's the app that, if it existed at the time it was written, I'm sure would have featured in [Disnaeland](https://barbicanpress.com/book/disnaeland/)._

_Also in the meantime, the creator of Signal has sounded the alarm how AI chats are the latest domain where we are yet to develop a privacy culture. He describes unencrypted conversations with AI as [confessions to a data lake](https://confer.to/blog/2025/12/confessions-to-a-data-lake/)._

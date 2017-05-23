---
title: Becoming the Target of MediaWiki Spambots
date: 2016-12-15
category: articles
tags: mediawiki
---

Recently, I installed a MediaWiki instance on a public-facing server. I knew this was a huge security risk, but since it was on a subdomain that nothing linked to, I assumed I'd be fine. I found that I didn't particularly like working with MediaWiki, so I moved on to a different approach and pretty much forgot all about it.

A few months later, I was shocked to realize there were nearly 100,000 emails sitting in the spam folder for the throwaway email address I set as the admin of the MediaWiki application. It turns out the messages were notifications of new pages, new users, new edits, and more from MediaWiki itself. The bots had found it, and it was escalating quickly!

The site got forty hits in September. A little over 100 in October. A shocking 300,000 in November, and - what?! - four million hits already this December! They'd consumed nearly 20 GB of data just in the last week. I have to admit I was fascinated by how much it seemed to be ramping up. My little shared-hosting MySQL database was 4 GB and growing (sorry, neighbors).

They started out small, and when they realized I wasn't moderating their posts whatsoever they doubled the resources sent my server every day. The articles were mostly nonsense with a link pointing to some small business that paid an SEO firm to try to boost their Google rank. 

Now I just have to wonder if the domain it was hosted on is going to be punished for my little oversight.
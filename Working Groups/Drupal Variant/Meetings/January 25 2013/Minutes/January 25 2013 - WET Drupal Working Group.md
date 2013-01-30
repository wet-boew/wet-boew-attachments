# Jan 25 WET Drupal Working Group notes

## Drupalcamp Ottawa!

* http://drupalcampottawa.com/ 
* Feb 22 and 23
* Andrew Hoppin from NYS Senate (keynote)
* Looking for panelists, speakers.
* Expecting 200+ people on the Friday, (first day)

## Chris from OPIN:

* use deploy module (WillH interested in comparing notes)
* use Solr for enterprise search (WillR - govt moving to search.gc.ca for multisite search)
 - PeterL: is there a search API plugin? 
 - AndrewS: for now the Google Crawler is on autopilot; though Solr is good for facets, etc.
 - WillR: Solr will still be used for GETS tender search

## MikeG from OpenConcept:

* excited to be involved in U Ottawa
* City of Calgary is considering Drupal
* excited about D8 accessibility, new features; now is the time to contribute
 - try hosted D8 today: http://simplytest.me/
* Shared Services NEEDS TO BE offering SSH access to Drupal VMs; currently not
* SteveOTT: NCC is considering upgrading to D7

## Misc Conversation:

* (Nancy Gagnon from PCO): is there anyone at Treasury Board pushing Drupal? Is Interwoven the most likely choice in their eyes? This is 100% political.
 - AndrewS: not enough; StatsCan CIO will bring this up at CIOC
* Q(?): when is there a stable release for WET? That's our primary concern.
 - WillH: Sorry, need to get better at tagging. It's fairly stable now, and when when StatsCan launches next week, we'll tag.

## AndrewS's Presentation (slides by Acquia): Achieving Leaner, More Agile Government

* We'll get left behind if we dont act in the next month or two. 
* The first time CIOC heard about Drupal was this week.  
* There's a risk they will ignore the RFI and just renew.
* Chris(phone): why dont we go to CIOC about this? I got a big mouth, so I can help. Why is Corrine Charette just hearing about Drupal now? 
  - AndrewS: she needs to hear about it from TBS
  - Laurent (TBS): our intent was the RFI; Acquia presentation made a great impression, so that's a start.
  - RobinG: we need to get Modis + other big players to lobby as well. Govt worried about open source. Drupal cannot invoice the government.
  - AndrewS: these decisions are being made in the next few months. We've got to prove the business value to them.
*  Andrew ran through the 60 slides in 5 minutes. (will be distributed with minutes)
  - market size
  - google trends: Interwoven vs Drupal: http://dl-web.dropbox.com/u/29440342/screenshots/GPNYEP-2013.1.25-14.2.png
  - Acquia has a lot of momentum: #1 Forbes growing company
    - very flexible about their role 
  - 25% of US Gov sites on Drupal
    - FEMA consolidated 3 domains into 1 Drupal site
  - US Gov Distribution: Openpublic, US equivalent to WET Distro
  - WET distro
  - Drupal embraces and extends open data / open standards: AD, LDAP, XMLRPC, JSON, Shib, CMIS, RDF, etc.
    - proprietary CMS seek lock-in
    - MikeG: Drupal was the first CMS to implement RDFa.
  - embraces authoring, responsive design (even admin), analytics & search integration, multichannel publishing
  - Scalable:
    - LAMP is proven
    - Warner Music Group's managed Drupal cloud handled 90M requests per day
    - Al Jazeera blogs regularly handles 20M requests per day
  - Slide with Acquia Drupal stack 
    - WillH: make sure you also use APC, Varnish, Memcached ALWAYS
    - support hot failover, auto-scaling with peak load
    - leverages Amazon Web Services, so will need to replicate in Canada
  - Onboarding (migration challenges):
    - trusted codebase, 
    - CDN, 
    - determine load testing needs & metrics, 
    - load balancing w/o sticky sessions
    - memcache "& high performance object stores"
    - ESI & ajax caching support
    - Readslaves
    - site audit (by Acquia)
    - WillH: be sure to use the migrate module, covers 90% of use cases in a few days of work
  - Acquia has a 30+ person security team, SECURITY IS THE PRIMARY PRIORITY
    - NancyG (PCO): this is the biggest hurdle for management
    - AndrewS: StatsCan is currently carrying out a Drupal Threat-Risk-Assesment, will share
    - WillH: try NewRelic's security scan, free with Acquia subscription
    - MikeG: security needs a "belt and suspenders attitude"
* This slide deck will be distributed with minutes
* Q(?): How will several companies submit a bid for the RFI? Will Acquia help?
  - AndrewS: They can either joint bid or just sub to their partners. At this point I'm worried whether an RFI will go out; they might skip both RFI and RFP to meet "agressive timelines" and to avoid procurement delays. 
  - Chris(OPIN): private companies need to push for openness, via competition bureau.

Will Hearn: Update on StatsCan work on WET Distro

* removed "Default Content" module, replaced with Migrate module (please extend our migration code)
  - We import WET documentation as sample content, and clean it up
  - wetkit_migrate_link.inc fixes link URLs on import time; uses CSS3 selectors
  - supports Rollback & Import, etc.
* ctools widget to scrape external HTML pages & clean them up
  - cached locally
* Demo of caption file upload integration with WET HTML5 video player
* added l10n_update, l10n_client modules
  - Q:(NancyG,PCO): side-by-side editor support?
  - A: not integrated yet, but very close!
* added a11n tweaks to admin (En/Fr buttons)
* added path_breadcrumbs modules
* adding D8-style inline editing support, based on CKEditor
  - already have a patch for publishing workflow integration
* Testing: integrating with SauceLabs.com visual test builder
  - saucelabs.com is free if you're willing to open-source your tests
* Q: Any pre-built package plans?
  - need help with whitelist process for Drupal.org packaging process
  - current Chef build exists, but fairly minimal
  - Steve(OTT): Patrick Connolly / MyPlanetDigital is working on finding a SaaS provider, to replicate Acquia stack in Canada
  - Chris(OPIN): we're also working on that. 
  - WillRoboly: IRCAN/HRE is working on this too

AndrewS: how to increase collaboration (pull requests) on GitHub?

* Jacques Blier: move to drupal.org?
  - We will mirror on Drupal.org, maintain those issue queue too.
* MikeG: need to enact culture change about contribution, and dedicate resources
* Chris: concern about statscan vs WET dev priority
  - WillH: we actually have a sub-distro for statscan for custom modules; eg sub-theme
* Laurent: WET core has the same problem; 
  - TBS cant seem to get people to take over
  - Communication/docs needs to be improved:
    - people need to follow day-to-day project to contribute
    - nontechnical people can help here
* Steve(OTT): other govt distributions (agov, openplans) overlap; need to look outside the federal level
* Alex(EvolvingWeb): 
  - standard open-source problem
  - need to figure out a way to attract open-source competent developers; 
  - Laurent: just organized a code sprint
* How to learn how to lobby for Drupal?
  - RobinG: lobbying vs advocacy; need to register; takes money (eg GTEC)
  - AndrewS: how about getting testimonials about Interwoven satisfaction
  - Nancy Gagnon: 
    - I paid a consultant to study Interwoven satisfaction, can share
    - senior managers dont care about WET, they care about security vs open source
    - need to sell Drupal = security in their head!
  - Laurent: we want to be the good option, not the less bad option
  - Chris(OPIN): let's do a marketing committee
  - Joseph: there's an Interwoven WET group, actually. And Interwoven is here to stay, eg DFAIT is 100% microsoft.
  - WillH: when StatsCan launches, Drupal will be #1 CMS by content count
  - MikeG: microsoft sponsors Drupal, IBM sells it abroad; we should buy an ad in Govt executive newsletter
  - MikeG + Chris_OPIN will take initiative at starting mailing list for this marketing discussion

## Laurent on WET 3.1

* jQuery mobile for everything, to support touch events (see wet-core's experimental branch)
* overhauling examples HTML
* estimated to released around April
* upgrading to jQuery 2, separate IE7/IE8-specific code (via auto build)
* new WET theme ("neutral"), less GoC-specific look (not a base theme)

## Will Roboly on BAS
 - Buyandsell.gc.ca (BAS) is being audited for a11n, but it's a collection of sites so in QA limbo.
 - expect D7 upgrade to launch in March
 - March 2014 - tentatively releasing GETS on Drupal (MERX successor), already have a demo
 - Predated WET-DRUPAL but might re-architect to use it (new idea: no custom code!)
 - Our new model uses PhpQuery as a templating system to avoid hacking WET HTML at all. (jQuery style transforms)
 - MikeG: share some code dammit!

## Steve OTT wrapup:
 - next meeting: end of Feb/early march
 - we should consider using Google Groups for mailing list
 - Hope to see you at Drupalcamp
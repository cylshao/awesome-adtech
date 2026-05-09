# Awesome AdTech [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of high-signal resources for engineers building programmatic
> advertising systems — OpenRTB protocols, real-time bidders, SSPs, identity,
> privacy frameworks, auction theory, and the infrastructure that runs
> underneath all of it.

This list is opinionated toward the **engineering** side of AdTech: protocols,
reference implementations, infrastructure trade-offs, performance work, and
the deep-end of how DSPs, SSPs, and ad servers actually get built and operated
at production scale.

Maintained by [Charles](https://github.com/cylshao) — Engineering Lead
working on high-QPS DSPs and OpenRTB protocol stacks.

## Contents

- [Specifications & Standards](#specifications--standards)
- [Open-Source Bidders & Servers](#open-source-bidders--servers)
- [Header Bidding](#header-bidding)
- [DSP / SSP Architecture Reading](#dsp--ssp-architecture-reading)
- [Privacy & Consent](#privacy--consent)
- [Identity & Resolution](#identity--resolution)
- [Mobile In-App](#mobile-in-app)
- [CTV & OTT](#ctv--ott)
- [Programmatic OOH](#programmatic-ooh)
- [Audio Advertising](#audio-advertising)
- [Retail Media](#retail-media)
- [Verification, Brand Safety & IVT](#verification-brand-safety--ivt)
- [Auction Theory & Bidding Algorithms](#auction-theory--bidding-algorithms)
- [Pacing & Budget Distribution](#pacing--budget-distribution)
- [Storage & Real-Time Infrastructure](#storage--real-time-infrastructure)
- [Performance, Profiling & JVM](#performance-profiling--jvm)
- [Observability & Tracing](#observability--tracing)
- [Datasets & Research](#datasets--research)
- [News & Trade Publications](#news--trade-publications)
- [Newsletters](#newsletters)
- [Podcasts](#podcasts)
- [Conferences & Events](#conferences--events)
- [Communities & Forums](#communities--forums)
- [Books](#books)
- [Career & Hiring](#career--hiring)
- [Contributing](#contributing)
- [License](#license)

---

## Specifications & Standards

The foundational documents every AdTech engineer should keep on the desktop.

- [IAB Tech Lab](https://iabtechlab.com/) - The standards body behind OpenRTB, VAST, OMID, GPP, and most other AdTech specs.
- [OpenRTB Specs (GitHub)](https://github.com/InteractiveAdvertisingBureau/openrtb) - Canonical home of OpenRTB 2.x and 3.0 protocol drafts.
- [OpenRTB 2.6 Specification](https://iabtechlab.com/standards/openrtb/) - Latest published 2.x version with DOOH support, CTV pod bidding, and impression metrics.
- [OpenRTB 3.0 + AdCOM 1.0](https://github.com/InteractiveAdvertisingBureau/AdCOM) - Next-generation split between protocol (OpenRTB 3) and content model (AdCOM).
- [VAST 4.3](https://iabtechlab.com/standards/vast/) - Video Ad Serving Template, the lingua franca of video advertising.
- [SIMID 1.1](https://iabtechlab.com/standards/secure-interactive-media-interface-definition-simid/) - Modern replacement for VPAID; decouples interactivity from execution.
- [Open Measurement SDK (OMID)](https://iabtechlab.com/standards/open-measurement-sdk/) - Industry-standard viewability and verification SDK.
- [MRC Standards](https://www.mediaratingcouncil.org/standards) - Ad measurement standards every major buy-side and sell-side platform follows.
- [ads.txt / app-ads.txt](https://iabtechlab.com/ads-txt/) - Public records of authorized digital sellers.
- [ads.cert 2.0](https://iabtechlab.com/ads-cert/) - Cryptographic supply path authentication.
- [sellers.json](https://iabtechlab.com/sellers-json/) - Sell-side identity disclosure for supply-chain transparency.
- [Buyers.json](https://iabtechlab.com/buyers-json/) - Buy-side counterpart to sellers.json for DSP transparency.
- [SupplyChain Object](https://github.com/InteractiveAdvertisingBureau/openrtb/blob/master/supplychainobject.md) - Inventory provenance object passed inside OpenRTB requests.
- [DOOH OpenRTB Extensions](https://iabtechlab.com/wp-content/uploads/2022/04/OpenRTB-2-6_FINAL.pdf) - Imp object fields specific to digital out-of-home.
- [Audio OpenRTB Extensions](https://iabtechlab.com/standards/openrtb-for-audio/) - Audio-specific extensions on top of OpenRTB.
- [Open Programmatic Audio (OPA)](https://iabtechlab.com/standards/open-programmatic-audio/) - Audio ad delivery and measurement specs.
- [DAAST](https://iabtechlab.com/standards/digital-audio-ad-serving-template-daast/) - Digital Audio Ad Serving Template.
- [Pod Bidding](https://iabtechlab.com/standards/openrtb/) - OpenRTB extensions for CTV ad pod auctions.
- [Server-Guided Ad Insertion (SGAI)](https://iabtechlab.com/standards/server-guided-ad-insertion/) - The successor to client-side and server-side ad stitching.
- [Open RTB JSON Schema](https://github.com/prebid/openrtb) - Maintained JSON schemas for OpenRTB validation.
- [IAB Tech Lab Spider/Bot List](https://iabtechlab.com/standards/iab-tech-lab-spiders-and-bots/) - Industry list of known non-human user agents.
- [VPAID 2.0 (Deprecated)](https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf) - Historical reference; replaced by SIMID and OMID.

## Open-Source Bidders & Servers

Reference implementations, test harnesses, and production-ready stacks.

- [Prebid Server (Go)](https://github.com/prebid/prebid-server) - The most widely-deployed open-source server-side header-bidding implementation.
- [Prebid Server (Java)](https://github.com/prebid/prebid-server-java) - Java port maintained by Magnite, a great reference for OpenRTB on the JVM.
- [Prebid.js](https://github.com/prebid/Prebid.js) - Browser-side header-bidding library, the de facto industry standard.
- [Prebid Mobile iOS](https://github.com/prebid/prebid-mobile-ios) - In-app header-bidding SDK for iOS.
- [Prebid Mobile Android](https://github.com/prebid/prebid-mobile-android) - Android counterpart to the iOS SDK.
- [Prebid Universal Creative](https://github.com/prebid/prebid-universal-creative) - Render-time creative wrapper used in Prebid auctions.
- [Google OpenRTB Java SDK](https://github.com/google/openrtb) - Battle-tested OpenRTB protocol models in Java with JSON and Protobuf serializers.
- [RTB4Free](https://github.com/RTB4FREE/RTB4FREE) - Open-source RTB bidder originally seeded for educational use.
- [bsm/openrtb (Go)](https://github.com/bsm/openrtb) - Lean Go OpenRTB structs, useful for implementing bidders or fuzzers.
- [Magnite SpringServe](https://www.springserve.com/) - Open ad server / SSP for CTV and video.
- [Vapor](https://github.com/InteractiveAdvertisingBureau/openrtb) - Reference VAST parser for IAB.
- [VAST Parser (jeremyrosen/vast-tools)](https://github.com/wptd/vast-tools) - Lightweight VAST parser libraries for various languages.
- [OMID JS](https://github.com/InteractiveAdvertisingBureau/Open-Measurement-JSClients) - JavaScript client for the Open Measurement SDK.
- [OMID iOS / Android](https://github.com/InteractiveAdvertisingBureau/Open-Measurement-SDKs) - Native SDK reference implementations.

## Header Bidding

- [Prebid Documentation](https://docs.prebid.org/) - Canonical reference for both client-side and server-side Prebid.
- [Prebid Adapter Submission Guide](https://docs.prebid.org/dev-docs/bidder-adaptor.html) - Step-by-step on writing a bid adapter that gets merged.
- [Prebid Server Bidder Params](https://docs.prebid.org/dev-docs/pbs-bidders.html) - Server-side bidder parameter reference.
- [Prebid Auction Lifecycle](https://docs.prebid.org/prebid/prebidjs.html) - End-to-end overview of how a Prebid auction runs in the browser.
- [Header Bidding Wiki (AdMonsters)](https://www.admonsters.com/) - Glossary and explainers from the publisher-ops community.
- [Open Bidding (Google)](https://support.google.com/admanager/answer/7128453) - Google's exchange-to-exchange header bidding implementation.
- [Amazon TAM](https://aps.amazon.com/aps/transparent-ad-marketplace/) - Amazon's server-side header bidding wrapper.
- [Index Exchange Wrapper Solutions](https://www.indexexchange.com/products/wrapper-solution/) - One of the most-deployed alternative wrappers to Prebid.

## DSP / SSP Architecture Reading

- [Building a Real-Time Bidding System (Liftoff)](https://liftoff.io/blog/) - Liftoff's engineering blog covers bidder design from a mobile-DSP perspective.
- [Moloco Engineering Blog](https://www.moloco.com/blog) - Posts on ML-driven bidding and the operational reality of running a DSP.
- [Magnite Engineering](https://www.magnite.com/blog/) - Sell-side perspective from one of the largest independent SSPs.
- [PubMatic Blog](https://pubmatic.com/blog/) - SSP tech blog covering supply-side engineering.
- [Criteo Engineering](https://medium.com/criteo-engineering) - Heavy ML/retargeting content from a major retargeting platform.
- [Adikteev Engineering](https://medium.com/adikteev-engineering) - Mobile re-engagement DSP, posts on bidder internals.
- [Adjoe Engineering](https://medium.com/adjoe-engineering) - In-app advertising platform engineering posts.
- [The Trade Desk Tech](https://www.thetradedesk.com/us/news) - Press releases and occasional engineering announcements.
- [DoubleVerify Engineering](https://www.doubleverify.com/blog/) - Verification and measurement engineering posts.
- [HUMAN Security Research](https://www.humansecurity.com/learn) - Threat reports and case studies on bot traffic and ad fraud.
- [AppsFlyer Engineering](https://engineering.appsflyer.com/) - Mobile attribution and big-data infrastructure deep-dives.
- [Adjust Engineering](https://www.adjust.com/blog/category/engineering/) - Mobile attribution platform engineering content.
- [LiveRamp Engineering](https://liveramp.com/blog/) - Identity resolution, data clean room engineering.
- [Quantcast Engineering](https://www.quantcast.com/blog/) - Audience measurement and DSP engineering posts.
- [Xandr Engineering Archive](https://medium.com/xandr-tech) - Historical posts from when Xandr was independent (acquired by Microsoft).

## Privacy & Consent

- [IAB Europe TCF 2.2](https://iabeurope.eu/transparency-consent-framework/) - Dominant consent framework for EEA traffic.
- [TCF 2.x GitHub](https://github.com/InteractiveAdvertisingBureau/GDPR-Transparency-and-Consent-Framework) - Source of truth for the spec, vendor list, and CMP API.
- [TCF Vendor List](https://vendor-list.consensu.org/v3/vendor-list.json) - Live JSON of registered TCF 2.2 vendors.
- [IAB Global Privacy Platform (GPP)](https://github.com/InteractiveAdvertisingBureau/Global-Privacy-Platform) - Multi-jurisdiction successor that bundles TCF, USP, and US state signals.
- [GPP String Encoder](https://iabgpp.com/) - Online tool for inspecting and encoding GPP strings.
- [Privacy Sandbox](https://privacysandbox.com/) - Google's umbrella initiative for cookieless advertising on Chrome.
- [Topics API](https://developer.chrome.com/docs/privacy-sandbox/topics/) - Browser-native interest-based advertising replacement for third-party cookies.
- [Protected Audience API](https://developer.chrome.com/docs/privacy-sandbox/protected-audience/) - On-device retargeting (formerly FLEDGE).
- [Attribution Reporting API](https://developer.chrome.com/docs/privacy-sandbox/attribution-reporting/) - Privacy-preserving conversion measurement.
- [Private Aggregation API](https://developer.chrome.com/docs/privacy-sandbox/private-aggregation/) - Differential-privacy-style aggregation for cross-site measurement.
- [Fenced Frames](https://developer.chrome.com/docs/privacy-sandbox/fenced-frame/) - Sandboxed iframes used by Protected Audience.
- [Storage Access API](https://developer.chrome.com/docs/privacy-sandbox/storage-access/) - Controlled access to cross-site storage.
- [Related Website Sets](https://developer.chrome.com/docs/privacy-sandbox/related-website-sets/) - First-party set successor for cross-domain functionality.
- [App Tracking Transparency (Apple)](https://developer.apple.com/documentation/apptrackingtransparency) - Source of truth for iOS ATT.
- [Apple Privacy Manifests](https://developer.apple.com/documentation/bundleresources/privacy_manifest_files) - Required disclosure files for SDKs collecting data.
- [California Privacy Protection Agency](https://cppa.ca.gov/) - CPPA, regulator for CCPA/CPRA enforcement.
- [Virginia VCDPA Reference](https://law.lis.virginia.gov/vacodefull/title59.1/chapter53/) - Virginia Consumer Data Protection Act statute.
- [Privacy Sandbox Status (Chromium)](https://www.chromium.org/Home/chromium-privacy/privacy-sandbox/) - Engineering-side launch status of each Sandbox API.
- [Mozilla Anti-Tracking Policy](https://wiki.mozilla.org/Security/Anti_tracking_policy) - Firefox's reference policy that drives ETP behavior.
- [Safari Privacy](https://webkit.org/tracking-prevention/) - WebKit ITP and tracking prevention engineering documentation.
- [DSAR Tooling (OneTrust)](https://www.onetrust.com/) - One of the dominant CMPs and privacy-rights workflow vendors.
- [Didomi Developer Docs](https://developers.didomi.io/cmp/web-sdk) - CMP integration reference, Europe-focused.

## Identity & Resolution

- [Unified ID 2.0 (IAB Tech Lab)](https://github.com/IABTechLab/uid2-docs) - Open-source deterministic ID built on hashed emails.
- [UID 2.0 Operator Source](https://github.com/IABTechLab/uid2-operator) - Reference operator implementation for UID2.
- [ID5](https://docs.id5.io/) - Cookieless probabilistic + deterministic ID with broad SSP coverage.
- [LiveRamp RampID](https://docs.liveramp.com/identity/en/welcome-to-rampid.html) - People-based identity graph used heavily in CRM-driven verticals.
- [LiveRamp ATS](https://liveramp.com/our-platform/authenticated-traffic-solution/) - Authenticated traffic solution for first-party identity activation.
- [The Trade Desk OpenPath](https://www.thetradedesk.com/us/news/openpath) - TTD's direct supply path initiative.
- [The Trade Desk Galileo](https://www.thetradedesk.com/) - First-party data activation product layered on UID2.
- [Permutive](https://docs.permutive.com/) - Cohort-based first-party data activation platform.
- [Adstra](https://www.adstra.com/) - Identity graph vendor focused on people-based marketing.
- [Lotame Panorama ID](https://www.lotame.com/panorama/) - Cookieless cross-channel identity solution.
- [Criteo Identity](https://www.criteo.com/identity/) - Criteo's first-party identity strategy post-cookie deprecation.
- [Yahoo ConnectID](https://www.yahooinc.com/data/connectid/) - Yahoo's authenticated email-based identity solution.

## Mobile In-App

- [Apple SKAdNetwork](https://developer.apple.com/documentation/storekit/skadnetwork) - Apple's privacy-preserving install attribution framework.
- [SKAdNetwork 4.0 (Apple)](https://developer.apple.com/documentation/storekit/skadnetwork/skadnetwork_release_notes/skadnetwork_4_release_notes) - SKAN 4 release notes covering hierarchical conversion values.
- [SKAN 4.0 Postback Mapping (AppsFlyer)](https://www.appsflyer.com/resources/guides/skadnetwork-skan/) - Practical engineer-grade overview of SKAN postbacks.
- [Apple AdAttributionKit](https://developer.apple.com/documentation/adattributionkit) - SKAN's successor for App Store and re-engagement attribution.
- [AppsFlyer Developer Hub](https://dev.appsflyer.com/) - One of the two dominant MMP SDKs and APIs.
- [Adjust Developer Docs](https://dev.adjust.com/) - The other dominant MMP, with strong CTV/OTT measurement support.
- [Branch Documentation](https://help.branch.io/developers-hub) - Deep-link plus attribution platform.
- [Singular Documentation](https://support.singular.net/) - Marketing analytics and attribution platform.
- [Kochava Developer Hub](https://support.kochava.com/) - Mobile measurement platform with cross-device support.
- [Google Play Install Referrer](https://developer.android.com/google/play/installreferrer) - Android-side install referral source.
- [Google Privacy Sandbox on Android](https://developer.android.com/privacy-sandbox) - Topics, Attribution Reporting, and SDK Runtime APIs for Android.
- [Android Advertising ID Reset](https://support.google.com/googleplay/android-developer/answer/6048248) - Policy and behavior reference for AAID.

## CTV & OTT

- [IAB Tech Lab Digital Video Suite](https://iabtechlab.com/standards/digital-video-suite/) - VAST, SIMID, OMID, SGAI, and pod bidding under one umbrella.
- [Server-Guided Ad Insertion (SGAI)](https://iabtechlab.com/standards/server-guided-ad-insertion/) - The successor to client-side and server-side ad stitching.
- [OpenRTB CTV Extensions](https://iabtechlab.com/standards/openrtb/) - Pod bidding fields, content categories, and connected-TV-specific signals.
- [Innovid CTV Resources](https://www.innovid.com/) - Resources from one of the dominant CTV ad servers.
- [SpringServe](https://www.springserve.com/) - CTV and video ad server with public engineering content.
- [FreeWheel Documentation](https://docs.freewheel.com/) - Comcast's ad-management and SSI platform.
- [Roku Ads Manager](https://advertising.roku.com/) - Roku's CTV ad platform documentation.
- [Samba TV ACR](https://www.sambatv.com/) - Automatic content recognition for CTV measurement.
- [VIZIO Inscape](https://www.vizio.com/inscape) - VIZIO's smart-TV data and measurement platform.
- [Conviva](https://www.conviva.com/) - Streaming-quality and ad measurement platform.

## Programmatic OOH

- [Place Exchange](https://www.placeexchange.com/) - Programmatic OOH marketplace with public DOOH OpenRTB extensions.
- [Vistar Media](https://www.vistarmedia.com/) - DOOH SSP with public engineering blog content.
- [VIOOH](https://www.viooh.com/) - JCDecaux-backed DOOH platform.
- [Hivestack](https://hivestack.com/) - Programmatic DOOH platform acquired by Perion.
- [DPAA](https://www.dpaaorg.com/) - Industry association for digital OOH.

## Audio Advertising

- [IAB Open Programmatic Audio](https://iabtechlab.com/standards/open-programmatic-audio/) - Audio ad delivery and measurement specs.
- [DAAST](https://iabtechlab.com/standards/digital-audio-ad-serving-template-daast/) - Digital Audio Ad Serving Template.
- [Spotify Ad Studio](https://adstudio.spotify.com/) - Spotify's self-serve audio ad platform.
- [Triton Digital](https://www.tritondigital.com/) - Audio measurement and ad serving for podcast and radio.
- [Megaphone](https://megaphone.fm/) - Spotify-owned podcast platform with programmatic audio integration.

## Retail Media

- [Amazon Advertising API](https://advertising.amazon.com/API/docs/en-us/) - Amazon Ads sponsored products / sponsored brands API.
- [Amazon DSP](https://advertising.amazon.com/solutions/products/amazon-dsp) - Amazon's demand-side platform.
- [Amazon Marketing Cloud](https://advertising.amazon.com/solutions/products/amazon-marketing-cloud) - Clean-room analytics layer over Amazon Ads.
- [Walmart Connect](https://advertising.walmart.com/) - Walmart's retail media network.
- [Criteo Retail Media](https://www.criteo.com/products/retail-media/) - Criteo's retail media offering across multiple retailers.
- [Pacvue](https://www.pacvue.com/) - Retail media optimization platform across Amazon, Walmart, and others.
- [Skai (formerly Kenshoo)](https://skai.io/) - Cross-channel digital marketing platform with retail media focus.
- [IAB Retail Media Guidance](https://www.iab.com/insights/retail-media-network-buyers-guide/) - Industry buyer's guide for retail media networks.

## Verification, Brand Safety & IVT

- [MRC Standards](https://www.mediaratingcouncil.org/standards) - Industry definitions for sophisticated invalid traffic and viewability.
- [HUMAN Security Research](https://www.humansecurity.com/learn) - Threat reports and case studies on bot traffic and ad fraud.
- [DoubleVerify Knowledge Base](https://docs.doubleverify.com/) - DV's measurement and brand-safety APIs.
- [DoubleVerify Authentic Ad](https://www.doubleverify.com/) - Reference for verification methodology.
- [IAS Insider](https://integralads.com/insider/) - IAS's research blog with verification deep-dives.
- [Pixalate Insights](https://www.pixalate.com/insights) - Trust-and-safety research, IVT detection.
- [Adloox](https://www.adloox.com/) - Verification provider with European focus.
- [Moat by Oracle](https://moat.com/) - Viewability and analytics, now sunset but still referenced.
- [GARM Brand Safety Floor](https://wfanet.org/leadership/garm) - Global Alliance for Responsible Media's brand safety taxonomy.
- [TAG (Trustworthy Accountability Group)](https://www.tagtoday.net/) - Anti-fraud and brand safety industry program.
- [ads.cert 2.0](https://iabtechlab.com/ads-cert/) - Cryptographic supply path authentication.
- [Bitdefender Adversarial Lab](https://www.bitdefender.com/blog/labs/) - Threat research relevant to ad-fraud botnet analysis.

## Auction Theory & Bidding Algorithms

- [Vickrey Auction (Original Paper)](https://www.jstor.org/stable/2977633) - Counterspeculation, Auctions, and Competitive Sealed Tenders (1961).
- [GSP Auction Paper (Edelman, Ostrovsky, Schwarz)](https://www.benedelman.org/publications/gsp-060801.pdf) - Internet advertising and the generalized second-price auction.
- [First-Price Auctions in Display (Google Research)](https://research.google/pubs/pub45822/) - Bidding economics under first-price across exchanges.
- [Bid Shading via Win-Rate Estimation (arXiv)](https://arxiv.org/abs/1901.10822) - Practical bid shading framework.
- [Optimal No-Regret Learning in Repeated First-Price Auctions](https://arxiv.org/abs/2003.09795) - Theoretical foundations for online bid shading.
- [Bid Shading in The Brave New World of First-Price Auctions](https://arxiv.org/abs/1909.04839) - Engineering-grade overview of bid-shading models.
- [A Practical Guide to Bid Shading (Beeswax / FreeWheel)](https://www.freewheel.com/) - Vendor-published primers on bid shading approaches.
- [Real-Time Bidding by Reinforcement Learning](https://arxiv.org/abs/1610.05096) - RL applied to RTB bidder design.
- [Display Advertising with Real-Time Bidding (Wang, Zhang, Yuan)](https://arxiv.org/abs/1610.03013) - Comprehensive survey paper on RTB.
- [Programmatic Auction Mechanics (Adservers.org)](http://adservers.org/) - Educational walkthrough of auction internals.

## Pacing & Budget Distribution

- [Smart Pacing for Display Advertising (Yahoo Research)](https://research.yahoo.com/publications/8722/smart-pacing-display-advertising-real-time-bidding) - Foundational pacing paper.
- [Budget Pacing for Targeted Online Advertising at LinkedIn](https://www.kdd.org/kdd2017/papers/view/budget-pacing-for-targeted-online-advertisements-at-linkedin) - Production pacing system at scale.
- [Optimal Bidding, Allocation and Budget Spending for a Demand Side Platform with Generic Auction Type](https://arxiv.org/abs/1908.01506) - Joint optimization of pacing and bidding.
- [PID Controllers in Ad Pacing (StackOverflow Discussion)](https://stackoverflow.com/questions/tagged/pid-controller) - Background reading on PID, the algorithm class behind most pacing implementations.
- [Liftoff Engineering on Pacing](https://liftoff.io/blog/) - Mobile-DSP-side blog posts on pacing and frequency capping in production.

## Storage & Real-Time Infrastructure

The infrastructure layer that bidders, pacing engines, and event pipelines actually run on.

- [Aerospike Documentation](https://aerospike.com/docs/) - Most common hot-storage choice for user-profile lookup at 100K+ QPS.
- [Aerospike AdTech Use Cases](https://aerospike.com/use-cases/adtech/) - Vendor-published reference patterns for DSP and DMP profile stores.
- [Aerospike vs Redis Benchmark](https://aerospike.com/blog/) - Vendor benchmarks (read with skepticism, but useful baselines).
- [ScyllaDB](https://www.scylladb.com/) - Cassandra-compatible NoSQL with low-latency C++ runtime, used in some bidders.
- [Apache Cassandra](https://cassandra.apache.org/doc/latest/) - Eventually-consistent NoSQL still common in DMP/CDP stacks.
- [ClickHouse](https://clickhouse.com/docs) - Columnar OLAP database used heavily for AdTech reporting and analytics.
- [Apache Druid](https://druid.apache.org/docs/latest/) - Real-time time-series database, the historic AdTech analytics workhorse.
- [Apache Pinot](https://docs.pinot.apache.org/) - LinkedIn-bred competitor to Druid for ad-hoc OLAP at scale.
- [Apache Kafka](https://kafka.apache.org/documentation/) - Event backbone for impression, click, and bid logs.
- [Apache Pulsar](https://pulsar.apache.org/docs/) - Multi-tenant messaging system used as Kafka alternative.
- [Apache Flink](https://flink.apache.org/) - Common stream-processing engine for real-time pacing and frequency capping.
- [Apache Spark Streaming](https://spark.apache.org/docs/latest/streaming-programming-guide.html) - Heavier-weight alternative for batch-leaning streaming workloads.
- [Redis](https://redis.io/docs/) - Frequency caps, rate limits, deduplication, and small-payload hot lookups.
- [Redis Bloom](https://redis.io/docs/data-types/probabilistic/) - Bloom filters and HyperLogLog for cardinality estimation.
- [Memcached](https://memcached.org/) - Simple distributed cache, still common in bidders for hot lookups.
- [DynamoDB](https://docs.aws.amazon.com/dynamodb/) - Managed key-value store, used by AdTech teams to avoid operating Aerospike.
- [Amazon S3](https://docs.aws.amazon.com/s3/) - Cold storage for bid logs and event archives.

## Performance, Profiling & JVM

- [Async Profiler](https://github.com/async-profiler/async-profiler) - The JVM profiler of choice when chasing sub-50ms p99 latency in bidders.
- [JMH](https://github.com/openjdk/jmh) - Java Microbenchmark Harness, essential for proving any latency claim.
- [JFR (Java Flight Recorder)](https://docs.oracle.com/en/java/javase/21/jfapi/) - Built-in low-overhead profiling and event recording.
- [JITWatch](https://github.com/AdoptOpenJDK/jitwatch) - Visualize HotSpot JIT compilation decisions.
- [GC Easy](https://gceasy.io/) - GC log analysis tool, useful for tuning bidder JVMs.
- [Aleksey Shipilëv's Talks](https://shipilev.net/) - Definitive content on JVM performance and concurrency.
- [Brendan Gregg's Performance Tools](https://www.brendangregg.com/linuxperf.html) - Linux performance toolkit reference, applicable to any high-QPS service.
- [USE Method](https://www.brendangregg.com/usemethod.html) - Utilization, Saturation, Errors performance methodology.
- [Mechanical Sympathy Blog](https://mechanical-sympathy.blogspot.com/) - Martin Thompson's posts on low-latency JVM design.
- [Disruptor Pattern](https://lmax-exchange.github.io/disruptor/) - High-throughput inter-thread messaging library, used in some bidders.

## Observability & Tracing

- [OpenTelemetry](https://opentelemetry.io/docs/) - Vendor-neutral standard for traces, metrics, and logs.
- [Prometheus](https://prometheus.io/docs/) - Time-series database and metrics format, near-universal in modern bidders.
- [Grafana](https://grafana.com/docs/) - Dashboarding layer over Prometheus and other data sources.
- [Jaeger](https://www.jaegertracing.io/docs/) - Distributed tracing system, originally from Uber.
- [Zipkin](https://zipkin.io/) - Twitter-originated distributed tracing system.
- [VictoriaMetrics](https://docs.victoriametrics.com/) - Prometheus-compatible TSDB optimized for high cardinality.
- [Loki](https://grafana.com/docs/loki/latest/) - Log aggregation system, Grafana-native.
- [eBPF.io](https://ebpf.io/) - Reference for eBPF-based observability tooling.

## Datasets & Research

- [iPinYou RTB Dataset](https://contest.ipinyou.com/) - Public dataset of real bid logs, widely used in academic CTR/RTB papers.
- [Criteo Display Advertising Challenge](https://www.kaggle.com/c/criteo-display-ad-challenge) - Public CTR prediction dataset on Kaggle.
- [Criteo 1TB Click Logs](https://ailab.criteo.com/download-criteo-1tb-click-logs-dataset/) - 1TB dataset of display ad click logs.
- [Avazu CTR Prediction](https://www.kaggle.com/c/avazu-ctr-prediction) - Mobile ad CTR dataset, smaller than Criteo's.
- [Outbrain Click Prediction](https://www.kaggle.com/c/outbrain-click-prediction) - Native ad recommendation dataset.
- [TenRec](https://github.com/yuangh-x/2022-NIPS-Tenrec) - Tencent recommendation dataset, useful for ML benchmarking.
- [arXiv cs.IR](https://arxiv.org/list/cs.IR/recent) - Information retrieval section of arXiv, where most CTR / bidding papers appear.
- [KDD Cup Archives](https://www.kdd.org/kdd-cup) - Historic competition datasets, several AdTech-relevant.

## News & Trade Publications

- [AdExchanger](https://www.adexchanger.com/) - The trade publication of record for programmatic advertising.
- [Digiday](https://digiday.com/) - Broader media plus AdTech coverage with strong investigative pieces.
- [AdAge](https://adage.com/) - Long-running advertising trade publication with AdTech beat.
- [AdWeek](https://www.adweek.com/) - Broad advertising industry news with regular AdTech coverage.
- [Campaign](https://www.campaignlive.com/) - UK-rooted publication with strong European AdTech coverage.
- [The Drum](https://www.thedrum.com/) - European marketing and AdTech news.
- [PPC Land](https://ppc.land/) - Daily AdTech news with strong policy and regulation coverage.
- [Marketing Brew](https://www.morningbrew.com/marketing) - Morning Brew's marketing newsletter and site.
- [ExchangeWire](https://www.exchangewire.com/) - European AdTech industry news.
- [Marketing Land](https://martech.org/) - MarTech.org, broader marketing technology coverage.
- [Mobile Dev Memo](https://mobiledevmemo.com/) - Eric Seufert's site and podcast on mobile growth and ad markets.
- [Ad Ops Insider](https://www.adopsinsider.com/) - Ben Kneen's blog with operational tutorials and primers.

## Newsletters

- [Marketecture](https://www.marketecture.tv/) - Ari Paparo's podcast and newsletter, very engineer-friendly.
- [Beeler.Tech](https://www.beeler.tech/) - Rob Beeler's newsletter and consultant network for ad operations.
- [The Rebooting](https://www.therebooting.com/) - Brian Morrissey's newsletter on the business of media and programmatic.
- [Quo Vadis (Tom Triscari)](https://lemonade-projects.com/) - Long-form essays on programmatic economics.
- [Mobile Dev Memo Newsletter](https://mobiledevmemo.com/subscribe/) - Eric Seufert's weekly newsletter on mobile growth.
- [Heavybit AdTech Letter](https://www.heavybit.com/library) - Sporadic but high-quality AdTech operator content.
- [Garbage Day](https://www.garbageday.email/) - Internet culture newsletter; surprisingly good on advertising's social impact.
- [Platformer](https://www.platformer.news/) - Platform policy newsletter relevant to ad regulation.

## Podcasts

- [Marketecture Podcast](https://www.marketecture.tv/podcast) - Weekly interviews with AdTech operators.
- [Mobile Dev Memo Podcast](https://mobiledevmemo.com/podcast/) - Mobile attribution, gaming, growth marketing.
- [The AdTech Podcast](https://podcasts.apple.com/us/podcast/the-adtech-podcast/id1460770388) - General-interest AdTech interview show.
- [Programmatic Mob](https://podcasts.apple.com/us/podcast/the-programmatic-mob-podcast/id1530625011) - DSP-focused operator interviews.
- [Two Brews and a Bid](https://twobrewsandabid.com/) - AdTech / programmatic chat with industry guests.
- [Acquired](https://www.acquired.fm/) - Not AdTech-only, but has excellent deep-dives on Google, Meta, TTD, AppLovin.
- [The Recode Decode (archive)](https://www.vox.com/recode-podcasts) - Historical episodes with key AdTech founders.
- [Hot Pod](https://www.hotpodnews.com/) - Podcast industry newsletter, relevant for audio advertising.

## Conferences & Events

- [Programmatic I/O](https://digiday.com/programmatic-io/) - Digiday's flagship programmatic event in NYC and Las Vegas.
- [AdMonsters Publisher Forum](https://www.admonsters.com/events/) - Invite-only ops-focused conference series.
- [dmexco](https://dmexco.com/) - Largest European digital marketing event, held annually in Cologne.
- [IAB Annual Leadership Meeting (ALM)](https://www.iab.com/events/) - The annual standards and policy gathering.
- [IAB Tech Lab Summit](https://iabtechlab.com/) - Engineering-side IAB event focused on standards work.
- [Cannes Lions](https://www.canneslions.com/) - The main brand-side global event with growing AdTech presence.
- [AppsFlyer MAMA](https://www.appsflyer.com/mama/) - Mobile-attribution-focused conference series.
- [AdExchanger Industry Preview](https://www.adexchanger.com/events/) - AdExchanger's annual industry kickoff event.
- [Digiday Publishing Summit](https://digiday.com/events/) - Publisher-focused complement to Programmatic I/O.
- [Cynopsis Measurement Conference](https://www.cynopsis.com/events/) - Measurement-focused industry event.

## Communities & Forums

- [r/adops](https://www.reddit.com/r/adops/) - Reddit community for ad operations and AdTech engineers.
- [r/programmatic](https://www.reddit.com/r/programmatic/) - More buyer/trader-leaning subreddit.
- [AdMonsters Slack](https://www.admonsters.com/) - Invite-only Slack for AdMonsters members.
- [Beeler.Tech Network](https://www.beeler.tech/network) - Independent AdTech consultant network.
- [Prebid Slack](https://prebid.slack.com/) - Open Slack workspace for Prebid contributors and users.
- [IAB Tech Lab Working Groups](https://iabtechlab.com/working-groups/) - Specification working groups; engineers can join.
- [LinkedIn AdTech Engineers Group](https://www.linkedin.com/groups/) - Several active LinkedIn groups, search "AdTech".
- [The Trade Desk Edge Academy](https://academy.thetradedesk.com/) - Free training and certification, useful even outside TTD.

## Books

- [The AdTech Book (ClearCode)](https://clearcode.cc/the-adtech-book/) - Free online book; the single best plain-English overview of how AdTech works.
- [Targeted by Mike Smith](https://www.amazon.com/Targeted-Programmatic-Advertising-Conquered-Reshaping/dp/0814433413) - History of how programmatic conquered display advertising.
- [Ad Serving Technology by Gregory Cristal](https://www.amazon.com/Ad-Serving-Technology-Gregory-Cristal/dp/1481947370) - Technical reference covering ad servers, exchanges, and DSPs.
- [Subprime Attention Crisis by Tim Hwang](https://us.macmillan.com/books/9780374538651/subprimeattentioncrisis) - Critical examination of programmatic advertising as a financial market.
- [The Attention Merchants by Tim Wu](https://www.penguinrandomhouse.com/books/231552/the-attention-merchants-by-tim-wu/) - History of attention-based business models.
- [Confessions of the Pricing Man by Hermann Simon](https://www.amazon.com/Confessions-Pricing-Man-Affects-Everything/dp/3319204998) - Not AdTech-specific but essential for anyone working on auction or pricing logic.
- [Designing Data-Intensive Applications by Martin Kleppmann](https://dataintensive.net/) - Mandatory reading for any backend engineer working on ad infrastructure.
- [The Almanack of Naval Ravikant](https://www.navalmanack.com/) - Tangential, but useful framing for engineers thinking about specialization and leverage.

## Career & Hiring

- [AdMonsters Job Board](https://www.admonsters.com/jobs/) - AdTech-specific job listings, US-leaning.
- [Beeler.Tech Job Board](https://www.beeler.tech/jobs) - Curated AdTech operator and engineering roles.
- [LinkedIn AdTech Filter](https://www.linkedin.com/jobs/) - Use "OpenRTB" or "DSP" as search terms.
- [Digiday Worklife](https://digiday.com/category/worklife/) - Career-focused content for AdTech professionals.
- [Levels.fyi AdTech Companies](https://www.levels.fyi/) - Compensation transparency for many AdTech employers.

## Contributing

Pull requests welcome. To suggest a resource:

1. Open an issue describing the resource and which category it belongs in.
2. Make sure the link is **stable** — no marketing landing pages, no link rot, no paywalls without preview.
3. Keep descriptions to **one factual sentence** — no superlatives, no opinion.
4. Submit a PR. Items in each category are alphabetized where practical.

## Maintainer

Maintained by **[Charles](https://github.com/cylshao)** — AdTech
Engineering Lead specializing in OpenRTB-based DSPs, JVM bidder tuning, and
high-QPS auction systems. Connect on
[LinkedIn](https://www.linkedin.com/in/cylshao) or
[book a call](https://calendly.com/cylshao).

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the maintainer has waived all copyright and
related or neighboring rights to this work.

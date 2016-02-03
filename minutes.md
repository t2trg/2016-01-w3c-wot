# T2TRG WoT Eurecom 2016 notes

## Tuesday, 26 Jan 2016

### 9:00 Welcome

* Welcome by Ulrich Finger of EURECOM
* Jörg Heuer continued with background and current work of WoT.
   * Interoperability and silo problem
   * Atomic use cases
   * WoT building blocks
   * Work so far
   * Upcoming
   * Today's agenda
* Carsten Bormann introduces T2TRG joint activity
   * Note well
   * IRTF
   * T2TRG focus
   * Previous meetings
   * W3C connection
   * Detailed activities
   * Next meetings
      * 15th and 16th of March (adjacent to IAB WS on semantic interop)
      * Summary meeting at Buenos Aires IETF meeting

### 9:36 Contributions

* Johannes Hund
   * WoT is about simplicity
   * Implementations vs standards
   * Kickoff in Berlin (findings)
   * TPAC in Santa Clara (patterns)
   * F2F in Munich (building blocks)
   * F2F in Sunnyvale (model)
   * TPAC in Sapporo (first plugfest)
   * F2F in Nice (ideas on how to continue: running code, technical spec that is not a standard)
* Jörg reminded that we should think how do we best capture the learnings from the plugfests
* Dave Raggett 
   * Robot videos (instead of cats :P)
   * Manufacturing
   * Robots and humans working together
   * Model-based techniques in automation
   * Web technologies can be used to bridge these technologies
   * Industrie 4.0
   * The Industrie 4.0 model has lots of commonalities with the models discussed in WoT
   * Apps model for manufacturing
   * Automatic contract negotiation
   * Next steps: group focused on smart manufacturing?
   * Questions:
      * Claes Nilsson: Existing Web-based systems running today?
      * Dave: Fairly new area. Anybody from the audience? No response
      * Joerg: we need commonalities and common building blocks
      * Dave: atomic use cases e.g. dealing with real-time requirements. Need to bring people together to work on this. 
      * There are different levels of e.g., real-time requirements, from microseconds to seconds.
      * Cerif Tahar: which type of industry is thinked as use cases?
      * Dave: need to be pragmatic. Depends on what people can be brought together. Should not throw out old techs.
      * Cerif: is the idea to bring the techs to WoT?
      * Dave: remains to be seen. Trying to reach out to communities.
* Soumya
   * Moving towards data-driven architecture
   * Map real components to WoT architecture
   * Connected vehicle scenario: sensors in vehicles and onboard system
   * Communicate sensor readings to Road Side Unit (~1 km connection radius) and to android app via M2MGW.
   * Question: ??1. how are thing descriptions used?
      * Describing the vehicle as a resource. Sensors and actuators. Initially using IPSO alliance objects and CoRE weblinks. Now moving towards JSON-LD.
   * Architecture actually implemented and demo shown later today
   * Questions
      * Kazuaki: Participate in “automotive work group”?
      * Soumya: Aware but not really associated
      * Kaz: staff contact for automotive group; happy to help
      * Joerg: Smartphone interaction with resources as virtual instance of car. Do you see use cases that do not involve phones (i.e., users)
      * Soumya: T2T logic, e.g., opening garage doors, new sensors ordered
      * Kaz: Automotive group working on APIs. What features can be made available, e.g., nav data, speed? Can be dangerous to interfere.

### 11:35 Contributions

* Victor
   * resource based uRDF. Small footprint RDF for IoT/WoT.
   * Demo later
   * Questions:
      * Dave: Thought about using RDF graphs?
      * Victor: No. Each thing would have its own graph, also hard for constrained devices
      * Dave: maybe closed-world model graphs can help
      * Joerg: Often processing capabilities are a problem (not only memory). Evaluated?
      * Victor: Not done yet
      * Jörg: consider making scenario description with this for plugfest activities?
      * Victor: Siemens will have smart offices soon. Could be done in that context.
      * Joerg: Could be used to get different implementations for the occupancy use case.
* Louay
   * Thing API in Web view for HomeKit
   * Connection through bridge on smartphone
   * Thing API proposal as WebIDL on GitHub
   * Needs discussion in the Thing API breakout
   * Short demo with temperature and door sensor
   * Web server on phone can connect remote parties to local HomeKit devices
   * Questions:
      * ?: WebIDL is not targeting JavaScript, rather JavaScript in Web browsers. Also a problem with Node.js. How is this implemented?
      * Louay: Phone caches device properties and has standing connection to Node.js server.
      * ?: Standardization perspective with regard to the sensor API for Web browsers. Observer pattern in JS was an issue. Did you experience the same?
      * Louay: not for now.
      * Johannes: Implemented this on Nashorn and experienced a problem with Promises. There should be basic requirements on the runtime and then make it even language-independent.
      * Dave: This is what I mean by the Thing layer
* Joerg: Use the lunch break to set up your demo in the designated room. Not much time in the afternoon.

### 12:14 Lunch -- Return 13:30

### 13:40 Contributions

* Matthias Kovatsch: [Overview of HATEOAS approaches](https://github.com/t2trg/2016-01-w3c-wot/raw/master/slides/08-2016_HATEOAS_Overview.pdf)
   * How things can adapt to changing environments (in APIs)
   * Function descriptions are in-band: links and forms
   * Clients can learn apps on the fly
   * Servers free to define own resource structure and dynamically add features
   * PlugREST exercise as practical approach. Lightning use case. How can new light types be controlled with old controllers and old lights with new controllers?
   * Two drafts from Klaus Hartke about Hypertext driven apps and the lightning use case
      * [https://tools.ietf.org/html/draft-hartke-core-apps-02]
      * [https://tools.ietf.org/html/draft-hartke-core-lighting-00]
   * Matthias's approach
      * CoRE-HAL media type and application-specific media types
      * Hypermedia Client, a machine client using Futures to navigate through application space
      * Uses link relation types to find right context and achieve programmed goal
   * Questions:
      * Sebastian: where does information what links to follow come from?
      * Matthias: part of basic vocabulary of the application. The vocabulary is decoupled from URIs. 
      * Viktor: any estimate on the number of relations?
      * Matthias: 10-20 range for the lightning use case. 
      * Viktor: need some classification of resources. Where would fit in HATEOAS approach?
      * Matthias: when entering context, you learn more by following links
      * Viktor: need abstraction layers for complex apps. One abstraction may not fit. Usually done using classes not relations. Can we do reasoning in HATEOAS?
      * Dave: relations and RDF linked data and data platform? w3c has done work on link data platform last year. Should have discussion how things fit together.
      * Matthias: functional description is often missing in semantic model; how to use
      * Dave: that’s what platform is about. Could be strong connection between these works.
      * Jörg: expect this work to continue. Want to see the approaches together.
    * Michael’s appraoch
      * Common CRUD model for protocol bindings
      * Collection based media type + SenML + Link-Format
      * Thing Object Model to provide API for scripting
      * Also includes domain models etc. to generate resources in common server implementation
      * Questions
         * Kazuaki: how is security handled?
         * Matthias:For security tokens can be used. When server sees client is authorized, can provide forms etc.
         * Carsten: the security modulates what forms are provided. Server provides client the links it is supposed to access (also needs to do enforcement).

* Omar Elloumi  & Martin Bauer: [OneM2M](https://www.w3.org/WoT/IG/wiki/File:OneM2M-for-W3C_jan_26th_2016_OELLOUMI_MBAUER.pdf)
    * See lot of potential in semantic technologies for IoT
    * There is need for understanding business, educating engineers, etc.
    * Looking forward to collaboration
    * Semantics is new feature in oneM2M rel 2
    * Semantic descriptor resource type for annotation
    * Base ontology has things, devices, operational aspects, and semantics
    * Questions
      * Claes: is this intended to be implemented in cloud services? How does deployment look like? Any existing implementations?
      * Martin: Some commercial, there are also open source implementations, e.g., om2m
      * Jörg: are the example implementations taking the distributed approach (middle node etc.)? Virtual instances in cloud?
      * Martin: there are implementations of different parts, at least for the Ocean implementation
      * Claes: which use cases are targeted?
      * Martin: trying to do horizontal approach supporting various. But in practice have been looking e.g. healthcare, transportation, and home. 
      * Sebastian: what kind of devices targeted?
      * Martin: something with CSE (common service entity) would not be very constrained node. 
      * Omar: currently not very optimized for constrained devices. LwM2M will be part of rel 2 and facilitates support for constrained devices. Very interested in the work of semantics for constrained devices
      * Jörg: here at different stages of activities. Where OneM2M has second release, we are doing exploration. What activities would be best for collaboration?
      * Omar: would have been good to discuss at f2f. Taking metadata approach and faced problems that need solving, e.g., access control policy: who can access what data in what context. If metadata is in triplet store, access control needs to be solved how to work efficiently. Domain specific expertise for ontologies can be provided by OneM2M.
      * Jörg: perhaps too early for ontologies yet but security related work ongoing. Could perhaps do common implementation of scenarios, e.g., the lightning scenario.
      * Omar: at OneM2M per se don’t do implementation; but members do. But pretty sure there is strong interest. 
      * Jörg: some comparison in example scenario makes things easier
      * Martin: will be discussing what can be done. For release 2 it was about basic semantics; now looking into how to go beyond. Looking into other approaches is interesting. Access control for instance works quite well on resources, but there will be a problem applying access control on top of triples.
      * Jörg: will continue working together

* David Janes: [Semantics and the Internet of Things](http://www.slideshare.net/dpjanes/semantic-and-the-internet-of-things)
    * Composition over classes
    * Simplicity and understandability goals
    * key concept: bands. Thing has and is described by bands like model, istate, ostate, meta, …
    * Thing is collection of bands. Bands, JSON-like dictionaries, manipulated RESTfully.
    * Two resources for the state: ISTATE (actual state) and OSTATE (desired state)
    * Agnostic to actual type of light
    * Need istate and ostate for interstitial states; things take a while to happen
    * Reference implementation at https://iotdb.org/ and github
    * Questions:
      * Kax relaying from IRC: who is in control of timing? What aspect need to be considered?
      * David: timestamps (UTC); “not earlier” and “not later” tags
      * Kaz: how to detect if there is problem with device?
      * David: things can report error state, but not yet very good model for this. You know if failed because state transition didn’t happen; can look into metadata then.
      * Kaz: adding diagnostic features could be useful
      * David: underlying concepts are what is strong here. 
      * Johannes: would like to pick up the discussion on one of the AP calls. If this can be dissected to several pieces that would facilitate discussion.
      * Jörg: e.g., istate and ostate could relate to TD actions. Wonder if this kind of mapping has been attempted yet? What would be for TD and what for AP task forces?
      * David: did implementation of TD. Ended up being complicated due to where result was observed and where changes were made.
      * Matthias: David is describing the problem that there is lot of documentation but it’s all in one blob. If that could be split in a way what fits to which TF that is discussed.

### 16:19 Plugfest

* Sebastian Kaebisch: TD Repository
   * GUI client provided as well
   * Registration, e.g., after address assignment, periodically, etc.
   * Semantic search in repository through SPARQL
* Johannes Hund: API
   * Language-agnostic definition
   * API proposal on GitHub
* Matthias Kovatsch: see HATEOAS talk about PlugREST
* Oliver Pfaff: Security
   * Optional features
   * Focus: authorization of actions and authentication of actors
   * Keep it simple
   * AM and AS introduced to Plugfest

### 16:32 Pitches

* Christian Glomb
   * Security token demo on NodeMCU
   * Web client to support servient
* Johannes Hund
   * Servient-side scripting
* Louay
   * Thing API for HomeKit
* Michael Koster
   * Hypermedia System Architecture
   * JSON + schema.org + hypermedia controls + Thing Object Model (script API)
* Kazuaki Nimura
   * WoT servient controlling LED with security
   * TD-based discovery
   * Findings: unclear how to prepare for full TD grammar/vocabulary set, unclear how to express currently available protocols
* Darko Anicic
   * IFTTT rule engine
   * Supports event handling with actions on same as well as different devices
* Soumya
   * WoT for connected vehicles
   * SenML + Android app
* Katsuyoshi Naka
   * ECHONET Lite devices connected to home gateway
   * Findings: names such as “ledOnOff” maybe too specific, effective ranges of property values needed, out-of-range behavior, how to deal with long-lasting actions
* Sebastian Kaebisch
   * Auto TD registration and T2T commander that can run tasks based on conditions
* Tibor (not present in hangout)


## Wednesday, 27 Jan 2016

### 9:11 Welcome

* Joerg Heuer: W3C WoT IG Objective & Goals of the meeting
   * Roadmap
   * Deliverables: need atomic use cases in use case document
   * Plugfest for practical exploration
   * Upcoming work items: start discussion
* Joerg Heuer: Agenda
   * Present breakout topics before splitting up to identify conflicts for participants and schedule accordingly

### 9:30 TF Reports

* AP
   * Finalize technology landscape, assign care takers and look for more contributors
   * Scripting API and also discuss the different types of APIs
   * Protocol bindings, especially together with T2TRG folks
   * Capture findings from Plugfest
   * Architecture document
* TD
   * Scope of TD in the working group
   * Tech landscape
   * Ontology enrichments
   * HATEOAS integration
   * Include security part in TD
   * Processing and semantics for data models
   * Plans for the next Plugfest
* TD Comments
   * Joerg: TFs will also reflect topic areas in the WG
   * Soumya: server metadata (e.g., regarding filtering in discovery) is important for DI -- joint discussion?
* DI
   * Finalize tech landscape
   * Evaluation of tech landscape -- how to evaluate
   * Deliverable document
   * Discussion about DI building blocks such as filtering, lifetime
   * Implication of security for DI
   * Provisioning -- define requirements, scope, etc.
* SP
   * Plugfest findings
   * Deliverable document about privacy landscape
   * How to announce security properties to the outside, how to tell runtime on the inside
   * Support for developers
   * See what others are doing
   * Next steps (e.g., regarding Plugfest)
   * Inputs for the charter
* SP Comments:
   * Soumya: joint discussion
   * Sebastian: joint discussion
   * Oliver: prefer first internal discussion, then go to other TFs
   * Kaz: Check with automotive group, how to interact
* Comment/observation by Carsten
   * API is for application to tell what should happen: setup (less frequently, more expensive) + operation (more frequent…). API needs to provided the needed information.
   * TD goes partly into setup, partly into operation; but more focused to setup.
   * DI is for setup
   * Authorization information is in focus since it impacts everything. Authentication is more straightforward. 
   * Protocols have mappings to different security (and other) features
   * Hard to figure out where to discuss different things.
   * Security often makes sense as distinct activity; however, e.g., thing description work is expressed in APIs and protocol bindings.
      * Johannes explained the background of the split
      * Dave: cleaner architecture layering helps discussion. Presented layers before as one way to abstract these things. For example, should be able to reason on metadata regardless where it is from.
      * Carsten: layering is not very clean
      * Dave: depends on the narrative
      * Carsten: OSI layering never realized. It’s not really layering what we have out there today. When looking at details, layers may get in way. The main concept here don’t come in nice layers.
      * Jörg: whether we have layers or modules, it’s means for discussing these topics. Important to understand interrelations and interdependencies. To organize the works we need some kind of modules. 
Cross-layer knowledge/interaction may also help optimization or result in smarter solutions
      * Carsten: for example, thing descriptions have actions. But can’t discuss it at TD alone. More important work to happen in common meetings.
      * Michael Mrissa: link between discussed schema and servient architecture?
      * Johannes: API has several meanings. Servient API to expose resources to other components and scripting API to expose function calls to application logic
      * TD and DI will have joint session
      * TD and HATEOAS were already on agenda
      * API and setup topic not yet on agenda
   * Johannes: very much related to scripting API. Plugfest finding: need to look into how to setup system and create things (virtual representations)
   * 10.30 Coffee Break

### 11:00 Breakout in TFs - Tech Landscape Discussion

   * TD (Things Description - Agenda & Minutes)
   * AP (Scripting API and Protocol mappings)
   * DI (Thing Discovery and Provisioning)
   * SP (Security, Privacy and Resilience)

### AP breakout

   * Kazuo Kajimoto: [Architecture document](https://lists.w3.org/Archives/Public/public-wot-ig/2016Jan/att-0042/WoT_architecture_20160127_Panasonic-Fujitsu_.pdf)
   * Abstract model from TPAC 2015; going now for more concrete model based on that
   * Physical, Client, and Server APIs for scripts. All APIs server by API providers (interpret scripts, retrieve information, etc) built on resource management (managing connected devices, request, ..) and thing description. Protocol mapping to legacy, web client, and web server communications. WoT API towards WoT servients; proprietary APIs towards legacy devices.
   * Architecture caters for with and without cloud communication
   * Resource management layer used for exposing the protocol functionality from different protocols to the applications via the scripting API
   * Comment: examples for need for physical, client, server API in the doc would be good
   * Conclusion: the architecture doc will be updated based on Kajimoto-san’s proposal
   * Louay Bassbouss: Thing API
   * https://github.com/w3c/wot/blob/master/TF-AP/thing-api/thing-api-webidl.md
   * ThingFilter a key part of the API
   * Johannes: makes sense to discuss this together with DI group later
   * Thing interface; actions and property get/set based on Promises. Listeners for events.
   * Johannes: missing decorator for addListener; possible to add properties. 
   * Claes: after receiving/discovering thing one does not see thing description? Maybe should expose that to the application
   * Louay: noted this problem with HomeKit. Disadvantage of thing descriptions; 
   * ; maybe want to follow CoRE way; defining type of the interface.
   * Johannes: the interface is generated from thing description
   * Louay: similar model to UPnP on the way of exposing services to network
   * Observing actions and observing property changes is now using same mechanism. Unique names for each needed.
   * Nimura: accessing the actual devices using the API? 
   * Louay: for app not important if the interaction is direct or via cloud. This API is decoupled from the underlying implementation.
   * Johannes: presented API seems to cover client side actions. Server side still needs to be discussed separately.
   * Conclusion: will keep the proposal as now, just separate discovery and interaction. 

### TD breakout

 * Discussion about elements in TD
 * URI could serve is uniform abstraction to handle different protocols and to address “thing instances”
 * “server metadata” is about additional communication data for “exotic” transports or for optimization (knowing buffer sizes etc.)
 * Assigning care takers to tech landscape

### 12:30 Lunch

### 13:30 Breakout in TFs - Findings Plugfest and WG Work Items
 * TD (Agenda & Minutes)
 * AP
 * DI
 * SP

### TD-DI Joint discussion

* Dave Ragget: Distributed Web of Things (see “smart manufacturing slides 29-30)
   * Distributed systems. Scripts running in different places should not need to know the communication details of the other.
   * Metadata about thing descriptions, security, and communication
   * Matthias: what are the views for Thing Description? What is the DI TF missing that TD could help?
   * Soumya: how to use TD for discovery and maybe TD can be used for filtering
   * Matthias: TD repository done in the TD DF. 
   * Darko: creating example for tomorrow how TD can be used to get additional data (location etc). And then could use SPARQL for that. Building example on SSN ontology. 
   * Sebastian: different levels; e.g. IP level discovery or data discovery.
   * Soumya: what do we try to discover. Things around me, in my network, from directories, across peers, based on metadata, semantic based discovery.
   * Dave: social network based discovery. Network of friends-of-friends. Applying to that to IoT.
   * Martin: semantic discovery; depends on what are you looking for and what are the assumptions. In OneM2M little discovery possibilities. Not enough, so need description and using SPARQL etc. Fits quite well to our needs. Can use to find resources. The slides have pointers. Will send text too.
   * Dave: thingsonomies and informal semantics can be useful too e.g., based on tagging. Depending on use case.
   * Soumya: how to use thing descriptions for filtering
   * Sebastian: know from TD what kind of data would be available and can be used for filtering.
   * Dave: properties for filtering: SPARQL queries could be used, or some high level API with semantics. Application level APIs for supporting that
   * Maxime: Repositories of triplets could be used for this. Not sure if we need to do new ones or specify which to use. Vocabulary defined could be useful. Discovering things on server, things expressed in RDF and perhaps ontology. 
   * Soumya: applies only to semantic discovery. For example CoRE links would not have ontology. 
   * Carsten: at IETF painful experience with location protocol; that nobody uses. Good idea to have strong look at use case and examples. 
   * Maxime: can we have common way to query triplet based and CoRE platforms?
   * Carsten: in CoRE the ways are very simple. Should be easy to translate.
   * Maxime: for interface type there is no relate for RDF. Could define ontology for semantic web type and use URIs as custom relations in CoRE context

### AP-TD joint discussion

* Plugfest
   * Some missing/unclear issues discovered: setting up IP addresses, data types with restrictions (e.g., range), access control restrictions, decoupling semantic type / relation, resource hierarchy, how to include more context / semantics.
   * [...]
   * Matthias: With HATEOAS, if thing breaks or changes, you follow the links again. Whether for new system you opportunistically take use of it, it’s different.
   * Louay: For protocol bindings, e.g., client finds information about binding to bluetooth device. For CoAP and REST there is clear way to access, but for specific mapping and property of underlying tech it’s not clear. 
   * Carsten: need to define URI for that information
   * Ari: Bluetooth SIG has published a whitepaper on RESTful API via GW
   * Matthias: fair assumption we access legacy bluetooth devices via GW
   * [...]
   * Carsten: do the right thing (re: thing description example)
   * Interactions should have hrefs and protocol description just _base
   * Can have relative or absolute URIs and with different schema (CoAP, HTTP(S), BLE)
   * Jörg: more plugfest activities will be useful for figuring this out
   * Wot Architecture
   * Carsten: important to separate structure of implementation, API, and interchange documents.
   * Johannes: important to separate in concepts the resources and how they are delivered
   * Conclusion: write down plugfest feedback. Also different ways to do TD; where you have the URIs. Carsten and Sebastian will work on proposals for further discussion.

### TD-SP joint session

 * TD currently split in two: communication part (metadata) and capabilities part (interactions).
 * PlugFest discussions implied need for access control. How to do that? Add links for more information for interactions?
 * Olivier: already security info in TD; in the schema: use TLS or not. But also many options e.g., cipher suites. Hundreds of possible combinations. Would suggest to not go too fine grained here though. 
 * Two strategies 1) a-priori (client has security token before request; metadata at TD) 2) a-posteriori (get error for request and asked to get token). W3C should not take decision whether is used. We should not evangelize either way but keep the way optional.
 * Sebastian: easy to define the existence of token to be optional
 * Olvier: need to consider what is told to the caller; at what granularity (host, port, path, …). There is no (good) best current practice for what we are doing here; based on human-readable instructions only.
 * For tokens to consider: expected issuer, expected token type (JWT; CBOR WT, URN), expected protection (encryption, signature types, …). Expected protocol for discussing to security infrastructure (e.g., OAuth / HTTP / TLS). Etc.
 * Carsten: merge this with the issuer
 * Sebastian: Resource Server (RS) provides this information to the client?
 * Olivier: Client makes call to RS (does not know about security; no security token). Resource is protected; RS responses (e.g., 401): give minimal information how to proceed (who to talk to, with what protocol, and what to ask).
 * Carsten: DCAF has also nonce; have found useful. 
 * Need to consider role of nonce in request/response vs. announcement of TDs.
 * Sebastian: is there standardized container for the information?
 * Olivier: would look into JWT for container.
 * Matthias: should be able to fit to TD or come with media type in response
 * Conclusions: should setup examples of TDs with the security information. Need the optional element to say that resource has access control. 
 * Matthias: other connection points between TD and SP
 * Olivier: could discuss granularity of access
 * Carsten: for example, property that can be read by anyone and written only by some
 * Olivier: also ability to get security info could be subject to access control
 * Sebastian: how do we trust security info in TD? Something to consider.
 * Olivier: would recommend against everything being signed since that involves a cost (who can sign what etc)

### 17:10 Wrap-up

 * Sebastian: Thing Description
 * Started with plugfest and clarified many topics. 
 * Tech landscape responsibles appointed
 * Discussed how to use TD in discovery and filtering. For AP discussion going to have use cases and examples. In security got good input on what kind of metadata is needed for access control
 * Soumya: Discovery
 * Freezes landscape document and will move it to github
 * Discussed new tech: Wi-Fi beacon
 * Discovery protocol abstractions (involving different protocols and techs) and filtering & ranking
 * Thing and server metadata discussion, semantic discovery, filtering with TD. Discovery and TD tightly coupled
 * Security session had overview of plugfest implemented security. How to include security and privacy in different aspects of discovery. Will capture these in separate wiki.
 * AP discussions: should have generic discovery? APIs for registering and discovery? Perhaps not separate work item needed for discovery, but TD and AP could cover this.
 * Johannes: APIs and Protocol bindings
 * Two major points in AP session: Reference architecture. Consensus on the proposed architecture. Comments welcome. API document from Louay. Split up discovery and interaction parts. Also need API for the server side.
 * Security session revealed white spots. No universal standard for token issuers and consumers.
 * TD session re-capped plugfest findings: how deal with different models. 
 * For discovery, will focus on client side APIs. In API will stay with key-value pairs and let the underlying mechanism figure out details.

 * Jörg: tomorrow will consider work items and see if some should be merged.
 * Joerg: All current findings and assumptions should be collected in a document (“Current Practice”) to prepare for upcoming plugfests and also better present our current state to the outside
 * WoT/T2TRG collaboration going forward.
 * potential for joint meeting before IETF96 at Berlin (around 16th July) with RIOT summit
 * Joint meeting July 16/17 might be difficult because of W3C in Beijing until 14
 * July 23/24 just as critical for IETF attendees
 * March 15/16 T2TRG meeting adjacent to IAB semantic interop workshop at San Jose
 * Virtual plugfest planned early June
 * Common meeting at Lisbon TPAC 2016, September 19-23?

### 18:00 EoD

##Thursday 28.1.

### TD + SE session
* WG work items
   * Topics in proposal
   * Vocabulary For Describing Data Models
   * Vocabulary For Describing Server Metadata
   * Serialization formats
   * Sebastian: In charter, there should only be one deliverable, the content will be structured, though
   * Oliver
   * Also include container for security information (e.g., which type of token to acquire from where)
   * Container should support integration in TD and inclusion in responses to be presented during run-time
   * also include mechanisms to protect data
   * Matthias: could make sense under serialization formats; metadata can describe how to handle protection (e.g., keying material etc.)
   * Sebastian: keyword “security” must explicitly appear in the text
* Strawman proposal
   * Sebastian’s word document
   * Need for guidance how to include legacy vocab/ontologies, so that TD does not corrupt
   * Need for multiple serialization formats, evaluate and start with one recommendation
      * Michael Mrissa: not fully clear what will make up the “data model”, need some more concrete examples
   * Matthias: Bottom-up attempt
   * vocabulary for identifying Properties, Actions, Events
   * vocabulary for link and form relation types (configuration, lighting, create item, change state)
   * vocabulary for data items (RGB value, brightness) -- each entailing an understandable
   * vocabulary about security properties
   * … continue ...
   * AP + DI session

* Proposals for WoT WG work items
   * Scripting API & Binding to common protocols
   * What is deliverable of bindings work?
   * Dave: could define thing layer for abstract messaging and how this binds to different protocols. Collaboring e.g. with IETF CoRE WG 
   * Soumya: oneM2M have defined protocol bindings for HTTP and CoAP
   * Johannes: bindings should be something we can give to protocol defining folks
   * Dave: precedent with WebRTC with this kind of split of work
   * Johannes: what is the right level to express? URIs help when you can map to one. Minimal set of assumptions and guidelines: e.g. can address items. HTTP and CoAP being the most common protocols; would work together with IETF.
   * Dave: also testing framework. Demonstrate with different groups (e.g. CoRE) how things work together. Framework and test suite. Every requirement mapped to a test. Framework there just to help building and executing tests. Key for showing interop. But not up to compliance testing.
   * Soumya showed example of oneM2M protocol bindings for HTTP and MQTT: http://www.onem2m.org/images/files/deliverables/TS-0009-HTTP_Protocol_Binding-V1_0_1.pdf
http://www.onem2m.org/images/files/deliverables/TS-0010-MQTT_protocol_binding-V1_0_1.pdf
   * Johannes discssed scope and deliverables: https://github.com/w3c/wot/blob/master/WG/wot-wg-items-ap.md
   * In scope: API definitions, call-back signatures, security model, language independent examples, etc.
   * Dave: with API definitions need to be clear on the level of APIs. For language independent definitions need to think of the functionality (e.g. are Promises part of it?).
   * Johannes: may need to implement some features in runtime. Would be good to discuss in pull requests and GitHub issues. For bindings, in scope resource model and URI concepts, interaction models, integration points, guidelines how to map protocols. Out of scope: URI mappings for non-resourceful protocols.
   * Dave: basing on URIs too strong. We want to update properties of resources; need some kind of addressing sub-resources. But does not necessarily mean URIs. For example abstractions in CSS, XPath, etc. 
   * Johannes: suggesting abstraction based on URIs.
   * Dave: you need way to identify what is being changed and how. Depending on the underlying layer what is natural there. 
   * Johannes: want everything addressable as URI
   * Dave: URI implies protocol scheme. Need in bindings but not in abstract model.
   * Johannes: bluetooth is very different from MQTT; both can be mapped with URI
   * Claes: more than one way of using Bluetooth, for example. GATT and also IPv6. Seems strange for inventing yet another way of using Bluetooth. Using something that maps well to web model, IPv6 way makes sense.
   * Dave: what’s the connection of URIs to abstract model?
   * Dape: How about if you’re using protocols directly? Can map to URIs
   * Dave: each platform has own addressing scheme
   * Johannes: idea; what ever you encounter in WoT; can be addressed by URI
   * Kaz: if resource model and URI concepts are split? 
   * [...]
   * Joerg: should take this discussion later to take discovery today too
   * Claes: would be good to have examples of the different approaches to make it more understandable
   * (will do that off-line)
      * Uniform and technology independent discovery
      * Soumya: API aspects could go to API doc. 
      * Joerg: different categories for discovery, and protocol mappings. Something more to look into?
      * Soumya: the mapping not complete yet.
      * Johannes: more impacting client side than server side. Better handled by runtime than script. 
      * Soumya: bindings handled in the API doc.
      * Dave: need to make sure the work docs are easily findable

### TD + DI session

* Carsten: Documents need to start with the definition/context of what DI means
* Objective: How to discover TDs -- but also thinks about iBeacon and other local broadcasting at lower layers
* TD must be discoverable -- Matthias: probably needs to be linkable and support linking
* TD must provide means for filtering (of data description such as sensor type, of metadata such as location)
* Server metadata in TD is unrelated to initial discovery process, but important for filtering once a component already has the TDs
* Metadata part of TD must be extensible to include tags for filtering
* If DI needs features/changes in TD, DI needs to provide the requirements; TD is not looking into how to process TD such as search engines, recommenders, etc.
* Carsten: Different phases for metadata 
* Manufacturer, e.g., serial number
* Installer, e.g., location, bindings
* Lifetime, e.g., reliability information about reachability
* Carsten: Lifecycle management will be important to consider

### AP + SP session

* Olivier: Security APIs should be considered 3rd party; come from .e.g. IETF. For example, OAuth token API (RFC6749): POST to a URI.
* Johannes: security APIs not in scope, but to incorporate them.
* Olivier: calling the APIs should be in scope, but supplying (specifying) not. Should have subset of the APIs in client that supply functionality for interacting with Client Security helper. Convenience helpers for application developer to enable security functionality.
* Claes: need authorization functionality in scripting API. But not the transport itself needs to be exposed.
* Daniel: we need to collect aspects of the runtime. Require tokens, etc.
* Olivier gave example of private resources with public facing service. Want to relieve security complexity from the serving system. Security tokens in requests supplied by clients helps there.
* Dave: security tokens could be explicit for the application or handled by system
* Olivier: how about security exceptions? How are they handled?
* Johannes: we need some kind of abstraction for security. But the level is open.
* Claes: With Oauth for IoT devices the user focus of Oauth and lack of UIs for devices is challenge
* Olivier: the work is ongoing in this space. We should express our desires for the functionality.
* Ari: ongoing work at the IETF for OAuth for IoT: https://datatracker.ietf.org/doc/draft-ietf-ace-oauth-authz/
* Olivier: work and specs for binding to CoAP/HTTP and any SASL enabled protocol exists from IETF
* Kaz: need to clarify the need for security
* Olivier: should be careful not to detach security too much. 
* Johannes: added to scope “high-level security handling on client and servient side”
* Oliver & Johannes: definition of security frameworks and protocols to out of scope

### TD session

* Darko: Ontology Enrichment
    * How to enable things to understand semantics?
    * Semantics used for discovery
    * Ontologies map Properties to concepts in a taxonomy
    * Need to describe the terms with the ontologies
    * Discovery can then be made with this rich model
    * Thing description ontology describes elements in the TD and allows mapping to other ontologies
    * Darko showed WoT ontology how TopBraid can be used to execute SPARQL queries etc. based on the ontology and thing descriptions
    * Now WoT ontology is connected to SSN (Semantic Sensor Network) ontology
    * Matthias: if two companies use different vocabulary for TD. Ontology solves this?
    * Darko: yes, but not implemented in my demo yet. That’s the next step. If we use the same ontology, we’re good. If we use different ontologies, need to do ontology mapping. 
    * Can do queries such as: “give thing descriptions that observe distance and illuminance” (in standard SSN terms).
    * Matthias: how fleshed out is WoT TD ontology?
    * Viktor: around 10 terms, 5 classes
    * Darko: for example, has interaction “action”, “event”, “property”. Has “metadata”. no yet model for e.g.,  “LED on/off”
    * Viktor: already other ontologies for this (domain specific) 
    * Darko: domain specific ontology would be out of scope for WoT. Something for the plugfest though. In the future to consider relationship to discovery etc. 
    * Ari: how complex/complete the idea to make the WoT ontology
    * Darko: keeping it simple.
    * Viktor: port to using other ontologies
    * Matthias: how can we limit this? Don’t want to describe the whole world. Describe things we want to connect and interact.
    * Viktor: could give limits for the size of used ontology. WoT ontology has nothing domain specific.
    * Sebastian: like the fact that we have now very simple model but it works and provides value
    * Matthias: need atomic vocabulary that is independent of domain. Maybe one step more concrete from “name”, “writable”, etc. Say, switching on and off. Cross-cutting vocabulary terms.
    * Ari: or for example “increase”, “decrease”, “reset”
    * Haven’t yet looked that kind of requirements from use cases to address here
    * Sebastian: worried of where to draw the border
    * Ari: already have drawn the border; but at quite abstract level. Might be worthwhile considering more concrete versions too
    * Darko: will be learning from the plugfest
    * Martin: base ontology trying to limit what is relevant for oneM2M. Then derive more specific things for each app. Depends if there is generic understanding what is e.g. “on”. If not the case, would leave for more specific ontology. How things are managed is also an important aspect (Matthias: DM vocab?).
    * SSN2 is splitting into many blocks. Minimal vocabulary for describing sensor. And build layers on top of that.
* Dave: Processing and semantics of data models -- not here

### Charter work: TD work items
* Goals and Scope
* See Sebastian’s Word document
* Out of Scope
* Domain-specific vocabulary
* Post-processing of TD such as filtering and ranking
* Protocol-specific mechanisms
* Serialization format (rely on existing such as JSON, CBOR, EXI)
* System-internal representation and generation of TD (Scripting runtime-related definitions need to go into API document)
* the enforcement of described security mechanisms
* Deliverables
* Specification of the TD document type
* TD ontology file
* Potentially a security document describing how to use existing security 

### Work organization, time plan and next steps

* WG charter
* Sebastian reports for TD (see above)
* Questions? [crickets]
* Johannes reports for AP
* https://github.com/w3c/wot/blob/master/WG/wot-wg-items-ap.md
* Matthias: Because of “testing approach”, any certification activities planned?
* Johannes: no
* Dave: If SDO of some protocol won’t define bindings; should we have it still possible to have in scope for us? Should make sure we don’t write in charter that this is not in scope. Re-chartering is expensive process, so better have it not excluded in charter.
* Charter layout
* Combined work items (no TF separation anymore)
* For each item: scope, out-of-scope, expected deliverables
* Next steps
* 7.2. compilation of charter document on GitHub (linked from wiki)
* 22.2. 1st round of comments  ends
* 7.3. 2nd commenting round ends
* Ari: personally limited possibilities to contribute during this short timeframe
* Deliverables
* Use case document: work paused
* Tech landscape: many whitespots
* Deadline: 15 Feb 2016 transfer everything to GitHub
* Deadline: 29 Feb 2016 first “complete draft”
* Architecture document: Start on GitHub, will reflect input from this F2F
* Initial draft deadline: 29 Feb 2016
* Current Practice document
* Collect current discussion and plugfest results
* Volunteers
* Daniel (as co-editor)
* Matthias (for reviews)
* Kaz: provide template for contributions
* Johannes: there is an appropriate W3C template
* Dave: also include photos to make it more personal and inviting
* Report from Communication & Collaboration
* A task force in the W3C to improve reach-out to other organizations
* Phonecall every third Wednesday
* White paper (CES 2016), sales sheet (IoT World USA) -- help Dave and Molly for good WoT pitch
* Maintain a list of interesting conferences and events
* WoT WG announcement at IoT World USA
* Testimonials (“likes”) for WoT landing page
* Add liaison organizations -- see wiki on “Tracking
* F2F meeting of the C&C TF in Montreal, April 2016
* Plugfest preparation
* Network setup must be specified beforehand
* TD Repository already helped
* Findings in Nice
* Darko: Wants more thing-to-thing interaction. Need to find good way to handle callbacks. Repo should enable us to have DI in Plugfest; in general better include all TFs. Also test more complex scenarios, with contributions from SP, DI, TD
* Kaz: Include this in Current Practice document
* Joerg: The document should cover the basis for future Plugfests
* Dave: Open up plugfest also for application developers (hackathon-like)
* Kaz: Maybe provide a basic platform for them
* Johannes: brings in the notion of documentation quality requirements, which might be harder, but has a benefit
* Matthias: Maybe try at RIOT Summit in July in Berlin?
* Joerg: Links to existing implementations might help to connect to open source communities.
* Have it close to the Current Practices document on GitHub to foster open source collaborations
* Upcoming Meeting logistics
* Resume Webex calls next week
* BOSTON meeting MOVED to MONTREAL to collocate with WWW Conference
* Kaz: Problem with Thursday call
* Moving to 1pm CET
* Kaz: relaying comment; is it necessary to have meetings every 3 months?
* Jörg: f2f meetings help resolving issues; especially in this early phase. Perhaps can to reconsider December time frame meeting schedule (move to January?).
* Speed up document work to meet deadlines to charter WG
* IG still runs until end of March
* Either do a short-term extension of the IG to finish properly or re-charter and have a long-term support IG in parallel to the WG
* Thanks to W3C staff for the support

### Meeting concluded

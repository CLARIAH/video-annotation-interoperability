# video-annotation-interoperability
Proposal for crosswalks between a number of video annotation tools, including the CLARIAH Web Annotation tool, ELAN, FrameTrail, VIAN and Waldorf.js.

[Blog post on our first meeting (12-13 July 2018)](https://clariah.github.io/mediasuite-blog/blog/2018/07/11/Clariah-annotation-expert-meeting)

[Blog post on our second meeting (13 July 2019.](https://www.clariah.nl/en/new/blogs/vaint-video-interoperability-interest-group-second-meeting-july-13-2019)

## Introduction
Digital annotation is a common activity among scholars, and takes places across different data and media types and across different digital tools. Digital annotation is one of the most active research fields in the last years. The conditions in order to use annotations in computer aided research and for the design of new digital research tools have improved significantly. The recent approval of the W3C Web Annotation Data Model (formerly Open Annotation) as W3C recommendation marks a big step in this respect, allowing to gain interoperability of annotation data across annotation types, tools, research practices and domains.

This proposal describes the planning of a two-day face-to-face expert meeting and workshop that aim to improve annotation interoperability within the CLARIAH infrastructure as well as with external annotation tools. Improving the interoperability allows scholars to connect their work both across CLARIAH work packages, as well as with annotations created by external tools.

The Web Annotation (WA) Data Model is a very generic model that allows for multiple solutions in order to model the structure of certain types of annotations. Furthermore, the model permits to be extended by other models in order to tackle issues which are beyond the scope of granularity of the Web Annotation Data Model. This situation calls for the definition of so called application profiles as they are used in the context of other generic models, such as Dublin Core. An application profile defines a subset of a data model in order to model a phenomenon that is of smaller scope than the scope of generic WA model, and that is relevant to specific types of research. In this respect the annotation of video is a specific case of annotating that has its own set of issues in comparison with the annotation of other resources. Furthermore an application profile describes recommendations and best practices for how specific terms of a model should be applied and interpreted within such a specific domain of application.

In the context of video annotation, such an application profile is of particular interest for a variety of reasons. Video annotation is a complex task because video is a multimodal media resource. The landscape of digital annotation tools is heterogeneous and reaches from desktop application tools to web applications. Tools specialize in specific tasks and model their data around such tasks. Many tools that are commonly used have a very long history which reaches back to times in which no shared understanding existed how to model annotations in a standardized way. Consequently, today’s annotation data is still produced and represented in different data models as well as content models. The work on an application profile for video annotation data will enable the definition of so called alignments and crosswalks between such models and the data that is represented in them. In doing so, such alignments enable two important things. On the one hand they make it possible to export annotation data which was created with one tool, to use it in another technological environment. On the other hand they create better conditions for the long-term-availability and -preservation of annotation data. Corresponding infrastructure will be able to focus on the requirements of the application profile and the transformation of annotation data to the model of the application profile.

CLARIAH work package five has worked in implementing an annotation tool which uses the W3C annotation model for structuring the annotation data. This tool is of high importance for supporting scholars who work with audio-visual collections (e.g., film and television scholars, oral historians and, in the future, communication scholars working on conversation analysis as part of the ADVANT proposal). Recent discussions in relevant stakeholder groups such as the DARIAH WG Digital Annotation and the ADHO SIG AVinDH showed that significant interest exist in the realisation of the aforementioned goals. Video annotation and interoperability were also an important topic during the recent Lorentz Workshop on “Collecting, Annotating and Analyzing Video Data”.

## Goals

1. Drafting definitions of Crosswalks between schemas of commonly used annotation tools,  in CLARIAH and external, on the basis of an interoperability layer which is derived from the W3C Web Annotation standard.
2. Drafting of a W3C Web Annotation application profile for video annotation on the ground of the aforementioned interoperability layer.
3. Involve international scholars and developers in the discussion and development of interoperable annotation in CLARIAH. 

The draft crosswalks and application profile will then be distributed for broader input, and will be improved and finalised in subsequent meetings.

## Deliverables

The schema crosswalks and application profiles will be published on GitHub and will be actively promoted to encourage uptake and reuse.

+ the [draft implementation of the data model](data/example_annotation.json) was written by John P. Bell (see [novomancy/webannotation](https://github.com/novomancy/webannotation) for the [original document](https://github.com/novomancy/webannotation/blob/master/unified_v0.1.json))


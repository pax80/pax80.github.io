---
layout: post
title: plantuml otel architecture
categories: [blogging]
---

# blog Plantuml otel architecture

- [intro](#intro)
  - [What is Plantuml](#what-is-plantuml)
  - [How to render](#how-to-render)
  - [why opentelemetry-demo](#why-opentelemetry-demo)
- [Build the diagram](#build-the-diagram)
  - [121 mapping with no layout change](#121-mapping-with-no-layout-change)

## intro

Building diagrams is a day to day task for me.
This is to:

- describe and environment
- show application flows
- explaining ideas

I want to be able to create diagram based on plane text file. This allows me to revision the diagram within codebases or
other specific git repositories.

### What is Plantuml

> PlantUML is an open-source tool allowing users to create diagrams from a plain text language.
> Besides various UML diagrams, PlantUML has support for various other software development related formats
> (such as Archimate, Block diagram, BPMN, C4, Computer network diagram, ERD, Gantt chart, Mind map, and WBD), as well as visualisation of JSON and YAML files.
>
> The language of PlantUML is an example of a domain-specific language.[5] Besides its own DSL,
> PlantUML also understands AsciiMath, Creole, DOT, and LaTeX. It uses Graphviz software to lay out its diagrams and Tikz for LaTeX support. Images can be output as PNG, SVG, LaTeX and even ASCII art. PlantUML has also been used to allow blind people to design and read UML diagrams.[6][7]

> _[From wikipedia](https://en.wikipedia.org/wiki/PlantUML)_

[mermaid](https://mermaid.js.org/#/) has the same approach to diagram creation but is using a different DSL.

### Why Plantuml

[I go more in detail on my previous post](https://pax80.github.io/planuml-user-experience/)

### How to render

To render _plantuml_ we need to select a server

- [spin up plantuml docker server](https://hub.docker.com/r/plantuml/plantuml-server)
- [use the online server](https://www.plantuml.com/plantuml/uml/SyfFKj2rKt3CoKnELR1Io4ZDoSa70000)

### why opentelemetry-demo

I read and follow **otel** and the repo is public available.

[The architecture](https://opentelemetry.io/docs/demo/architecture/)
of the demo shows services that made up a **simple** online shop.
This is a perfect example to show the capability of plantuml and the simplicity on how a diagram can be build
by using _diagram as code_

## Build the diagram

### 121 mapping with no layout change

The first step is to create the same amount of boxes we have for the original
diagram and coloring

[Code](/assets/diagrams/otel-demo-puml-1.puml)

Render:
![image](http://www.plantuml.com/plantuml/png/bLPTR-8w47tthx3AbNhlGoi-e9Js5hKDi5fj7zhbSNSL6MU0B2PE7QTjjDh_ldOWuAa3sY8XalauddDcFE8sqqpfV2q88GguPib203tv_v-5a3C8uqI3Ia0FloUVjuydb6MqihzBIWkzb8a9Vf0iefyW0SMqL6MACAPmKPbeezFhj-zwrnhUzDNhCjQ0eNIHGiPLdDgp9qecca8IbKXp-sPUQ6FSxBTQNPp8Kv5dzXkAE87mLQfepTJAebHvZqg-5VJVSV8YY_yGP9XQbm4UjISNzsvnvDIGvd8T9mkg5PlFOqxUPPrzQym4uwiVPyCT8AcKmbwKIB0qzJX4omNe9IZwYr3pGPn_iXTc2Dv5D0Fr4dCeIHdGxIjj32QzIQldPwwaDZALuh0yeYFGnXlBX4uTeBdrXL7bswDssytceEdAv1smaBOmpcMUQAlTTEmKk3Fl8LkTmIYO7C09bi1NCjUeEhurUXY_oQv3zARIz6Rew5Bhzm1jxmKhGD4E8Syvv1lbs7nbHVzYVyj2IWjjb49Ss-6xAY49EQJVUNNe-N2JJ6eKyOCymdx8qMbHUMOlrNGPfwav2OcPMIDgoAWxwFPR60NTzQ_0vNfjH6JUu2ZascFwTx--LpT3hw3wCE-aVUTc2jYAdE8b4KczsMe1K--cYIbtalgN5qqquCxvg00tp-kG6-i5-xtwgsqMv4f1mWjS_TPOWLURh6u8PeL16QzPB104MCi-lnSqWrRBLQ1s--nMzIChJ1kmfkd6vXGLZ8BkO0DQocBwVrIqeSVC3pzpzoPYuSUYrk7oS8kFLK3mVLYcXlvJBZKWyi_Muep-k3kuxBXw-clkKSaevphaJ3CXpUYxMYAVlpYFSHqUoYRUjNUrH0m8lcaVEcM_IBl4fBCPopQp256SbPUHBwjRQ9x2qcuOCLNF1aKX6K49ysmW9y1qhe1E1CEBRhvnX7F1717l-ktcvONR7KyQL44T2i7qFv28_nOuyOSIa8gfpFH2GVOiFDvQAZ1ZjGsOFZtGqNsD2ZQC46ohhzrB8hUcxdmj_W00)

> **together** statements allows to group objects without the need to have them within a bigger container

```bash

together {
        rectangle "<$rust>\nShipping Service" as shipping_service #D49471
        rectangle "<$python>\nRecommendation Service" as recommendation_service #3572A5;text:white
}

```

![together](/assets/img/together.png)

- change of line

> Line type are differentiate to connections
> this can be achieved with the use of different symbols

```bash
A --> B: Line
A ..> B: Dotted line
A ==> B: Bold line
```

[more explanation](https://crashedmind.github.io/PlantUMLHitchhikersGuide/layout/layout.html)

### User ortho lines

Ortho linetype render straight lines instead of curved once

[code](/assets/diagrams/otel-demo-puml-2.puml)

![ortho](http://www.plantuml.com/plantuml/png/ZLPTR-8w47tthx3AbNhlGoi-e9Js5hKDS7MrVMYNnzrLP9m1iZXnwZXjezN-zxK30KyTgY8XalauddDcFE8srqpf8X64v9iupPXY2HLn2hhCW4gbrv8G1LopT2M0dlpxrqh81OHnga6PgF7tzF_TumbbEQtjxvAoqW2b9lX1ieZ-1oaefgMgKeGnXQlQH5kzmR1xDxZMyAQlNjUn1Wnb2ykvYZDxzap9L5D8emffQT_C2srDsyDEfuyJUIQAt7v3oozybIfAcDfOb3hlKSctaluzJLza-G-233FhCi2JxkpYtYsEd1hIN2Pnkg9QiUKovkHTrjctra8mllbnDju3abefvCM914lJZ4EqN85UWwA_23KVnFadUs66u5r4Sr0lCOUAb07TlTBMQ3QOTGP-vaPg8rCb3YiYEW5jlB5CwTm1MbfV6DM-0sg_sswFsgvCtW4hQGlZN1QfjjhDfqw1U_C1ijCRJOBP4PnW3NmZ2usgupkZX_6Rx3j4RsfDRyQEBer-3z3sNh0I5EqHybn0iLMEBJTMz2_sjogaij1M9SIr7Rwh2fAGO_gTruUUZxV9n5EaASWZx8LyF2sgoEsbcg_ZB3Cd8J5pQqGDcVH7_M47ew2x_XMuJ18Z8lC6Ho7N0TE_-yszkXbx1JM7UISTEhTGm3Ra52-9IEhjLWkOUZTDJBcJDBoyQBi3xfQ92d3p_0uviLwmrwlFRREWK0fINkBgTyOQlDvaJKEmA0tAD66nG11WBOVyGT0EEXr7WURjir_LZwmqRS2QPbkRKrGm2VgZBMWbY-d_XwADFMP--9cxDn4BFnQr3fVdjVXe1GJVXtLcw3yLKWCY_smjpkXF-wFBdgkdl-OUbOmAhaFED1FIZBwh9VBvY_CZhkDZsSIxzgwMY07nRzgdJpaiqZunwMp1ykqiGXJdrMNaw_eMcgUmiXj6J3MoGL5OHb32F1l86J1TAA0pmV2YMsuTuL8mHyIxORTzUU5snvC6LT24GZpwdqt4VmkS-6C9ICLCvdgb87yM7cyj5PYnsWNCdnxevBv11Hj62BOrr-ubaLjJTv68Fm00)

### Adding Icons 👍

Plantuml has a standard library containing icons for all the devices.

[Library](https://github.com/plantuml/plantuml-stdlib)

To add an icon:

- import with the include statement
  `!include <logo/nginx>`
- use on the diagram
  `rectangle "<$nginx>" as nginx_app`

```plantuml
!include <logo/nginx>
rectangle "<$nginx>" as nginx_app
```

![nginx example](http://www.plantuml.com/plantuml/png/SoWkIImgAStDuUBYKipCIyufJKbLiCd9JyylrizBpyohiEDAJ2x9Br8eBKujuYfAJIv9p4lFILLGib61I2if91OhW9bSN20r2hgwTZ2-GsfU2j1e0000)

[Code](/assets/diagrams/otel.puml)

![with Icons](/assets/img/otel.svg)

### layout tips

Inline layout is starting with `#`

Hex will define the color of the inside shape
separated by `;`
**_text_**:color

```bash
rectangle "<$kotlin>\nFraud Detection Service" as fraud_detection_service #420090;text:white
```

## Conclusion

### Why i like it

- there are now plenty of logos to choose to make the diagram looking even more professional
- **ortho linetype** gives a clean layout look
- using the include statement allows to create modular design reusing specific components without the need to rewrite the same code overtime
- lots of documentation online

### What could be improved

- allow and easier layout positioning. at this moment there is no coordinate enforchment and the layout will depend on the way box and line are ordered

### References

- [Plantuml site](https://plantuml.com/)
- [Docs](https://crashedmind.github.io/PlantUMLHitchhikersGuide/index.html)

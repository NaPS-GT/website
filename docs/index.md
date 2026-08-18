# Nanotechnology and Photonics Society @ GT

![NaPS](assets/Buzz_cleanroom.svg){ .center .off-glb style="width: 180px" }

The purpose of the Nanotechnology and Photonics Society (NaPS) is to foster an environment that gives students an opportunity to explore all aspects within the semiconductor fabrication pipeline. Through semester-long projects, members can gain hands-on experience in process engineering, equipment maintenance, and experimental design.

<!--
  Community card grid. Add or remove cards freely — the grid reflows on its
  own. Swap an icon by changing the :name: between the colons; the full set is
  searchable at https://squidfunk.github.io/mkdocs-material/reference/icons-emojis/
-->

<div class="grid cards" markdown>

-   :fontawesome-brands-discord:{ .lg .middle } __Discord__

    ---

    For day to day coordination and chit-chat.

    [:octicons-arrow-right-24: Join the server](https://discord.com/channels/1496377146757615696/1496377148456439891/1532522882150830120){:target="_blank"}

-   :fontawesome-brands-github:{ .lg .middle } __GitHub__

    ---

    Designs and source code for this organization.

    [:octicons-arrow-right-24: Browse the org](https://github.com/napsocietygt){:target="_blank"}

-   :fontawesome-brands-instagram:{ .lg .middle } __Instagram__

    ---

    Our primary social media account, be sure to follow!

    [:octicons-arrow-right-24: Follow instagram](https://www.instagram.com/nanotechgt)

</div>

## Intro

Semiconductor fabrication is hard to get into as an undergraduate. The equipment sits behind cleanroom access, training queues, and cost. The coursework that covers it is senior-level and tied to a single department. Research positions, when you can get one, often place you on a single narrow step of someone else's process. Very few students get to carry a device from layout through fabrication to a measurement they can actually act on.

NaPS exists to change that. We aim to build the fabrication capability ourselves and run it as a student project, so members work directly with the equipment, developing processes, fabricating devices, troubleshooting hardware, and learning the pipeline end to end. Specific steps include, but are not limited to, 

- Layout and design
- Process simulation
- Lithography
- Thin-film deposition
- Etching, diffusion
- Vacuum systems
- Metrology
- Electrical characterization. 

Because we build and maintain the tools as well as use them, there is as much work here in vacuum systems, optics, and mechanical design as there is in device physics.

We also want the organization to be more than a fabrication project. NaPS is a networking and technical community for anyone interested in the broader semiconductor and nanotechnology world, connecting students across ECE, ME, ChBE, MSE, physics, and other disciplines, and creating opportunities to meet researchers and industry professionals working in the field.
!!! note "Where things stand"
    As of Fall 2026, the primary goal of the technical branch is to establish the fabrication infrastructure that future semiconductor, nanotechnology, and photonics projects will run on. Our first major project is developing a process for fabricating CMOS circuits. That single goal pulls in most of the capabilities we need anyway (lithography, thin-film deposition, etching, diffusion, vacuum systems, metrology, and process characterization) so building it lays the groundwork for everything that comes after.

### What members work on

Work at NaPS runs the full width of the pipeline, and you can go deep on whichever part interests you:

-   **Design and layout.** Simulate a device's fabrication, draw the layout, and work through design rules and how layers interact before anything is committed to silicon.
-   **Process development.** Our flow uses spin-on dopant and spin-on glass, which makes process *integration* a real problem to solve rather than a recipe to follow — how individual modules interact, and how the overall flow can be optimized.
-   **Equipment.** Build, modify, troubleshoot, and optimize the fabrication infrastructures like vacuum systems, lithography tools, deposition, diffusion, and the rest. A large part of the experience is figuring out what to do when a tool or a process does not behave the way it should.
-   **Characterization and process control.** Measure what came out, interpret fabrication and electrical characterization data, and use statistics and process control to evaluate yield, variation, repeatability, and drift — rather than judging a run by a single device.
-   **Iteration.** Feed that data back into the next revision of the design and the process. This is the part that is hardest to get anywhere else.

## Get involved

**No prior experience is required.** You do not need to be an ECE major, you do not need to be a senior, and you do not need to have touched fabrication equipment before. Members come from ECE, ME, ChBE, MSE, physics, and elsewhere, and there is useful work at every level of background.

1.  **Join the Discord and introduce yourself.** Say what you're studying and what you'd like to work on — that's enough for us to point you somewhere. This is also where day-to-day coordination happens, so it's the single most important step.
2.  **Come to a general body meeting.** Anyone can drop in, members and non-members alike. It's the fastest way to see what's currently running.
3.  **Pick a project and talk to whoever is leading it.** Projects span design and layout, lithography, deposition, etching, diffusion, vacuum systems, metrology, and characterization, so pick the part of the pipeline you want to learn.
4.  **Or propose your own.** If there's a device or a piece of equipment you want to build, write it up — proposals get reviewed by current members and can become real projects. Ask in Discord for the proposal template.

New to the subject? The [Resources](resources/index.md) page collects the references and tutorials we've found most useful for getting up to speed.

!!! note "Meeting times"

    General body meeting day, time, and location are still to be confirmed for the
    semester — check Discord for the current schedule.

## About this site

This documentation is built from plain Markdown with [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/){:target="_blank"}, and it's as much a work in progress as the fabrication line it describes. The goal is to eventually have enough written down here — equipment status, processes, tutorials — that someone could pick up where we left off without having to ask an officer first.

It gets there the same way the fab does: members filling in the parts they know. You don't need to be an officer, and you don't need to know HTML or CSS — if you can write Markdown, you can add a page. See [Contributing](contributing.md) for how to preview changes locally and publish them.

## Equipment

!!! warning "Work in progress"

    The equipment inventory hasn't been written up yet. If you know a tool's
    current status, what it's used for, or what training it requires, add it here
    or send the details to an officer in Discord.

<!-- ### Primary tools

<!-- Delete the Cost or Location column if you'd rather not publish either. -->

<!-- | Tool | Status | Cost | Location | Notes |
| ---- | ------ | ---- | -------- | ----- |
| [Tool name] | [Operational / In progress / Planned] | [$0,000] | [Room / lab] | [What it's for] |
| [Tool name] | [Operational / In progress / Planned] | [$0,000] | [Room / lab] | [What it's for] |
| [Tool name] | [Operational / In progress / Planned] | [$0,000] | [Room / lab] | [What it's for] |

### Metrology and verification

| Tool | Status | Notes |
| ---- | ------ | ----- |
| [Tool name] | [Operational / In progress / Planned] | [What it measures] |
| [Tool name] | [Operational / In progress / Planned] | [What it measures] |

### Materials and chemicals

| Category | Items | Notes |
| -------- | ----- | ----- |
| [Photoresists] | [Specific products] | [Handling or storage notes] |
| [Etchants] | [Specific products] | [Handling or storage notes] |
| [Dopant sources] | [Specific products] | [Handling or storage notes] | -->

## About

!!! warning "Work in progress"

    Our founding history, current officer roster, contact email, and the license
    covering our designs, code, and documentation still need to be filled in here.
    If you have those details, add them or pass them along in Discord.

<!-- [Origin of the org — when it was founded and by whom, if you know.]

**Current officers:** [Name — Role], [Name — Role], [Name — Role]

**Contact:** [email address]

**License:** [How others may reuse your designs, code, and documentation.
Hacker Fab uses CERN-OHL-W for hardware, MPL 2.0 for software, and
CC BY-SA 4.0 for docs — a reasonable starting point if you want your work
to stay open.] -->

- on [[2026-02-18 it was a good bowl]] I asked a [new question on discord](https://discordapp.com/channels/927628110009098281/927628110009098284/1473649272590307483):
> Do any of you regularly have links to other notes in your note properties, display said properties on your blog, and they show up on the blog as clickable links to the other notes? If so, how did you accomplish this?
- saberzero1 replied:
>There is a community implementation for this. We're also providing a plugin in the upcoming version 5.
- to which I replied:
> Does that translate to "wait for version 5"? or is that community implementation available somewhere already now?
- saberzero1 replied:
>https://quartz.eilleeenz.com/Quartz-Snippets#show-any-frontmatter-properties
> I am unsure how up-to-date this implementation is.

Paging down on that link lead to this link for [Working Properties with Obsidian Links](https://github.com/natashayasi/quartz/commit/d42e0bcab0b234498a5e746b38dd6f903486babc), which shows code for changing four files:
- create a file called [`quartz/components/Properties.tsx‎`](https://github.com/natashayasi/quartz/commit/d42e0bcab0b234498a5e746b38dd6f903486babc#diff-de2caae6386aaa7c025d008f6888c4bc66758e23b5f1e20c542a829fb8b4692e)
- edit the quartz.layout.ts to define the  Component.Properties(),
- edit the quartz/components/index.ts file to import Properties and add it to the export list
- add three lines to quartz/components/styles/properties.scss to give it a border

- [ ] test this later? or just wait for the plugin with version 5?
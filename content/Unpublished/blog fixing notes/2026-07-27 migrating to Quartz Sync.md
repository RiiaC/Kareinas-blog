see my [work obsidian for 2026-07-24](obsidian://adv-uri?vault=UmUArkeologi_Obsidian&filepath=Daily%20notes%2F2026-07%20(July)%2F2026-07-24%20Friday.md) and [2026-07-27](obsidian://open?vault=UmUArkeologi_Obsidian&file=Daily%20notes%2F2026-07%20(July)%2F2026-07-27%20Monday) for the notes for the transition to Quartz sync as done for https://riiac.github.io/SEAD_structure

- [x] Confirm current site is working  
- [x] Make a backup copy of C:\Obsidian files\Kareinas-blog Obsidian vault  
- [x] rename https://github.com/RiiaC/Kareinas-blog to `old_Kareinas_blog`
- [x] change its published url to https://riiac.github.io/old_Kareinas-blog/
- [x] confirm that the site is still published at the new address

- [x] Within Obsidian, delete the non-blog related folders and content, and move the actual content to the root level
- [x] add `publish: true` to all of the notes in all of the remaining folders
- [x] Create a new Quartz repository (`Kareinas-blog`) by following instructions at  https://saberzero1.github.io/quartz-syncer-docs/guides/github-setup
	- [x] clone from git clone https://github.com/RiiaC/Kareinas-blog.git
	- [x] this made the repository too big to push, so I deleted the video of Tania playing hammer dulcimer (which remains at C:\Obsidian files\clones for backups\backup-pre-quartz-syncer-Kareina-blog\content\Images\2026-05-21 Tania  plays Babba Lisas hyfs'n.mp4), and then it was possible
	- [ ] consider putting that film on YouTube
- [x] edit the config.yaml files as needed to adjust the blog title and links at the bottom 
- [x] personal access token `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`
- [x] in Obsidian, Install the Quartz Syncer plugin and link it to the new quartz `Kareinas-blog` repository
 - lots of issues encountered, have it close, but Quartz syncer's Publication center isn't succeeding. Eventually, left a "Me too" comment at https://github.com/saberzero1/quartz-syncer/issues/134
- [ ] Verify Syncer can successfully publish  
- [ ] update[ this checklist in the unpublished folder of my personal blog](obsidian://open?vault=Kareinas-blog&file=Unpublished%2Fblog%20fixing%20notes%2Fmigrating%20to%20Quartz%20Sync)
